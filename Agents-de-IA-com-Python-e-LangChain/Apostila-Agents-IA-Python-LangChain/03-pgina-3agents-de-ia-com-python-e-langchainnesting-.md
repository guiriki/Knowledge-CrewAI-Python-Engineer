## Página 3

Agents de IA com Python e LangChain
Nesting de Classes com Pydantic
. . . . . . . . . . . . . . . . . . . . . . . . . . . . .
20
Utilizando Pydantic para Criação de Tools da OpenAI
. . . . . . . . . . . . . . . . . . . . .
21
Utilizando Pydantic para Criar a Tool . . . . . . . . . . . . . . . . . . . . . . . . . . .
21
Convertendo para uma Função da OpenAI
. . . . . . . . . . . . . . . . . . . . . . . .
22
Adicionando Função Externa Utilizando LangChain
. . . . . . . . . . . . . . . . . . . . . .
22
Utilizando o Parâmetro functions . . . . . . . . . . . . . . . . . . . . . . . . . . .
22
Criando um Novo Componente de chat_model
. . . . . . . . . . . . . . . . . . . .
23
Forçando o Modelo a Chamar uma Função . . . . . . . . . . . . . . . . . . . . . . . .
23
Adicionando a uma Chain . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
23
Desafio - Criando uma Função para Obter Emails . . . . . . . . . . . . . . . . . . . . . . . .
24
05. Tagging - Categorização de Texto Utilizando Funções
25
Por que é importante categorizar textos? . . . . . . . . . . . . . . . . . . . . . . . . . . . .
25
Tagging para Análise de Sentimento e Detecção de Língua . . . . . . . . . . . . . . . . . . .
25
Parseando a Saída para Obtermos Apenas o que Interessa . . . . . . . . . . . . . . . . . . .
26
Um Exemplo Mais Interessante
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
27
Dica de conteúdo . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
29
06. Extraction - Extraindo e Estruturando Informações de Textos
31
Extraindo de Dados de Textos
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
31
Extraindo Informações da Web . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
33
Desafio
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
35
O que você precisa fazer?
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
35
Dicas para a Extração . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
36
07. Criação de Tools com LangChain
37
O que são tools?
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
37
Como as Tools se Relacionam com Modelos de Linguagem
. . . . . . . . . . . . . . . . . .
37
Criando Tools com o Decorador @tool . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
37
Descrevendo os Argumentos . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
38
Chamando a Tool . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
39
Criando Tools com StructuredTool . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
39
08. Processo Completo para Criação de Tool de Temperatura e do Wikipedia
41
Criando uma Tool de Busca de Temperatura
. . . . . . . . . . . . . . . . . . . . . . . . . .
41
Passo a Passo para Criar a Função de Temperatura . . . . . . . . . . . . . . . . . . . .
41
Encapsulando em uma Função
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
42
Testando a Tool . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
43
Asimov Academy
2


---
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