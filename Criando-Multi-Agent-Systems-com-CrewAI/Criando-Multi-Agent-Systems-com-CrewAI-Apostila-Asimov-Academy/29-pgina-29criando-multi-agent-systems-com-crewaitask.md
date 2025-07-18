## Página 29

Criando Multi Agent Systems com CrewAI
tasks.yaml
definir_requisitos_e_escopo:
description: >
Identificar as funcionalidades necessárias para o sistema e documentar os requisitos de
forma clara.
↪
Sistema solicitado: {especificacoes_sistema}
expected_output: >
Documento de requisitos detalhado, alinhado com as expectativas dos stakeholders.
agent: product_owner
especificar_agentes:
description: >
Definir os agentes no agents.yaml, incluindo seus papéis e permissões dentro do sistema.
Sistema solicitado: {especificacoes_sistema}
expected_output: >
Arquivo agents.yaml completo, com agentes especificados e documentados.
O formato é o seguinte:
nome_do_agente:
role: >
Descreve a função e a especialização do agente dentro da equipe. Aqui você define o
papel do agente e sua expertise na aplicação.
↪
goal: >
O objetivo individual que guia a tomada de decisões do agente. Este campo define o que o
agente busca alcançar com suas ações.
↪
backstory: >
Contextualiza o agente, fornecendo informações sobre sua personalidade, experiência e
como ele se relaciona com o restante da equipe.
↪
nome_do_agente_2:
...
Retorne apenas o arquivo solicitado!
agent: desenvolvedor_de_agentes
definir_tarefas:
description: >
Criar o tasks.yaml, descrevendo as ações necessárias para cada task, incluindo entradas e
saídas.
↪
Sistema solicitado: {especificacoes_sistema}
expected_output: >
Arquivo tasks.yaml estruturado com tasks claras e detalhadas.
O formato é o seguinte:
nome_da_task:
description: >
Uma declaração clara e concisa sobre o que a tarefa envole. Este campo deve especificar
exatamente o que o agente precisa fazer para completar a tarefa. Ele não deve descrever o
agente, e sim a task que ele executará.
↪
↪
expected_output: >
Uma descrição detalhada do que a conclusão da tarefa deve produzir. O que se espera como
resultado final após a tarefa ser executada.
↪
agent: nome_do_agente (nome conforme arquivo de agentes)
nome_da_task_2:
...
Retorne apenas o arquivo solicitado!
agent: desenvolvedor_de_tarefas
Asimov Academy
28


---
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