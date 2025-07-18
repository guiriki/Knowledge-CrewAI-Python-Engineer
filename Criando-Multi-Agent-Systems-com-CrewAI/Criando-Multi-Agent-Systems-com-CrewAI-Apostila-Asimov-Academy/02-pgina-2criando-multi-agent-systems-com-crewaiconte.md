## Página 2

Criando Multi Agent Systems com CrewAI
Conteúdo
01. Apresentação do curso
4
02. O conceito central de CrewAI
5
03. Entendendo Crews, Agents, Tasks, Tools e Processes
6
Agents . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
6
Tasks
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
6
Crew . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
7
Process . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
7
Tools . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
7
Conclusão . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
8
04. Criação de Agents, Tasks e Crews no CrewAI
9
Overview da aplicação . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
10
Configuração do Ambiente . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
12
Criação dos Agents . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
12
Definição das Tasks . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
13
Criação da Crew . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
14
Ordem importa . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
15
Execução da Crew
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
15
Passando Inputs para a Crew
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
15
Conclusão e Próximos Passos . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
16
Dúvidas sobre criação de Agents, Tasks e Crews
. . . . . . . . . . . . . . . . . . . . .
17
Desafio ‑ Criação de uma Crew para roteirização de vídeo no YouTube
. . . . . . . . . . . .
18
05. Princípios da Engenharia de Prompt na criação de Crews
19
Gerando especificidade através da modularização . . . . . . . . . . . . . . . . . . . . . . .
19
Dando Tempo para Pensar Através da Reflexão . . . . . . . . . . . . . . . . . . . . . . . . .
20
Como Saber se a Minha Task é de Reflexão ou Execução?
. . . . . . . . . . . . . . . .
20
Conclusão . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
21
06. Estruturado Agents e Tasks com ajuda do ChatGPT
22
Prompt 1: Descrevendo o processo . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
22
Prompt 2: Utilizando o Chat para criar Agents e Tasks
. . . . . . . . . . . . . . . . . . . . .
23
07. Projeto finalizado ‑ Criando uma crew para criar crews
27
agents.yaml . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
27
tasks.yaml . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
28
Asimov Academy
1


---
## Página 3

Criando Multi Agent Systems com CrewAI
08. Projeto ‑ Criando uma crew para criar crews
32
Desenvolvendo a primeira versão do sistema . . . . . . . . . . . . . . . . . . . . . . . . . .
32
Criando o arquivo agents.yaml
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
36
Criando o arquivo tasks.yaml
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
37
Refinando as expected_output’s . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
38
09. Projeto ‑ Refinando a crew para criar crews
42
Iniciando um projeto . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
42
Analisando a estrutura do projeto . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
43
Arquivo .env . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
44
Arquivo agents.yaml . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
45
Arquivo tasks.yaml . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
45
Arquivo crew.py . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
46
Arquivo main.py
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
48
Conclusão . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
48
10. Observabilidade com AgentOps
49
O que é Observabilidade?
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
49
Introduzindo o AgentOps . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
49
Principais Funcionalidades do AgentOps . . . . . . . . . . . . . . . . . . . . . . . . .
49
Como Utilizar o AgentOps
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
50
O painel do AgentOps
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
52
Análise de Sessões . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
52
Conclusão . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
53
11. Tools de CrewAI
54
Como um modelo age? . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
54
O que são as tools? . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
54
Os dois principais tipos de tools . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
54
Tools de captura de informação . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
54
Tools de atuação . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
55
Como usar tools? . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
55
Tools disponibilizadas pela CrewAI
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
58
12. Adicionando tools ao meu projeto
62
tasks.yaml . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
63
crew.py . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
64
Asimov Academy
2


---