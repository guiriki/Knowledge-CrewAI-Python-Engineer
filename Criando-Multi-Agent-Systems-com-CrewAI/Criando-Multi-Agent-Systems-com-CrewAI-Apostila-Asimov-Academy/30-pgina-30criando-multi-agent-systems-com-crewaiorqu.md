## Página 30

Criando Multi Agent Systems com CrewAI
orquestrar_agentes_e_tarefas:
description: >
Implementar o crew.py conectando agentes e tasks, configurando o fluxo de execução.
Sistema solicitado: {especificacoes_sistema}
expected_output: >
Arquivo crew.py funcional, com integração completa entre agents.yaml e tasks.yaml.
O código final deve parecer com:
```python
from crewai import Agent, Crew, Process, Task
from crewai.project import CrewBase, agent, crew, task
from dotenv import load_dotenv, find_dotenv
_ = load_dotenv(find_dotenv())
@CrewBase
class NomeDaCrew():
"""Teste crew"""
agents_config = 'config/agents.yaml'
tasks_config = 'config/tasks.yaml'
@agent
def nome_do_primeiro_agente(self) -> Agent:
return Agent(
config=self.agents_config['nome_do_primeiro_agente'],
verbose=True
)
@agent
def nome_do_segundo_agente(self) -> Agent:
return Agent(
config=self.agents_config['nome_do_segundo_agente'],
verbose=True
)
@task
def nome_da_primeira_task(self) -> Task:
return Task(
config=self.tasks_config['nome_da_primeira_task'],
)
@task
def nome_da_primeira_task(self) -> Task:
return Task(
config=self.tasks_config['revisa_arquivo_yaml_agentes'],
)
@task
def nome_da_segunda_task(self) -> Task:
return Task(
config=self.tasks_config['nome_da_segunda_task'],
)
@crew
Asimov Academy
29


---
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