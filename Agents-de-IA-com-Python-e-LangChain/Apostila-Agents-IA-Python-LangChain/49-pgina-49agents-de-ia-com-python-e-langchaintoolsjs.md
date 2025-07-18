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
## Página 50

Agents de IA com Python e LangChain
resultado.tool
'busca_wikipedia'
resultado.tool_input
{'query': 'Isaac Asimov'}
E um AgentFinish, caso a mensagem esteja finalizada.
resultado = chain.invoke({'input': 'Olá'})
resultado
AgentFinish(return_values={'output': 'Olá! Como posso te ajudar hoje?'}, log='Olá! Como posso
te ajudar hoje?')
�→
resultado.return_values['output']
'Olá! Como posso te ajudar hoje?'
Rodando as Ferramentas
Podemos criar uma função simples de roteamento para lidar com os dois estados possíveis:
from langchain_core.agents import AgentFinish
def roteamento(resultado):
if isinstance(resultado, AgentFinish):
return resultado.return_values['output']
else:
return tool_run[resultado.tool].run(resultado.tool_input)
Podemos adicionar essa função a nossa chain:
chain = prompt | chat.bind(functions=tools_json) | OpenAIFunctionsAgentOutputParser() |
roteamento
�→
E rodamos primeiro com uma input que não necessitará utilização de tools:
chain.invoke({'input': 'Olá'})
E a resposta será diretamente a string de resposta:
'Olá! Como posso ajudar você hoje?'
Agora quando fazemos uma pergunta que necessita de uma tool:
chain.invoke({'input': 'Quem foi Isaac Asimov?'})
E o resultado é a observação gerada pela tool:
Asimov Academy
49


---