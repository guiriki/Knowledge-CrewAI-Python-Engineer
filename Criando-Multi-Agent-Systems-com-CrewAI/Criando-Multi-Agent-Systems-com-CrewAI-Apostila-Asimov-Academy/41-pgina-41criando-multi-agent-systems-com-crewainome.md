## Página 41

Criando Multi Agent Systems com CrewAI
nome_da_task_2:
...
agent: desenvolvedor_de_tarefas
orquestrar_agentes_e_tarefas:
description: >
Implementar o crew.py conectando agentes e tasks, configurando o fluxo de execuçã
expected_output: >
Arquivo crew.py funcional, com integração completa entre agents.yaml e tasks.yam
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
Asimov Academy
40


---
## Página 42

Criando Multi Agent Systems com CrewAI
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
def crew(self) -> Crew:
return Crew(
agents=self.agents,
tasks=self.tasks,
verbose=True,
)
```
agent: desenvolvedor_de_orquestracao
E já temos a base dono nosso projeto. Na próxima aula vamos testá‑lo e colocá‑lo para rodar!
Até lá!
Asimov Academy
41


---