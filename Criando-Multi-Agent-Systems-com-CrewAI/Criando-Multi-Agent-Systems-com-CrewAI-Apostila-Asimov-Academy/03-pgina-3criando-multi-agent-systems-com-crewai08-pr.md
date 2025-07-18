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
## Página 4

Criando Multi Agent Systems com CrewAI
13. Criando tools presonalizadas para CrewAI
67
Criando e utilizando Tools em CrewAI . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
67
Função que será usada como exemplo
. . . . . . . . . . . . . . . . . . . . . . . . . .
67
Criando Tools com BaseTool . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
68
Descrevendo os argumentos . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
69
Juntando tudo . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
70
Utilizando Tools do LangChain . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
70
Integrando Ferramentas do LangChain ao CrewAI
. . . . . . . . . . . . . . . . . . . .
71
14. Finalizando o curso
72
Introdução – Recapitulando o curso . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
72
Recapitulação dos conceitos fundamentais . . . . . . . . . . . . . . . . . . . . . . . . . . .
72
Aplicações práticas e exemplos
. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
73
Dicas e direcionamentos para o futuro
. . . . . . . . . . . . . . . . . . . . . . . . . . . . .
73
E pra finalizar . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .
73
Asimov Academy
3


---