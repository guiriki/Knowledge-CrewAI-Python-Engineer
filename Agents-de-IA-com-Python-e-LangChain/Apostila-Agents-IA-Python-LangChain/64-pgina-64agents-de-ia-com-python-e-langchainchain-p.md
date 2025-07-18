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
## Página 65

Agents de IA com Python e LangChain
observacao = tool_run[resposta_inicial.tool].run(resposta_inicial.tool_input)
observacao
'21.9ºC'
Podemos utilizar a função format_to_openai_function_messages para modificar o formato
da resposta de forma que ela possa ser enviada, junto da observação, de volta ao modelo. No caso,
o que está ocorrendo é que o modelo está pedindo que uma Tool seja rodada, estamos rodando a
Tool e gerando uma observação, e agora enviamos novamente para o modelo a pergunta original, a
mensagem do próprio modelo dizendo que precisava que a Tool fosse rodada e a observação gerada
pela ferramenta.
from langchain.agents.format_scratchpad import format_to_openai_function_messages
format_to_openai_function_messages([(resposta_inicial, observacao)])
[AIMessage(content='', additional_kwargs={'function_call': {'arguments':
'{"latitude":-27.5954,"longitude":-48.548}', 'name': 'retorna_temperatura_atual'}},
response_metadata={'token_usage': {'completion_tokens': 27, 'prompt_tokens': 153,
'total_tokens': 180}, 'model_name': 'gpt-3.5-turbo', 'system_fingerprint': None,
'finish_reason': 'function_call', 'logprobs': None},
id='run-722c78ea-a704-41e2-9205-564c3e8270ab-0'),
�→
�→
�→
�→
�→
FunctionMessage(content='21.9ºC', name='retorna_temperatura_atual')]
Vamos invocar a chain novamente, agora incluindo a observação.
resposta_final = chain.invoke({
'input': 'Qual a temperatura em Floripa?',
'agent_scratchpad': format_to_openai_function_messages([(resposta_inicial, observacao)])})
resposta_final
AgentFinish(return_values={'output': 'A temperatura em Florianópolis é de 21.9ºC no
momento.'}, log='A temperatura em Florianópolis é de 21.9ºC no momento.')
�→
Criando um Loop de Raciocínio
Por fim, podemos criar um loop que adiciona automaticamente as chamadas de função e observações
e fica chamando o modelo novamente até que a mensagem de AgentFinish seja recebida.
from langchain.schema.agent import AgentFinish
def run_agent(input):
passos_intermediarios = []
while True:
resposta = chain.invoke({
'input': input,
'agent_scratchpad': format_to_openai_function_messages(passos_intermediarios)
})
if isinstance(resposta, AgentFinish):
Asimov Academy
64


---