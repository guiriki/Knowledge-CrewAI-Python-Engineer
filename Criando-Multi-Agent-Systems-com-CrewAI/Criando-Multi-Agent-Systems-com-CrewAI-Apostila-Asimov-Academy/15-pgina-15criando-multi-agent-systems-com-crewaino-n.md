## Página 15

Criando Multi Agent Systems com CrewAI
No nosso código, definimos várias tasks, cada uma vinculada ao agent especializado para aquela fase
do processo de criação do blog. Abaixo está o código que define essas tasks:
cria_ideias = Task(
description='Crie uma lista com 10 ideias diferentes para posts de blog sobre o tema: {tema}.
As ideias devem ser criativas, relevantes e diversificadas em formato, com foco em engajar
o público-alvo.',
↪
↪
agent=desenvolvedor_de_ideais,
expected_output='Uma lista com 10 ideias de posts, cada uma com um título criativo e um breve
resumo do que o conteúdo abordará.'
↪
)
seleciona_ideias = Task(
description='Selecione a melhor ideia da lista gerada, justificando sua escolha com base na
relevância e no alinhamento com os objetivos do blog.',
↪
agent=desenvolvedor_de_ideais,
expected_output='A escolha de uma ideia com uma justificativa clara e concisa sobre sua
relevância e alinhamento com os objetivos do conteúdo.'
↪
)
planeja_conteudo = Task(
description='Crie um briefing detalhado para o post de blog, incluindo informações como
objetivo, público-alvo, tom de voz, palavras-chave e formato.',
↪
agent=planejador_de_conteudo,
expected_output='Um briefing estruturado, abordando todos os pontos importantes para guiar a
criação do conteúdo.'
↪
)
escreve_post = Task(
description='Escreva o conteúdo completo do post de blog, seguindo as diretrizes do briefing
e a ideia selecionada. Certifique-se de que o post seja envolvente, bem estruturado e
adequado ao público-alvo.',
↪
↪
agent=escritor_do_post,
expected_output='Um post de blog com introdução, desenvolvimento e conclusão, que seja claro,
interessante e alinhado com o briefing.'
↪
)
revisa_post = Task(
description='Revise o post de blog, corrigindo erros gramaticais e de pontuação, além de
melhorar a fluidez do texto. Assegure que o post esteja alinhado com o tom e objetivo
definidos no briefing.',
↪
↪
agent=revisor_do_post,
expected_output='O post revisado, sem erros gramaticais e com boa fluidez, pronto para ser
publicado.'
↪
)
Criação da Crew
Por fim, unimos todos os elementos ao definir a Crew. A Crew é a estrutura que organiza a interação
entre os agents e as tasks. Durante a definição da crew, informamos uma lista dos agents envolvidos,
outra lista das tasks a serem executadas e especificamos o tipo de processo que a crew seguirá. Neste
Asimov Academy
14


---
## Página 16

Criando Multi Agent Systems com CrewAI
exemplo, optamos pelo processo sequencial, o que significa que as tarefas serão executadas em uma
ordem pré‑definida.
Abaixo, o código que configura a Crew:
blog_post_creation_crew = Crew(
agents=[desenvolvedor_de_ideais, planejador_de_conteudo, escritor_do_post, revisor_do_post],
tasks=[cria_ideias, seleciona_ideias, planeja_conteudo, escreve_post, revisa_post],
process=Process.sequential
)
Ordem importa
Muito importante salientar que a ordem em que organizamos nossas tasks é crucial ao desenvolver‑
mos a crew. Quando utilizamos o processo sequencial, a execução das tarefas segue a ordem pre‑
definida na lista de tasks, com a saída de uma tarefa servindo como contexto para a próxima.
Ou seja, a primeira tarefa será executada, seguida pela segunda, que terá acesso ao resultado da
primeira; depois, a terceira, que contará com o resultado da segunda, e assim por diante.
Portanto, éfundamentalquevocêpresteatençãoaolistarsuastasksdeumamaneiraquefaçasentido
dentro do fluxo de trabalho!
Execução da Crew
E para finalmente executá‑la:
result = blog_post_creation_crew.kickoff({'tema': 'Aplicações com inteligência artificial'})
print(result.raw)
print(result.tasks_output[0])
Nesse exemplo, o método kickoff() inicia todo o fluxo de trabalho, coordenando a execução das
tasks pelos agentes e retornando um resultado que pode ser analisado tanto de forma geral quanto
de forma específica, como a saída da primeira task.
Passando Inputs para a Crew
Vocêdeveterpercebidoque, aoexecutarmosacrewcomométodokickoff, passamosoparâmetro
tema com o valor “Aplicações com inteligência artificial”. Dessa forma, conseguimos direcionar o
desenvolvimento do nosso artigo para o conteúdo que gostaríamos de explorar.
Asimov Academy
15


---