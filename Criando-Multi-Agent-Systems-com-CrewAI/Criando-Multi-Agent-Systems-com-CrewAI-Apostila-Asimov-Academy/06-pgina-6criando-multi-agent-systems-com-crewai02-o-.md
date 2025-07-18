## Página 6

Criando Multi Agent Systems com CrewAI
02. O conceito central de CrewAI
Bem‑vindos à primeira aula do nosso curso de CrewAI! Hoje, vamos explorar os conceitos essenciais
dessa biblioteca, entendendo como ela nos ajuda a construir aplicações inteligentes e colaborativas
utilizando sistemas multiagentes.
Antes de começarmos, quero relembrar um ponto fundamental sobre o uso eficiente dos modelos de
linguagem:
Nós precisamos induzir os modelos a pensar e agir de maneira similar a humana.
Quando damos a um modelo uma tarefa complexa, por exemplo, “desenvolva um código em Python
para um jogo X”, estamos exigindo demais de uma única vez. Um ser humano jamais realizaria esse
processo de forma contínua; ele pararia, refletiria sobre onde começar, avaliaria como estruturar o
código e quais pontos merecem atenção, para depois desenvolver e, por fim, revisar.
Você percebe que uma tarefa complexa exige diversos passos, não?
Da mesma forma, ao darmos a uma IA generativa a oportunidade de dividir uma atividade em vários
passos, obtemos resultados muito superiores do que quando exigimos a execução da tarefa de ime‑
diato.
Esse é o conceito central por trás do CrewAI: quebrar tarefas.
Precisamos decompor uma tarefa em pequenos passos e criar agentes específicos para resolver cada
um deles. Assim como em uma empresa, onde temos diferentes funcionários com habilidades distin‑
tas, um profissional sozinho pode não construir algo de valor, mas, em conjunto com outros profis‑
sionais, pode contribuir para a criação de soluções de extrema complexidade.
Mantenha sempre esta ideia em mente a partir de agora! E vamos para o nosso curso.
Asimov Academy
5


---
## Página 7

Criando Multi Agent Systems com CrewAI
03. Entendendo Crews, Agents, Tasks, Tools e Processes
Nesta aula, vamos apresentar os principais conceitos da biblioteca CrewAI:
• Agents
• Tasks
• Crew
• Process
• Tools
Entendê‑los com profundidade é fundamental para utilizarmos bom a biblioteca. Então vamos lá!
Agents
Um Agent é uma entidade autônoma com capacidades definidas, capaz de executar diversas funções.
Eles são os blocos básicos do CrewAI, responsáveis por tomar decisões e colaborar com outros agents.
Ou seja, qualquer estrutura desenvolvida com CrewAI terá, no mínimo, um agent, pois este é o seu
elemento fundamental – como o tijolo em uma construção.
Qual a característica de um bom agent?
Ele deve ser especializado em uma única área ou função. Se um agent realiza muitas ações diferentes,
você não estará aproveitando plenamente o potencial de um sistema multiagente. A ideia é sempre
modularizar!
Tasks
Depois temos as Tasks, ou tarefas! Ao definir um agent, estabelecemos seu comportamento e seu
objetivo principal, mas não determinamos, naquele momento, qual tarefa específica ele executará –
isso fica sob responsabilidade das Tasks.
Imagine que um agent defina “quem eu sou”, por exemplo: “sou Adriano, professor de programação
Python”. A task, por sua vez, define “o que eu faço” naquele momento, como “desenvolver um curso
de CrewAI”.
• Agent: “sou o professor Adriano”
• Task: “desenvolver o curso de CrewAI”
Ou seja: o agent está relacionado à identidade, enquanto a task está atrelada à atividade.
Um agent precisa, no mínimo, ter uma task para agir, mas pode possuir múltiplas tasks, desde que
Asimov Academy
6


---