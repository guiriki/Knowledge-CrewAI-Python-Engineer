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
## Página 18

Criando Multi Agent Systems com CrewAI
Parabéns por ter criado sua primeira crew e por dar esse passo importante na sua trajetória de apren‑
dizado em IA! É emocionante ver como, ao combinar o poder das LLMs e a estrutura do CrewAI, pode‑
mos aumentar a produtividade e a eficiência em processos criativos.
Dúvidas sobre criação de Agents, Tasks e Crews
Caso tenha alguma dúvida sobre como utilizar qualquer uma das classes, criamos a tabela abaixo
para ajudá‑lo a consultar as funcionalidades de cada parâmetro:
Classe ParâmetroDescrição
Agent role
Descreve a função do agent dentro do sistema, indicando qual tarefa ele está
designado a executar.
goal
Define o objetivo principal do agent, ou seja, o que se espera que ele alcance
ao executar sua função.
backstoryFornece um contexto que ajuda a moldar a personalidade e a abordagem do
agent em suas tarefas.
verbose Permite que o agent registre informações detalhadas durante sua execução
quando definido como True, facilitando a depuração e análise de
performance.
Task
description
Orienta sobre o que a task deve realizar, detalhando as ações específicas que
o agent deve executar.
agent
Indica qual agent é responsável pela execução da task.
expected_output
Descreve o resultado esperado da task, que é utilizado para validar se a
execução foi bem‑sucedida.
Crew
agents
Recebe uma lista de agents que farão parte da crew, permitindo a definição
da equipe e suas especializações.
tasks
Recebe uma lista de tasks que serão executadas pela crew, organizando o
fluxo de trabalho.
process Define como as tasks serão executadas, seja de forma sequencial ou
conforme um fluxo hierárquico, estabelecendo a dinâmica da colaboração.
Asimov Academy
17


---