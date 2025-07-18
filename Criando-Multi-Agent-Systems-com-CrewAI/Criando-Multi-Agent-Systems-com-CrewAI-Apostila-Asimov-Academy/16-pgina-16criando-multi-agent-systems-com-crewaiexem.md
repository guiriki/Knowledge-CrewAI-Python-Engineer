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
## Página 17

Criando Multi Agent Systems com CrewAI
Mas como essa variável tema é utilizada dentro da Crew? Caso você não tenha observado, em
algumas partes dos textos que definimos em nossas Tasks e Agents, deixamos uma variável entre
colchetes chamada {tema}.
Veja o exemplo da task atribuída ao Desenvolvedor de Ideias:
cria_ideias = Task(
description='Crie uma lista com 10 ideias diferentes para posts de blog sobre o tema: {tema}.
As ideias devem ser criativas, relevantes e diversificadas em formato, com foco em engajar
o público-alvo.',
↪
↪
agent=desenvolvedor_de_ideias,
expected_output='Uma lista com 10 ideias de posts, cada uma com um título criativo e um breve
resumo do que o conteúdo abordará.'
↪
)
Na execução da crew, essa variável será substituída pelo valor que passamos no método kickoff.
EsteéumdosrecursospoderososdoCrewAI:acapacidadedepassarinputsdinamicamenteparasuas
tasks e agents. Neste exemplo, utilizamos a variável tema, mas poderíamos ter passado múltiplos
parâmetros diferentes. A flexibilidade que temos permite que essa variável seja aplicada em diversas
partes da nossa aplicação, garantindo que os agents utilizem informações atualizadas e relevantes
ao longo do processo.
Importante! Essas variáveis do CrewAI podem ser incluídas em qualquer parte dos parâmet‑
ros role, goal e backstory dos agents, assim como nos parâmetros description e ex-
pected_output das tasks, proporcionando uma excelente flexibilidade na hora de passar var‑
iáveis para a aplicação.
Conclusão e Próximos Passos
É com grande alegria que chegamos ao final desta aula, onde iniciamos nossa jornada com o Cre‑
wAI desenvolvendo uma aplicação que reflete a essência de como tudo começou aqui na Asimov
em relação às aplicações de IA. Ao criar uma Crew para produção de posts de blog, você não ape‑
nas compreendeu a funcionalidade e a importância das classes Agents, Tasks e Crew, mas também
deu o primeiro passo em direção a um entendimento mais profundo sobre como otimizar processos
com inteligência artificial.
Ao longo deste caminho, percebemos que cada agent tem um papel específico, configurado com
parâmetros que orientam sua atuação. As tasks delimitam as atividades que cada agent deve exe‑
cutar e, finalmente, a crew se torna o laço que une esses sistemas, organizando e orquestrando as
interações entre os agentes e as tarefas.
Asimov Academy
16


---