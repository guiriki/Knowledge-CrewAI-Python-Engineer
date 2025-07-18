## Página 1

Agents de IA com Python e LangChain
Asimov Academy


---
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