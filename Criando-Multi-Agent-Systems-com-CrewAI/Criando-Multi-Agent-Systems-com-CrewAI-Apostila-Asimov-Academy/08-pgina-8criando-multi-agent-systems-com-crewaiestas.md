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
## Página 9

Criando Multi Agent Systems com CrewAI
O CrewAI dispõe de diversas tools que ampliam as capacidades dos agents. Elas permitem, por exem‑
plo, acessar bancos de dados, interagir com APIs, processar dados ou realizar operações complexas
que seriam inviáveis sem o seu uso.
Conclusão
Ao longo desta aula, nós exploramos os componentes essenciais da biblioteca CrewAI: Agents, Tasks,
Crew, Process e Tools. Esses elementos formam a espinha dorsal do desenvolvimento de sistemas
multiagentes, e compreender como cada um deles funciona é crucial para tirar o máximo de proveito
dessa poderosa ferramenta. E na próxima aula, vamos criar nossa primeira crew! Até lá!
Asimov Academy
8


---