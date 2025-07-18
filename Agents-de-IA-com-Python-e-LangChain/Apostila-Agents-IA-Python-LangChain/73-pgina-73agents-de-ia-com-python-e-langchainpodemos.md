## Página 73

Agents de IA com Python e LangChain
Podemos ver que ele solicitou a utilização da ferramenta python_repl_ast para conseguir gerar a
resposta ao usuário. É exatamente o que é esperado de um agente, que ele raciocine, esteja ciente das
ferramentas que possui e as utilize para gerar uma resposta mais acurada.
Refinando a System Message
Como falamos, o comportamento do modelo pode melhorar bastante com um pouco de engenharia
de prompt. Vamos criar uma System Message mais refinada para melhorar a performance do nosso
Agent:
from langchain.agents import create_tool_calling_agent, AgentExecutor
from langchain.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
system_msg = """Você é um agente projetado para escrever e executar código Python para
responder perguntas.
�→
Você tem acesso a um REPL Python, que pode usar para executar código Python.
Se encontrar um erro, depure o código e tente novamente.
Use apenas a saída do seu código para responder à pergunta.
Você pode conhecer a resposta sem executar nenhum código, mas deve ainda assim executar o
código para obter a resposta.
�→
Se não parecer possível escrever código para responder à pergunta, simplesmente retorne "Não
sei" como a resposta."""
�→
prompt = ChatPromptTemplate.from_messages([
('system', system_msg),
('placeholder', '{chat_history}'),
('human', '{input}'),
('placeholder', '{agent_scratchpad}')
])
chat = ChatOpenAI()
agent = create_tool_calling_agent(chat, tools, prompt)
agent_executor = AgentExecutor(agent=agent, tools=tools, verbose=True)
Vamos rodar novamente:
agent_executor.invoke({'input': 'Quantas letras tem a palavra LangChain?'})
{'input': 'Quantas letras tem a palavra LangChain?',
'output': 'A palavra "LangChain" tem 9 letras.'}
ReAct Agent (Reason + Act)
O que é?
O ReAct é uma técnica de engenharia de prompt que significa Reason (pensar) mais Act (agir). Foi
criada para permitir que os LLMs interajam com ferramentas externas para recuperar informações
Asimov Academy
72


---
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