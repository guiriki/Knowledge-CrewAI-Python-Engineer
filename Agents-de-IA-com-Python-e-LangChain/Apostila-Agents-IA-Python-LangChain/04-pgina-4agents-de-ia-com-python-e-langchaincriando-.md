## Página 4

Agents de IA com Python e LangChain
Criando uma Tool de Busca no Wikipedia . . . . . . . . . . . . . . . . . . . . . . . . . . . .
43
Passo a Passo para Criar a Função de Busca no Wikipedia . . . . . . . . . . . . . . . .
43
Testando a Tool . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
44
Integrando as Tools em uma Chain
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
44
Configurando a Chain
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
44
Testando a Chain . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
44
09. Roteamento para Execução Automática de Tools
46
Recriando as Tools . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
46
Integrando as Tools ao Modelo . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
47
Criando Roteamento para Rodar Ferramenta . . . . . . . . . . . . . . . . . . . . . . . . . .
48
Adicionando OpenAIFunctionsAgentOutputParser . . . . . . . . . . . . . . . . . . . .
48
Rodando as Ferramentas . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
49
Desafio - Enviando um Email . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
50
10. Explorando Tools Padrão da Biblioteca LangChain
52
Explorando Tools Padrão . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
52
ArXiv . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
52
Python REPL
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
54
StackOverflow
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
54
File System . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
55
Exemplo de uma aplicação . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
56
11. Como um Agent é construído
59
Definindo um agente . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
59
Estrutura de um Agente
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
59
Entendendo cada componente
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
59
Modelo LLM . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
59
Planejamento . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
60
Memória . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
60
Ferramentas
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
60
Construindo um Agent . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
61
Criando as Tools que Usaremos . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
61
Revisando a Utilização das Tools
. . . . . . . . . . . . . . . . . . . . . . . . . . . . .
62
Adicionando o Raciocínio do Agent às Mensagens (agent_scratchpad) . . . . . . . . .
63
Criando um Loop de Raciocínio . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
64
O que Temos no Final? . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
66
Um Agent . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
66
Um AgentExecutor . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
66
Asimov Academy
3


---
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