## Página 31

Criando Multi Agent Systems com CrewAI
def crew(self) -> Crew:
return Crew(
agents=self.agents,
tasks=self.tasks,
verbose=True,
)
```
Retorne apenas o código python na sua resposta!
agent: desenvolvedor_de_orquestracao
from crewai import Agent, Crew, Process, Task
from crewai.project import CrewBase, agent, crew, task
@CrewBase
class CrewCreator():
"""CrewCreator crew"""
agents_config = 'config/agents.yaml'
tasks_config = 'config/tasks.yaml'
@agent
def product_owner(self) -> Agent:
return Agent(
config=self.agents_config['product_owner'],
verbose=True
)
@agent
def desenvolvedor_de_agentes(self) -> Agent:
return Agent(
config=self.agents_config['desenvolvedor_de_agentes'],
verbose=True
)
@agent
def desenvolvedor_de_tarefas(self) -> Agent:
return Agent(
config=self.agents_config['desenvolvedor_de_tarefas'],
verbose=True
)
@agent
def desenvolvedor_de_orquestracao(self) -> Agent:
return Agent(
config=self.agents_config['desenvolvedor_de_orquestracao'],
verbose=True
)
@task
def definir_requisitos_e_escopo(self) -> Task:
return Task(
config=self.tasks_config['definir_requisitos_e_escopo'],
)
Asimov Academy
30


---
## Página 32

Criando Multi Agent Systems com CrewAI
@task
def especificar_agentes(self) -> Task:
return Task(
config=self.tasks_config['especificar_agentes'],
output_file='output/agents.yaml'
)
@task
def definir_tarefas(self) -> Task:
return Task(
config=self.tasks_config['definir_tarefas'],
output_file='output/tasks.yaml'
)
@task
def orquestrar_agentes_e_tarefas(self) -> Task:
return Task(
config=self.tasks_config['orquestrar_agentes_e_tarefas'],
output_file='output/crew.py'
)
@crew
def crew(self) -> Crew:
"""Creates the CrewCreator crew"""
return Crew(
agents=self.agents, # Automatically created by the @agent decorator
tasks=self.tasks, # Automatically created by the @task decorator
process=Process.sequential,
verbose=True,
)
Asimov Academy
31


---