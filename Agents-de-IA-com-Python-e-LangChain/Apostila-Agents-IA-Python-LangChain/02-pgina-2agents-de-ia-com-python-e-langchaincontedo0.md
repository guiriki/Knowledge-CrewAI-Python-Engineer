## Página 2

Agents de IA com Python e LangChain
Conteúdo
01. Bem-vindos ao curso
5
Como o curso está estruturado? . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
5
1) LCEL - LangChain Expression Language . . . . . . . . . . . . . . . . . . . . . . . . .
5
2) Adição de Funções Externas e Aplicações . . . . . . . . . . . . . . . . . . . . . . . .
5
3) Criação de Tools . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
6
4) Criação de Agents . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
6
Pré-requisitos para o curso . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
6
02. Criando uma chain com LCEL
7
O que é LCEL? . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
7
Principais Características da LCEL . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
7
Criando sua Primeira Chain com LCEL . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
7
Adicionando mais elementos à chain . . . . . . . . . . . . . . . . . . . . . . . . . . .
8
Atenção: A ordem importa!
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
8
Entendendo a ordem correta . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
8
Chains Clássicas vs. LCEL . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
9
Métodos de um Runnable
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
10
O que são Runnables? . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
10
Métodos Principais dos Runnables
. . . . . . . . . . . . . . . . . . . . . . . . . . . .
10
Métodos Assíncronos . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
11
03. Adição de Funções Externas à API da OpenAI
12
Por que adicionar ferramentas externas é relevante? . . . . . . . . . . . . . . . . . . . . . .
12
Importações Iniciais
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
12
Criando a Função que Será Adicionada ao Modelo . . . . . . . . . . . . . . . . . . . . . . .
13
Criando a Descrição da Função
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
13
Chamando o Modelo com a Nova Ferramenta . . . . . . . . . . . . . . . . . . . . . . . . . .
14
Adicionando Resultado da Função às Mensagens . . . . . . . . . . . . . . . . . . . . . . . .
15
Explorando Diferentes Perguntas e o Parâmetro tool_choice . . . . . . . . . . . . . . .
16
Parâmetro “auto” . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
16
Parâmetro “none”
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
17
Parâmetro “dicionário com a key function” . . . . . . . . . . . . . . . . . . . . . . . .
18
04. Adição de Funções Externas Utilizando LangChain
19
Introduzindo Pydantic . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
19
Como Criamos uma Estrutura de Dados Sem Pydantic . . . . . . . . . . . . . . . . . .
19
Como Criamos uma Estrutura de Dados Usando Pydantic . . . . . . . . . . . . . . . .
20
Asimov Academy
1


---
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