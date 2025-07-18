## Página 5

Agents de IA com Python e LangChain
12. Criando um AgentExecutor com Memória
67
Por que as memórias são importantes em uma aplicação de IA? . . . . . . . . . . . . . . . .
67
Criando um AgentExecutor do LangChain . . . . . . . . . . . . . . . . . . . . . . . . . . . .
67
Criando as Tools que Usaremos . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
67
Adicionando Memória
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
68
Configurando o AgentExecutor com Memória . . . . . . . . . . . . . . . . . . . . . . .
68
Testando o AgentExecutor com Memória . . . . . . . . . . . . . . . . . . . . . . . . .
68
13. Agent Types - Entendendo os Agents Tool Calling e ReAct
70
Por que temos diferentes tipos de Agents?
. . . . . . . . . . . . . . . . . . . . . . . . . . .
70
Tool Calling Agent
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
70
O que é? . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
70
Exemplo Prático
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
70
Refinando a System Message
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
72
ReAct Agent (Reason + Act) . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
72
O que é? . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
72
Exemplo Prático
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
73
Refinando o Prompt
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
74
Quando utilizar Tool Calling e quando utilizar ReAct . . . . . . . . . . . . . . . . . . . . . .
74
14. Agents Toolkits - Criando Agents para Analisar Dataframes e SQL
76
O que são os Tollkits? . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
76
Pandas DataFrame . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
76
SQL Database . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
78
15. Finalizando o curso
81
Asimov Academy
4


---
## Página 6

Agents de IA com Python e LangChain
01. Bem-vindos ao curso
Bem-vindos a mais um curso da Asimov!
Este é o curso de Agentes de IA com Python e LangChain, e estamos muito felizes em trazer este
conteúdo novo para vocês. Vocês já devem ter percebido que acreditamos muito nas IAs como uma
forma revolucionária de lidar com o trabalho e com o acesso à informação. Estamos iniciando uma
nova era e quebrando diversos paradigmas. Nessa linha, os agentes entram como componentes
principais dessa revolução.
Essas estruturas são capazes de raciocínios similares aos humanos, acesso a informações praticamente
ilimitadas, capacidade de agir no mundo e buscar informações em tempo real. Tudo isso de uma forma
autônoma, ou seja, após desenvolvido o meu agente, ele será capaz de se adequar às novas tarefas e
necessidades que forem surgindo!
Tudoissoparecebomdemais, maseudigoqueestamosapenasnoinício. Recémcomeçamosaexplorar
as capacidades dessas estruturas e, para ser sincero, ainda não sei do que as aplicações com agentes
serão capazes no futuro. Mas uma coisa eu tenho certeza: em um futuro próximo, teremos contato
diário com os mais diferentes tipos de agentes! E nada melhor do que começar agora a entender o que
são agentes, como construí-los e já adicioná-los às minhas aplicações hoje.
Façamos um futuro que começa agora!
Como o curso está estruturado?
Teremos 4 partes principais no nosso curso:
1) LCEL - LangChain Expression Language
As primeiras aulas são para apresentar o LangChain Expression Language, ou LCEL. Esta é uma forma
declarativa e intuitiva de compor chains, de maneira fácil e escalável e será a base para criarmos as
chains dos nossos agents!
2) Adição de Funções Externas e Aplicações
Vamos ver neste módulo como criar funções externas que estarão disponíveis para o modelo de
linguagem utilizar quando necessário. Essas estruturas aumentarão as capacidades dos modelos,
pois poderão gerar informações atualizadas ou atuar no mundo de forma customizada. Neste módulo
entenderemos como criar jsons específicos, com boas descrições das funções e dos argumentos, que
aumentam as chances do modelo reconhecer e utilizá-las nos momentos corretos.
Asimov Academy
5


---