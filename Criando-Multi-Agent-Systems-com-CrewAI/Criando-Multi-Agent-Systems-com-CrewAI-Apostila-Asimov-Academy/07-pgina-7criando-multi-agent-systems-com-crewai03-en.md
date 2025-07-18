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
## Página 8

Criando Multi Agent Systems com CrewAI
estas não ultrapassem seu escopo. Pessoalmente, prefiro criar uma única task por agent para garantir
maior modularidade na minha crew. Muito raramente eu crio mais de uma task por agent.
E, tanto na definição do agent quanto na da task, a clareza é fundamental para que o sistema funcione
bem!
Crew
A estrutura que reúne esses agents e permite que eles interajam é chamada de Crew (ou “tripulação”,
em inglês).
É exatamente isso: uma tripulação composta por diversos indivíduos que, trabalhando juntos, dire‑
cionam o barco na direção desejada.
Dentro da Crew, são definidos os modos de interação e comunicação entre os agents. Essa arquite‑
tura colaborativa, que discutimos já na aula inicial da nossa trilha de sistemas multiagentes, será
detalhada aqui!
Process
E a forma como os agents colaboram será definida pelos Processes, ou processos.
A definição do processo determina como a colaboração entre os agents ocorrerá. Há, basicamente,
dois tipos principais:
• No processo sequencial, temos uma sequência pré‑estabelecida de tasks a serem realizadas, o que
oferece menos autonomia ao sistema, porém maior previsibilidade nos resultados.
• No processo hierárquico, um modelo de linguagem é utilizado para definir a sequência de etapas a
ser seguida na execução da Crew. Essa abordagem confere mais autonomia ao sistema, mas reduz o
nível de controle e confiabilidade.
Como já discutimos: quanto mais controle, menor autonomia; quanto mais autonomia, menor cont‑
role.
Tools
E, não menos importante, temos as Tools do CrewAI.
Na analogia com profissionais de uma empresa, até os melhores colaboradores precisam de ferra‑
mentas para facilitar seu trabalho. Eu diria que os melhores profissionais são aqueles que sabem
aproveitar ao máximo as ferramentas à sua disposição.
Asimov Academy
7


---