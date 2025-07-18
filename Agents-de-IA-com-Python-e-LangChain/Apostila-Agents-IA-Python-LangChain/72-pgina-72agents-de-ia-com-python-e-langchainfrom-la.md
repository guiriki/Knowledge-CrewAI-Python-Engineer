## Página 72

Agents de IA com Python e LangChain
from langchain.agents import create_tool_calling_agent, AgentExecutor
from langchain.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
system_msg = '''Você é um assistente amigável.
Certifique-se de usar a ferramenta PythonAstREPLTool para auxiliar a responder as perguntas'''
prompt = ChatPromptTemplate.from_messages([
('system', system_msg),
('placeholder', '{chat_history}'),
('human', '{input}'),
('placeholder', '{agent_scratchpad}')
])
chat = ChatOpenAI()
agent = create_tool_calling_agent(chat, tools, prompt)
agent_executor = AgentExecutor(agent=agent, tools=tools, verbose=True)
Vamos rodar o Agent e fazer uma pergunta:
agent_executor.invoke({'input': 'Qual é o décimo valor da sequência Fibonacci?'})
O Agent tentará utilizar a ferramenta Python para calcular o décimo valor da sequência Fibonacci.
Ele pode cometer alguns erros no processo, mas eventualmente deve conseguir chegar ao resultado
correto.
{'input': 'Qual é o décimo valor da sequência Fibonacci?',
'output': 'O décimo valor da sequência Fibonacci é 34.'}
Podemos tentar outra pergunta:
agent_executor.invoke({'input': 'Quantas letras tem a palavra LangChain?'})
{'input': 'Quantas letras tem a palavra LangChain?',
'output': 'A palavra "LangChain" tem 9 letras.'}
Quando utilizamos o parâmetro verbose=True, o LangChain nos mostra todos os passos que o modelo
está dando para chegar na resposta. No último caso, podemos ver que o modelo seguiu a seguinte
linha de raciocínio:
> Entering new AgentExecutor chain...
Invoking: `python_repl_ast` with `{'query': "len('LangChain')"}`
9
A palavra "LangChain" tem 9 letras.
> Finished chain.
{'input': 'Quantas letras tem a palavra LangChain?',
'output': 'A palavra "LangChain" tem 9 letras.'}
Asimov Academy
71


---
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