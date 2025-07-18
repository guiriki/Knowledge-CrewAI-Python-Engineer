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
## Página 47

Criando Multi Agent Systems com CrewAI
Arquivo crew.py
Agora vamos para o arquivo crew.py, onde fazemos a criação da nossa Crew de fato. É ele que im‑
portará as definições de agents e tasks, definirá o tipo do processo e combinará as tools aos agents,
conforme necessário, o que veremos mais adiante no curso.
Este é o exemplo que vem ao criarmos o projeto inicialmente:
from crewai import Agent, Crew, Process, Task
from crewai.project import CrewBase, agent, crew, task
@CrewBase
class ProjetoTeste():
"""ProjetoTeste crew"""
agents_config = 'config/agents.yaml'
tasks_config = 'config/tasks.yaml'
@agent
def researcher(self) -> Agent:
return Agent(
config=self.agents_config['researcher'],
verbose=True
)
@agent
def reporting_analyst(self) -> Agent:
return Agent(
config=self.agents_config['reporting_analyst'],
verbose=True
)
@task
def research_task(self) -> Task:
return Task(
config=self.tasks_config['research_task'],
)
@task
def reporting_task(self) -> Task:
return Task(
config=self.tasks_config['reporting_task'],
output_file='report.md'
)
@crew
def crew(self) -> Crew:
"""Creates the ProjetoTeste crew"""
return Crew(
agents=self.agents,
tasks=self.tasks,
process=Process.sequential,
Asimov Academy
46


---