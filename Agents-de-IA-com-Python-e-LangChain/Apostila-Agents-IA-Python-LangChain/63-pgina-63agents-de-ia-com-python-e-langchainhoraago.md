## Página 63

Agents de IA com Python e LangChain
hora_agora = datetime.datetime.now(datetime.UTC).replace(tzinfo=None)
lista_horas = [datetime.datetime.fromisoformat(temp_str) for temp_str in
resultado['hourly']['time']]
�→
index_mais_prox = min(range(len(lista_horas)), key=lambda x: abs(lista_horas[x] -
hora_agora))
�→
temp_atual = resultado['hourly']['temperature_2m'][index_mais_prox]
return f'{temp_atual}ºC'
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
Revisando a Utilização das Tools
Vamos revisar a utilização das Tools que acabamos de criar. Primeiro, configuramos o prompt e o
modelo de linguagem.
from langchain.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
from langchain_core.utils.function_calling import convert_to_openai_function
prompt = ChatPromptTemplate.from_messages([
('system', 'Você é um assistente amigável chamado Isaac'),
('user', '{input}')
])
chat = ChatOpenAI()
tools = [busca_wikipedia, retorna_temperatura_atual]
tools_json = [convert_to_openai_function(tool) for tool in tools]
tool_run = {tool.name: tool for tool in tools}
chain = prompt | chat.bind(functions=tools_json)
Em seguida, adicionamos o OutputParser para interpretar as respostas do modelo.
from langchain.agents.output_parsers import OpenAIFunctionsAgentOutputParser
Asimov Academy
62


---
## Página 64

Agents de IA com Python e LangChain
chain = prompt | chat.bind(functions=tools_json) | OpenAIFunctionsAgentOutputParser()
Agora, vamos invocar a chain com uma pergunta específica.
resposta = chain.invoke({'input': 'Qual a temperatura em Floripa?'})
resposta
A resposta inclui informações sobre a Tool que foi chamada e os inputs utilizados.
resposta.tool
'retorna_temperatura_atual'
resposta.tool_input
{'latitude': -27.5953787, 'longitude': -48.5480499}
resposta.message_log
[AIMessage(content='', additional_kwargs={'function_call': {'arguments':
'{"latitude":-27.5953787,"longitude":-48.5480499}', 'name': 'retorna_temperatura_atual'}},
response_metadata={'token_usage': {'completion_tokens': 30, 'prompt_tokens': 153,
'total_tokens': 183}, 'model_name': 'gpt-3.5-turbo', 'system_fingerprint': None,
'finish_reason': 'function_call', 'logprobs': None},
id='run-9ee389cd-e54e-477d-b466-abee4c4081be-0')]
�→
�→
�→
�→
�→
Adicionando o Raciocínio do Agent às Mensagens (agent_scratchpad)
Temos que adicionar junto às nossas mensagens um campo que armazenará o raciocínio atual do
modelo chamado agent_scratchpad. Para isso, utilizamos um MessagesPlaceholder no
nosso prompt. Ele guardará espaço para o raciocínio e, caso o modelo não esteja gerando um raciocínio
no momento, o MessagesPlaceholder não é utilizado.
from langchain.prompts import MessagesPlaceholder
prompt = ChatPromptTemplate.from_messages([
('system', 'Você é um assistente amigável chamado Isaac'),
('user', '{input}'),
MessagesPlaceholder(variable_name='agent_scratchpad')
])
chain = prompt | chat.bind(functions=tools_json) | OpenAIFunctionsAgentOutputParser()
Vamos invocar a chain novamente, agora incluindo o agent_scratchpad.
resposta_inicial = chain.invoke({
'input': 'Qual a temperatura em Floripa?',
'agent_scratchpad': []})
resposta_inicial
A resposta inicial inclui a Tool que foi chamada e os inputs utilizados.
Asimov Academy
63


---