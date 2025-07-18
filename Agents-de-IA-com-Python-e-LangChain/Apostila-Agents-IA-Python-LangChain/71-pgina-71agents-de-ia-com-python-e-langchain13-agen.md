## Página 71

Agents de IA com Python e LangChain
13. Agent Types - Entendendo os Agents Tool Calling e ReAct
Olá, pessoal! Agora vamos explorar um tópico super interessante e essencial para quem quer dominar
a criação de agentes inteligentes: os diferentes tipos de Agents. Vamos focar em dois tipos principais:
Tool Calling e ReAct. Nossos objetivos serão:
• Compreender o conceito de Agent Types.
• Aprender a criar e utilizar um Tool Calling Agent.
• Entender o funcionamento e a criação de um ReAct Agent.
• Explorar exemplos práticos de cada tipo de Agent.
Por que temos diferentes tipos de Agents?
Conforme a utilização de modelos de linguagem e ferramentas foi se consolidando, percebeu-se que
modelos mais simples podem performar muito bem quando utilizamos técnicas de engenharia de
prompt. Isso nos leva a criar diferentes tipos de Agents, cada um otimizado para utilizar ferramentas
de maneira eficiente. Vamos explorar os dois tipos mais utilizados: Tool Calling e ReAct.
Tool Calling Agent
O que é?
O Tool Calling Agent é um tipo de agente que detecta quando uma ou mais ferramentas devem ser
acionadas e responde com os dados que devem ser passados para essas ferramentas. Ele permite que
o modelo escolha inteligentemente gerar um objeto estruturado, como JSON, contendo argumentos
para acionar essas ferramentas. O tool calling agent é ótimo para modelos que já possuem um fine
tuning para utilização de ferramentas, como os modelos GPT, Gemini e Claude.
Exemplo Prático
Vamos criar um pequeno Agent que tem acesso à ferramenta do Python para fazer cálculos mais
rebuscados. Primeiro, importamos a ferramenta:
from langchain_experimental.tools import PythonAstREPLTool
tools = [PythonAstREPLTool()]
Agora, vamos criar o nosso Agent:
Asimov Academy
70


---
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