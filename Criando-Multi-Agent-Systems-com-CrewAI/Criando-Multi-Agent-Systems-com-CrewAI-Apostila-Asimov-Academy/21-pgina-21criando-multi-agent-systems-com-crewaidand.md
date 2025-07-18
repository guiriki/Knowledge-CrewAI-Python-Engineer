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
## Página 22

Criando Multi Agent Systems com CrewAI
Conclusão
Queroquevocêssaiamdestaaulacomaclarezadequeaprincipalvalênciadasestruturasmulti‑agent
é a modularização, que permite uma maior especificidade em nossos sistemas.
Além disso, lembrem‑se de dar tempo ao modelo para pensar, adicionando etapas de reflexão que
farão com que ele planeje, revise e critique as ações, aumentando assim a qualidade da resposta.
Mantendo esses princípios em mente, tenho certeza de que vocês construirão ótimas aplicações!
Asimov Academy
21


---