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
## Página 67

Agents de IA com Python e LangChain
O que Temos no Final?
No final temos duas estruturas: Agent + AgentExecutor segundo a nomenclatura do LangChain.
Um Agent
prompt = ChatPromptTemplate.from_messages([
('system', 'Você é um assistente amigável chamado Isaac'),
('user', '{input}'),
MessagesPlaceholder(variable_name='agent_scratchpad')
])
pass_through = RunnablePassthrough.assign(
agent_scratchpad = lambda x: format_to_openai_function_messages(x['intermediate_steps'])
)
chain = pass_through | prompt | chat.bind(functions=tools_json) |
OpenAIFunctionsAgentOutputParser()
�→
Um AgentExecutor
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
Nos próximos capítulos, veremos que o LangChain já tem Agents e AgentExecutors prontos, então
começaremos a utilizá-los para simplificar o processo.
Agora espero que tenha ficado claro para vocês o que é um Agent: ele é uma estrutura capaz de
raciocinar, armazenar passos intermediários (no nosso caso, noAgent Scratchpad) e agregar mais
informações ao modelo de linguagem, aumentando sua capacidade de fornecer respostas precisas.
Isso é um Agent.
Espero que tenham gostado e que esta tenha sido uma boa introdução aos Agents!
Asimov Academy
66


---