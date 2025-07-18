## Página 69

Agents de IA com Python e LangChain
tools = [busca_wikipedia, retorna_temperatura_atual]
Adicionando Memória
Agora, vamos adicionar memória ao nosso AgentExecutor para que ele possa lembrar das inter-
ações anteriores. Utilizaremos o ConversationBufferMemory. As memórias são conteúdo do nosso
curso inicila de LangChain, caso você queira saber mais sugerimos que deem uma olhada lá.
from langchain.memory import ConversationBufferMemory
memory = ConversationBufferMemory(
return_messages=True,
memory_key='chat_history'
)
prompt = ChatPromptTemplate.from_messages([
('system', 'Você é um assistente amigável chamado Isaac'),
MessagesPlaceholder(variable_name='chat_history'),
('user', '{input}'),
MessagesPlaceholder(variable_name='agent_scratchpad')
])
pass_through = RunnablePassthrough.assign(
agent_scratchpad = lambda x: format_to_openai_function_messages(x['intermediate_steps'])
)
agent_chain = pass_through | prompt | chat.bind(functions=tools_json) |
OpenAIFunctionsAgentOutputParser()
�→
Adicionamos no prompt um campo com MessagesPlaceholder com a variável “chat_history”. Neste
local será adicionado a lista de histórico de mensagens da memória.
Configurando o AgentExecutor com Memória
AgorapodemosimportaroAgentExecutosdoLangchaineadicionarachaindonossoagenteamemória
que criamos previamente:
from langchain.agents import AgentExecutor
agent_executor = AgentExecutor(
agent=agent_chain,
tools=tools,
memory=memory,
verbose=True
)
Testando o AgentExecutor com Memória
Vamos testar nosso AgentExecutor com memória para ver como ele se comporta.
Asimov Academy
68


---
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