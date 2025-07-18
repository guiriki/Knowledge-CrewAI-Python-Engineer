## Página 74

Agents de IA com Python e LangChain
adicionais, levando a respostas mais confiáveis e factuais. Ele é ótimo para modelos mais simples
que não necessriamente passaram por um processo de fine tuning para utilização de ferramentas.
Sugerimos que para modelos open source, o agent ReAct seja usado:
Exemplo Prático
Vamos criar um ReAct Agent. Primeiro, importamos a função necessária:
from langchain.agents import create_react_agent
Podemos utilizar o LangChain Hub para obter prompts prontos para React:
from langchain import hub
prompt = hub.pull('hwchase17/react')
prompt
Vamos dar uma olhada no prompt:
print(prompt.template)
Answer the following questions as best you can. You have access to the following tools:
{tools}
Use the following format:
Question: the input question you must answer
Thought: you should always think about what to do
Action: the action to take, should be one of [{tool_names}]
Action Input: the input to the action
Observation: the result of the action
... (this Thought/Action/Action Input/Observation can repeat N times)
Thought: I now know the final answer
Final Answer: the final answer to the original input question
Begin!
Question: {input}
Thought:{agent_scratchpad}
Agora, vamos criar o Agent:
chat = ChatOpenAI()
agent = create_react_agent(chat, tools, prompt)
agent_executor = AgentExecutor(agent=agent, tools=tools, verbose=True)
Vamos rodar o Agent e fazer uma pergunta:
agent_executor.invoke({'input': 'Qual é o décimo valor da sequência Fibonacci?'})
Asimov Academy
73


---
## Página 75

Agents de IA com Python e LangChain
{'input': 'Qual é o décimo valor da sequência Fibonacci?',
'output': 'The tenth value of the Fibonacci sequence is 55.'}
Neste caso, o modelo até foi capaz de chegar em uma solução. Mas ao observamos a execução,
verificamos que por diversas vezes ele tentou utilizar a ferramenta de python mas não conseguiu.
Vamos melhorar o prompt para aumentar as chances de utilizarmos as ferramentas eficazmente.
Refinando o Prompt
Vamos criar um prompt mais refinado para o React Agent:
from langchain.prompts import PromptTemplate
prompt = PromptTemplate.from_template(
'''Answer the following questions as best you can. You have access to the following tools:
{tools}
Use the following format:
Question: the input question you must answer
Thought: you should always think about what to do
Action: the action to take, should be one of {tool_names}
Action Input: the input to the action
Observation: the result of the action
... (this Thought/Action/Action Input/Observation can repeat N times)
Thought: I now know the final answer
Final Answer: the final answer to the original input question
Begin!
Question: {input}
Thought:{agent_scratchpad}'''
)
chat = ChatOpenAI()
agent = create_react_agent(chat, tools, prompt)
agent_executor = AgentExecutor(agent=agent, tools=tools, verbose=True)
Vamos rodar novamente:
agent_executor.invoke({'input': 'Qual é o décimo valor da sequência Fibonacci?'})
{'input': 'Qual é o décimo valor da sequência Fibonacci?',
'output': 'The tenth value of the Fibonacci sequence is 55.'}
Quando utilizar Tool Calling e quando utilizar ReAct
Sugerimos que utilizem o ReAct agent para modelos mais simples que não passaram por processo de
fine tuning para utilização de funções externa. Em geral, esse é o caso quando você tentar rodar um
Asimov Academy
74


---