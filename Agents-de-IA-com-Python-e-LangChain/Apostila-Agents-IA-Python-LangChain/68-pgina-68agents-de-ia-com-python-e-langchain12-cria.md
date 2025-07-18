## Página 68

Agents de IA com Python e LangChain
12. Criando um AgentExecutor com Memória
Olá, pessoal! Na última aula, criamos uma estrutura de Agent e AgentExecutor manualmente, a premira
contenda a chain executada e a segunda implementa o loop para executar todos os passos do raciocínio
do modelo. Nesta aula, vamos explorar como criar um AgentExecutor próprio do LangChain e
como adicionar memória a ele. Isso é crucial para desenvolver uma aplicação de chat funcional, onde
o agente pode lembrar das interações anteriores com o usuário. Nosso objetivos, portanto, serão:
• Entender a importância de adicionar memória a um AgentExecutor.
• Aprender a criar e configurar um AgentExecutor com memória.
Por que as memórias são importantes em uma aplicação de IA?
Para criarmos uma aplicação de chat funcional com nosso agente, é necessário que ele tenha a
capacidade de armazenar as informações trocadas com o usuário. Isso é essencial para que o agente
possa responder de forma contextual e coerente, lembrando das interações anteriores.
Ao utilizarmos a função run_agent criada no capítulo anterior, vemos que nosso modelo não posui
memória e, por isso, não é capaz nem de decorar o nosso nome. Se primeiro eu disser meu nome:
resposta = run_agent({'input': 'Olá, eu sou o Adriano'})
resposta
AgentFinish(return_values={'output': 'Olá, Adriano! Como posso te ajudar hoje?'}
E depois perguntar para ele o meu nome:
resposta = run_agent({'input': 'Qual o meu nome?'})
resposta
AgentFinish(return_values={'output': 'Seu nome é Isaac! Como posso te ajudar hoje?'}, log='Seu
nome é Isaac! Como posso te ajudar hoje?')
�→
Ele só não soube o meu nome como ainda se confundiu com o seu próprio nome. Nada bom, um
modeloassimparaconversaçãotempoucautilidade. Masvamosveragoracomosuperaressalimitação
utilizando os AgentExecutors do próprio LangChain.
Criando um AgentExecutor do LangChain
Criando as Tools que Usaremos
Primeiro, vamos criar as ferramentas (tools) que nosso agente vai utilizar.
As tools de
busca_wikipedia e retorna_temperatura_atual já foram criadas anteriormente, portanto não
vamos criá-las novamente.
Asimov Academy
67


---
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