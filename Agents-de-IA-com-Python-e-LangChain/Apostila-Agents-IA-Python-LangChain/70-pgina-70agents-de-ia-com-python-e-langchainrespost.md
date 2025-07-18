## Página 70

Agents de IA com Python e LangChain
resposta = agent_executor.invoke({'input': 'Meu nome é Adriano'})
print(resposta)
[1m> Entering new AgentExecutor chain...[0m
[32;1m[1;3mOlá, Adriano! Como posso te ajudar hoje?[0m
[1m> Finished chain.[0m
{'input': 'Meu nome é Adriano',
'chat_history': [HumanMessage(content='Meu nome é Adriano'),
AIMessage(content='Olá, Adriano! Como posso te ajudar hoje?')],
'output': 'Olá, Adriano! Como posso te ajudar hoje?'}
resposta = agent_executor.invoke({'input': 'Qual o meu nome?'})
print(resposta)
[1m> Entering new AgentExecutor chain...[0m
[32;1m[1;3mSeu nome é Adriano. Como posso te ajudar, Adriano?[0m
[1m> Finished chain.[0m
{'input': 'Qual o meu nome?',
'chat_history': [HumanMessage(content='Meu nome é Adriano'),
AIMessage(content='Olá, Adriano! Como posso te ajudar hoje?'),
HumanMessage(content='Qual o meu nome?'),
AIMessage(content='Seu nome é Adriano. Como posso te ajudar, Adriano?')],
'output': 'Seu nome é Adriano. Como posso te ajudar, Adriano?'}
E podemos perceber que o nosso AgentExecutor mantém nosso histórico de conversa e está pronto
para gerar uma aplicação real!
E é isso, pessoal! Agora vocês sabem como criar um AgentExecutor com memória utilizando o
LangChain. Isso é fundamental para desenvolver aplicações de chat mais realistas e funcionais, onde
o agente pode lembrar das interações anteriores e responder de forma mais contextual.
Asimov Academy
69


---
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