## Página 45

Criando Multi Agent Systems com CrewAI
│
└── __init__.py
└── config/
├── agents.yaml
└── tasks.yaml
Temos alguns arquivos principais que precisamos entender para utilizar as Crews nesta estrutura:
Arquivo
Finalidade
agents.yaml
Define seus agentes de IA e seus papéis
tasks.yaml
Configura tarefas e fluxos de trabalho dos agentes
.env
Armazena chaves de API e variáveis de ambiente
main.py
Ponto de entrada do projeto e fluxo de execução
crew.py
Orquestração e coordenação da equipe
tools/
Diretório para ferramentas personalizadas de agentes
Arquivo .env
Vamos começar analisando o arquivo .env.
Você pode perceber que aqui é definido o modelo que o nosso sistema utilizará. Como definimos no
início o gpt-4o-mini, o comando create já preenche o arquivo com o modelo que solicitei.
Neste arquivo, também adicionamos a chave de API do provedor. No final, teremos um arquivo
como:
MODEL=gpt-4o-mini
OPENAI_API_KEY=MINHA_CHAVE_DE_API
No caso da OpenAI, o nome para fornecer a key é OPENAI_API_KEY. Este nome varia conforme o
provedor!
Asimov Academy
44


---
## Página 46

Criando Multi Agent Systems com CrewAI
Arquivo agents.yaml
Através do arquivo agents.yaml, começamos o desenvolvimento da nossa aplicação. Você lembra
que, ao definir um agente, temos três principais parâmetros que precisamos preencher: role, goal e
backstory.
Neste arquivo YAML, podemos fazer a definição dos nossos agentes e suas descrições de forma clara
e fácil de visualizar, diferente de quando as definições ficavam dentro do código.
As formatações devem seguir o exemplo que vem junto ao criarmos o projeto via linha de comando:
researcher:
role: >
{topic} Senior Data Researcher
goal: >
Uncover cutting-edge developments in {topic}
backstory: >
You're a seasoned researcher with a knack for uncovering the latest
developments in {topic}. Known for your ability to find the most relevant
information and present it in a clear and concise manner.
Você vê que é uma estrutura que utiliza dois pontos e indentação para determinar elementos que
pertencemaoelementoanterior. Nestecaso, temosumagenteresearchersendodefinido. Utilizamos
os dois pontos e a indentação para evidenciar que os parâmetros role, goal e backstory que serão
definidos na sequência fazem parte do researcher declarado anteriormente. O mesmo ocorre com as
definições de role, goal e backstory.
Este arquivo, então, eu modificaria para customizar a minha Crew!
Arquivo tasks.yaml
O mesmo ocorre com o arquivo tasks.yaml. Nele, definimos nossas tasks, também com a formatação
devida, com dois pontos e indentação.
Este é o exemplo padrão contido no projeto que a CrewAI cria para nós:
research_task:
description: >
Conduct a thorough research about {topic}
Make sure you find any interesting and relevant information given
the current year is {current_year}.
expected_output: >
A list with 10 bullet points of the most relevant information about {topic}
agent: researcher
Podemos ver que adicionamos também o parâmetro agent com o nome do agente que executará esta
task, para facilitar o casamento de task e agent.
Asimov Academy
45


---