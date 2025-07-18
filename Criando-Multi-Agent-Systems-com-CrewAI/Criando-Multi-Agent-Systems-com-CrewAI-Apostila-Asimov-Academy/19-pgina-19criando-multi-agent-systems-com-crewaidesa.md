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