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
## Página 76

Agents de IA com Python e LangChain
modelo menor localemnte. Ao utilizar modelos maiores, dos principais provedores de modelos de
linguagem como OpenAI, Google ou Anthropic, sugerimos que utilize o Tool Calling.
Hoje aprendemos sobre dois tipos importantes de Agents: Tool Calling e ReAct. Vimos como criar e
utilizar cada um deles, além de entender suas aplicações e limitações. Agora, você está mais preparado
para escolher e implementar o tipo de Agent que melhor se adapta às suas necessidades. Continue
praticando e explorando as possibilidades que esses Agents oferecem!
Asimov Academy
75


---