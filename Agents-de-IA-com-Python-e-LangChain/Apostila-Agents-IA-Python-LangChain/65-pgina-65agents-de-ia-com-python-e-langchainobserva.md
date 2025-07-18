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
## Página 66

Agents de IA com Python e LangChain
return resposta
observacao = tool_run[resposta.tool].run(resposta.tool_input)
passos_intermediarios.append((resposta, observacao))
Vamos testar o loop.
run_agent('Qual é a temperatura de Floripa?')
AgentFinish(return_values={'output': 'A temperatura atual em Florianópolis é de 21.5ºC.'},
log='A temperatura atual em Florianópolis é de 21.5ºC.')
�→
Modificamos um pouco o formato para padronizar ao funcionamento do LangChain para Agents.
from langchain.schema.agent import AgentFinish
from langchain.schema.runnable import RunnablePassthrough
pass_through = RunnablePassthrough.assign(
agent_scratchpad = lambda x: format_to_openai_function_messages(x['intermediate_steps'])
)
chain = pass_through | prompt | chat.bind(functions=tools_json) |
OpenAIFunctionsAgentOutputParser()
�→
def run_agent(input):
passos_intermediarios = []
while True:
resposta = chain.invoke({
'input': input,
'intermediate_steps': passos_intermediarios
})
if isinstance(resposta, AgentFinish):
return resposta
observacao = tool_run[resposta.tool].run(resposta.tool_input)
passos_intermediarios.append((resposta, observacao))
Essa modificação é implementada utilizando um RunnablePassthrough. Esse runnable funciona como
um dicionário, ao utilizarmos o método assign, ele adiciona uma chave nova ao dicionário. No caso a
chave sendo adicionada é de agent_scratchpad, que será derivada da chave intermediate_steps, mas
convertida para o formato da openai utilizando a função format_to_openai_function_messages.
pass_through.invoke({'input': 'Qual é a temperatura de Floripa?', 'intermediate_steps': []})
{'input': 'Qual é a temperatura de Floripa?',
'intermediate_steps': [],
'agent_scratchpad': []}
E testando novamente o podemos ver que o funcionamento é igual.
run_agent('Qual é a temperatura de Floripa?')
AgentFinish(return_values={'output': 'A temperatura atual em Floripa é de 21.5ºC.'}, log='A
temperatura atual em Floripa é de 21.5ºC.')
�→
Asimov Academy
65


---