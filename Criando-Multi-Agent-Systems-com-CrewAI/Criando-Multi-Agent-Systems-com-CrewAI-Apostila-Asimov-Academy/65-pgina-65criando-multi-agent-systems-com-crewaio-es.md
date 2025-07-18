## Página 65

Criando Multi Agent Systems com CrewAI
O escritor do blog utiliza o briefing desenvolvido pelo planejador de conteúdo para criar
um artigo completo do topico de {topico}, garantindo que todas as informações sejam
apresentadas de maneira coesa e que o texto atenda aos objetivos da equipe.
↪
↪
expected_output: >
O artigo de blog escrito, que deve ser envolvente, claro e informativo, abordando todos os
pontos discutidos no briefing e pronto para a revisão final.
↪
agent: escritor_do_blog
revisao_conteudo:
description: >
O revisor do conteúdo revisa o artigo escrito para assegurar que não haja erros de
gramática, ortografia ou clareza. Ele também adiciona informações relevantes que possam
enriquecer o texto.
↪
↪
expected_output: >
Um documento revisado e polido, livre de erros, que inclui todas as melhorias feitas e que
está formatado corretamente para publicação, pronto para ser disponibilizado ao público.
↪
agent: revisor_do_conteudo
salva_conteudo:
description: >
Salva o conteúdo utilizando a tool FileWriterTool, criando um nome de arquivo que faça
sentido com relação ao conteúdo do texto.
↪
expected_output: >
Arquivo salvo.
agent: revisor_do_conteudo
crew.py
from crewai import Agent, Crew, Process, Task
from crewai_tools import SerperDevTool, ScrapeWebsiteTool, FileWriterTool
from crewai.project import CrewBase, agent, crew, task
from dotenv import load_dotenv, find_dotenv
_ = load_dotenv(find_dotenv())
serper = SerperDevTool()
scraper = ScrapeWebsiteTool()
file_write = FileWriterTool()
@CrewBase
class ContentCreationCrew():
"""Crew for content creation process"""
agents_config = 'config/agents.yaml'
tasks_config = 'config/tasks.yaml'
@agent
def pesquisador_de_conteudo(self) -> Agent:
return Agent(
config=self.agents_config['pesquisador_de_conteudo'],
verbose=True,
tools=[serper]
Asimov Academy
64


---
## Página 66

Criando Multi Agent Systems com CrewAI
)
@agent
def planejador_de_conteudo(self) -> Agent:
return Agent(
config=self.agents_config['planejador_de_conteudo'],
verbose=True,
tools=[scraper]
)
@agent
def escritor_do_blog(self) -> Agent:
return Agent(
config=self.agents_config['escritor_do_blog'],
verbose=True
)
@agent
def revisor_do_conteudo(self) -> Agent:
return Agent(
config=self.agents_config['revisor_do_conteudo'],
verbose=True,
)
@task
def pesquisa_conteudo(self) -> Task:
return Task(
config=self.tasks_config['pesquisa_conteudo'],
)
@task
def planejamento_conteudo(self) -> Task:
return Task(
config=self.tasks_config['planejamento_conteudo'],
)
@task
def escrita_blog_post(self) -> Task:
return Task(
config=self.tasks_config['escrita_blog_post'],
)
@task
def revisao_conteudo(self) -> Task:
return Task(
config=self.tasks_config['revisao_conteudo'],
)
@task
def salva_conteudo(self) -> Task:
return Task(
config=self.tasks_config['salva_conteudo'],
tools=[file_write]
)
Asimov Academy
65


---