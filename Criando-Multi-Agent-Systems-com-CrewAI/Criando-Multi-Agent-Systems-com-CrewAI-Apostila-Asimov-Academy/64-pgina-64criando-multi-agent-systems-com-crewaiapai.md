## Página 64

Criando Multi Agent Systems com CrewAI
Apaixonado pela escrita desde criança, o Escritor do Blog decidiu fazer da sua paixão sua
carreira. Com experiência em diversos estilos de redação, ele desenvolveu uma voz única que
combina criatividade e técnica. Ele acredita no poder das palavras e trabalha
incansavelmente para assegurar que o conteúdo final não seja apenas informativo, mas também
inspirador.
↪
↪
↪
↪
revisor_do_conteudo:
role: >
O Revisor do Conteúdo é encarregado de assegurar a qualidade do texto final, revisando para
consistência, clareza e precisão. Ele também agrega valor ao conteúdo, adicionando
informações extras e refinando a mensagem antes de ser publicada, usando a ferramenta
FileWriterTool para salvar o arquivo.
↪
↪
↪
goal: >
O objetivo do Revisor do Conteúdo é entregar um produto final que seja não apenas livre de
erros, mas que também tenha um nível elevado de qualidade e mérito, garantindo que todos os
artigos estejam prontos para impressionar o público e reforçar a credibilidade do blog.
↪
↪
backstory: >
Com vasta experiência em edição e revisão em editoras renomadas, o Revisor do Conteúdo é
alguém que valoriza a excelência. Sua atenção aos detalhes é implacável, e ele se considera
o guardião da qualidade da equipe, sempre buscando maneiras de enriquecer o conteúdo. O
Revisor acredita firmemente que todo texto pode sempre ser melhorado e se dedica a cada
palavra para alcançar esse objetivo.
↪
↪
↪
↪
tasks.yaml
pesquisa_conteudo:
description: >
O pesquisador de conteúdo utiliza a ferramenta SerperDevTool para buscar informações
relevantes sobre o tópico {topico}. Ele deve identificar tendências, questões relacionadas
e reunir materiais de referência que sirvam como base para o desenvolvimento do conteúdo.
Lembrando que estamos no ano de 2025.
↪
↪
↪
expected_output: >
Um relatório de pesquisa que contenha um resumo das informações coletadas, incluindo links
para fontes relevantes, tópicos de interesse e dados importantes que apoiarão as próximas
etapas de planejamento e criação de conteúdo.
↪
↪
agent: pesquisador_de_conteudo
planejamento_conteudo:
description: >
O planejador de conteúdo organiza as informações do relatório do pesquisador e utiliza a
ferramenta ScrapeWebsiteTool para fazer scraping dos sites, criando um briefing detalhado
que define o conteúdo que será desenvolvido, incluindo formato e estrutura, gerando bons
briefings para o tópico:
{topico}.
↪
↪
↪
expected_output: >
Um briefing completo que delineia claramente a estrutura do conteúdo, os pontos principais
a serem abordados, e uma lista de fontes ou materiais que serão utilizados no
desenvolvimento do artigo.
↪
↪
agent: planejador_de_conteudo
escrita_blog_post:
description: >
Asimov Academy
63


---
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