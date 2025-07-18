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
## Página 19

Criando Multi Agent Systems com CrewAI
Desafio ‑ Criação de uma Crew para roteirização de vídeo no YouTube
Neste desafio, você irá criar uma Crew utilizando o CrewAI para roteirizar um vídeo para YouTube. O
objetivo é automatizar o processo criativo de desenvolvimento de conteúdo de vídeo, dividindo as
responsabilidades entre diferentes agentes especializados.
Agentes a serem Criados:
1. Pesquisador: Este agent será responsável por pensar em até 10 ideias diferentes para vídeos
em um determinado tema e selecionar a melhor ideia.
2. Criador da Ideia Central: Depois que a ideia for escolhida, esse agent deverá formular a prin‑
cipal mensagem que será transmitida durante o vídeo.
3. Criador do Hook: Este agent deverá desenvolver os primeiros 30 segundos do vídeo, criando
uma abertura atrativa que capture a atenção do público.
4. Criador do Roteiro: Este agent será encarregado de desenvolver o roteiro completo do vídeo,
estruturando as seções de forma clara e coerente.
O que você deve fazer:
• Defina os agents com suas respectivas responsabilidades e histórias.
• Crie as tasks que cada agent deve executar.
• Organize todos os agents e tasks em uma Crew e configure o processo de execução.
• Utilizeumavariáveldeinput, comotema, epasse‑aparaaCrewusandoométodokickoff()
para ver como essa entrada pode moldar o conteúdo gerado.
Lembre‑se de que você pode adicionar outros agents se achar necessário, sempre visando otimizar o
processo criativo.
Ao concluir o desafio, sinta‑se à vontade para compartilhar sua implementação! Lembre‑se de que,
no desenvolvimento de aplicações, o importante não é acertar em tudo, já que há infinitas formas
de se estruturar uma solução, mas sim praticar e experimentar. Cada tentativa irá lhe proporcionar
aprendizado e ajudar a aperfeiçoar suas habilidades com o CrewAI. Boa sorte e divirta‑se criando!
Asimov Academy
18


---