## Página 48

Agents de IA com Python e LangChain
'longitude': longitude,
'hourly': 'temperature_2m',
'forecast_days': 1,
}
resposta = requests.get(URL, params=params)
if resposta.status_code == 200:
resultado = resposta.json()
hora_agora = datetime.datetime.now(datetime.UTC).replace(tzinfo=None)
lista_horas = [datetime.datetime.fromisoformat(temp_str) for temp_str in
resultado['hourly']['time']]
�→
index_mais_prox = min(range(len(lista_horas)), key=lambda x: abs(lista_horas[x] -
hora_agora))
�→
temp_atual = resultado['hourly']['temperature_2m'][index_mais_prox]
return temp_atual
else:
raise Exception(f'Request para API {URL} falhou: {resposta.status_code}')
@tool
def busca_wikipedia(query: str):
"""Faz busca no wikipedia e retorna resumos de páginas para a query"""
titulos_paginas = wikipedia.search(query)
resumos = []
for titulo in titulos_paginas[:3]:
try:
wiki_page = wikipedia.page(title=titulo, auto_suggest=True)
resumos.append(f'Título da página: {titulo}\nResumo: {wiki_page.summary}')
except:
pass
if not resumos:
return 'Busca não teve retorno'
else:
return '\n\n'.join(resumos)
Integrando as Tools ao Modelo
Agora que recriamos nossas tools, vamos integrá-las ao nosso modelo de IA. Isso envolve criar uma
chain que combina o prompt, o modelo de chat e as tools.
from langchain.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
from langchain_core.utils.function_calling import convert_to_openai_function
prompt = ChatPromptTemplate.from_messages([
('system', 'Você é um assistente amigável chamado Isaac'),
('user', '{input}')
])
chat = ChatOpenAI()
tools = [busca_wikipedia, retorna_temperatura_atual]
Asimov Academy
47


---
## Página 49

Agents de IA com Python e LangChain
tools_json = [convert_to_openai_function(tool) for tool in tools]
tool_run = {tool.name: tool for tool in tools}
chain = prompt | chat.bind(functions=tools_json)
Criamos três componentes aqui importantes que não devem passar despercebidos.
• tools (list) - Este é o formato padrão de inicialização de ferramentas a um agente do LangChain.
Elas devem sempre ser passadas para o agente na forma de uma lista.
• tools_json (list) - É uma lista com as tools convertidas para o padrão de jsons que a OpenAI
reconhece (como vimos anterioremente nas aulas de reconhecimento de funções).
• tool_run (dict) - Ele permite rodar uma tool baseado no nome desta. Será utilizado posterior-
mente no roteamento.
Criando Roteamento para Rodar Ferramenta
Chamamos de roteamento o processo de análise da saída de um modelo que possui acesso a ferramen-
tas. Neste processo, precisamos entender qual é o tipo de saída que o modelo está nos fornecendo.
Caso seja uma saída já com a resposta final do modelo, podemos retorná-la ao usuário; caso o modelo
esteja solicitando a chamada de uma ferramenta, temos que chamar essa ferramenta e mostrar o
resultado ao usuário.
Adicionando OpenAIFunctionsAgentOutputParser
Para auxiliar neste processo, podemos utilizar o OpenAIFunctionsAgentOutputParser. Ele
processa a saída de um modelo da OpenAI que possui ferramentas e determina o estado da mensagem
devolvida.
from langchain.agents.output_parsers import OpenAIFunctionsAgentOutputParser
chain = prompt | chat.bind(functions=tools_json) | OpenAIFunctionsAgentOutputParser()
O retorno será um AgentAction caso necessite que uma ferramenta seja executada.
resultado = chain.invoke({'input': 'Quem foi Isaac Asimov?'})
resultado
AgentActionMessageLog(tool='busca_wikipedia', tool_input={'query': 'Isaac Asimov'},
log="\nInvoking: `busca_wikipedia` with `{'query': 'Isaac Asimov'}`\n\n\n",
message_log=[AIMessage(content='', additional_kwargs={'function_call': {'arguments':
'{"query":"Isaac Asimov"}', 'name': 'busca_wikipedia'}}, response_metadata={'token_usage':
{'completion_tokens': 20, 'prompt_tokens': 154, 'total_tokens': 174}, 'model_name':
'gpt-3.5-turbo', 'system_fingerprint': None, 'finish_reason': 'function_call', 'logprobs':
None}, id='run-1a81360a-a616-4e49-a4f9-727a23afeef7-0')])
�→
�→
�→
�→
�→
�→
Asimov Academy
48


---