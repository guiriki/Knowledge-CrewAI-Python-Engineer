## Página 20

Criando Multi Agent Systems com CrewAI
05. Princípios da Engenharia de Prompt na criação de Crews
Ótimo! Agora você já tem um entendimento básico de como criar uma Crew. Já conhece a utiliza‑
ção das três principais classes: Agent, Task e Crew, e pode começar a se desafiar, criando aplicações
diferentes.
Mas antes de você começar, quero reforçar alguns pontos que considero essenciais, afinal, sua crew
será tão boa quanto sua capacidade de entender o seu problema e dividi‑lo em partes.
É isso mesmo! A ideia por trás de uma crew é criar uma aplicação que aumente a capacidade de um
modelo de linguagem e, para isso, precisamos usar os dois princípios da engenharia de prompts:
1. Especificidade
2. Dar tempo ao modelo para pensar
Vocês já devem estar familiarizados com esses princípios, mas quero reforçá‑los para garantir que
vocês criem aplicações úteis!
Gerando especificidade através da modularização
Para gerar especificidade, você precisa ser capaz de modularizar o seu projeto, pensando no seu prob‑
lema como uma sequência de etapas que geram um produto final.
Jáutilizamosaanalogiadeumambienteempresarial, earetomoaquiporqueseaplicaperfeitamente.
Dentro de uma empresa, temos diversos cargos específicos executando papéis e funções diferentes.
Cada cargo necessita de habilidades e ferramentas distintas. Alguns cargos respondem a outros, uns
criam, outros revisam, alguns coletam informações e outros levam essa informação ao cliente final.
Às vezes, múltiplas funções são executadas por um mesmo funcionário; em outras ocasiões, temos
um funcionário responsável por apenas uma única função.
As possibilidades são infinitas, mas algumas regras precisam ser respeitadas para criar uma boa es‑
trutura organizacional, como:
• Tarefas precisam ser específicas.
• Toda tarefa precisa de um responsável.
• Todo o processo precisa de revisão e validação.
• Os canais de comunicação entre os elementos da equipe devem ser claros.
Isso se aplica tanto a um ambiente empresarial quanto a uma Crew!
Asimov Academy
19


---
## Página 21

Criando Multi Agent Systems com CrewAI
Dando Tempo para Pensar Através da Reflexão
Na minha opinião, a técnica que mais tem aumentado a capacidade dos modelos de linguagem é a
reflexão, e isso é incrível, pois é muito simples.
Já falamos também que devemos pensar no modelo como um ser humano. Quando damos uma
tarefa muito complexa para alguém e não damos tempo para que essa pessoa raciocine, a resposta
naturalmente será de baixa qualidade. Da mesma forma, acontece com os modelos de linguagem.
Para termos bons resultados, é importante incentivá‑los a refletir sobre os passos críticos para chegar‑
mos a uma boa resposta.
Mas como fazemos isso no contexto do CrewAI?
Simples, criando agents responsáveis por planejar, pensar e revisar!
Essas são tarefas de reflexão, onde qualificamos nosso trabalho, em contraste com as tarefas de exe‑
cução, que envolvem o desenvolvimento prático da tarefa. Adicionar passos de reflexão no meio da
sua crew é fundamental para obter bons resultados. No exemplo da aula anterior, temos um desen‑
volvedor de blog posts. Se vocês prestarem atenção nas características das tasks, notarão que temos
três tarefas de reflexão e apenas uma de execução:
• Gerar ideias > reflexão
• Planejar conteúdo > reflexão
• Escrever post > execução
• Revisar post > reflexão
Isso foi pensado. Eu poderia ter criado uma crew com apenas um passo, o escrever post, mas o re‑
sultado teria sido péssimo, semelhante a pedir para o ChatGPT escrever um post sobre um assunto
(o famoso zero‑shot prompt). Quando adiciono todas essas etapas de reflexão, a qualidade final mel‑
hora muito, e com modelos simples superamos facilmente modelos muito mais complexos.
Como Saber se a Minha Task é de Reflexão ou Execução?
Isso é simples: tasks de reflexão geralmente começam com palavras como planeje, revise, critique,
selecione. Ou seja, elas não criam o resultado em si, masoferecemferramentasparafacilitaracriação
ou realizam o polimento necessário para que o resultado atenda às necessidades do usuário.
Já as tarefas de execução realmente desenvolvem o resultado e, em geral, começam com palavras
como gere, desenvolva, etc. Podemos ter crews compostas apenas por tarefas de execução (embora
o resultado não seja muito bom), mas não podemos ter uma crew composta apenas por tarefas de
reflexão.
Asimov Academy
20


---