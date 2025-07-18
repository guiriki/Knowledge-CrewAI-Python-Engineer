## Página 72

Criando Multi Agent Systems com CrewAI
Integrando Ferramentas do LangChain ao CrewAI
Mas vamos ver, na prática, como podemos fazer isso. A estrutura será similar à criação de uma ferra‑
menta personalizada, com a diferença de que a classe da ferramenta do LangChain será importada e
o método _run apenas executará a Tool da seguinte forma:
import os
from dotenv import load_dotenv
from crewai import Agent, Task, Crew
from crewai.tools import BaseTool
from pydantic import Field
from langchain_community.utilities import GoogleSerperAPIWrapper
# Configure sua chave SERPER_API_KEY em um arquivo .env, por exemplo:
# SERPER_API_KEY=<sua chave da API>
load_dotenv()
class SearchTool(BaseTool):
name: str = "Search"
description: str = "Útil para consultas baseadas em busca. Use isso para encontrar
informações atuais sobre mercados, empresas e tendências."
↪
search: GoogleSerperAPIWrapper = Field(default_factory=GoogleSerperAPIWrapper)
def _run(self, query: str) -> str:
"""Executa a consulta de busca e retorna os resultados"""
try:
return self.search.run(query)
except Exception as e:
return f"Erro ao realizar a busca: {str(e)}"
No exemplo acima, estamos criando uma ferramenta de busca chamada SearchTool, que utiliza a
classe GoogleSerperAPIWrapper do LangChain para buscar resultados no Google.
Notem que definimos a ferramenta GoogleSerperAPIWrapper do LangChain como um atributo
da classe que estamos criando:
class SearchTool(BaseTool):
#...
search: GoogleSerperAPIWrapper = Field(default_factory=GoogleSerperAPIWrapper)
E depois podemos utilizar essa ferramenta dentro do nosso método _run:
def _run(self, query: str) -> str:
#...
return self.search.run(query)
#...
Com essa simplicidade, temos acesso a todas as ferramentas do framework LangChain!
Aproveitem para dar uma olhada nas ferramentas existentes e comentem aqui conosco quais delas
fazem sentido para vocês!
Asimov Academy
71


---
## Página 73

Criando Multi Agent Systems com CrewAI
14. Finalizando o curso
Parabéns, meu amigo! Você chegou ao final do nosso curso “Criando Multiagent Systems com Cre‑
wAI”! Para encerrar, vamos fazer uma breve recapitulação para fixar as ideias que exploramos, além
de te dar algumas dicas para o futuro.
Introdução – Recapitulando o curso
Desde o início, nosso objetivo foi mostrar como quebrar problemas complexos em partes menores e
mais fáceis de lidar. A ideia é simples: assim como em uma equipe, cada membro tem uma função
específica e contribui para o sucesso do projeto.
Vimos como dividir as tarefas e organizar os agents, tasks, crews, processes e tools é fundamental
para resolver desafios complicados com mais clareza e eficiência. Esse é o propósito do framework
CrewAI!
Recapitulação dos conceitos fundamentais
• Agents – Aprendemos que cada agente deve ter uma função bem definida, com um role, goal
e backstory claros. Assim, cada “pessoa” da nossa crew sabe exatamente no que focar.
• Tasks – Discutimos a importância de planejar direitinho as atividades: tasks de reflexão (como
planejamento e revisão) mostram que dar um tempo para pensar pode render resultados bem
melhores do que tentar fazer tudo de uma vez, sem pausas, no famigerado “zero‑shot”.
• Crews – Montar a crew é como montar um time competente: quando as interações e o fluxo de
trabalho estão organizados, tudo funciona de forma harmoniosa e os resultados ficam muito
mais incríveis.
• Tools – As ferramentas expandem as capacidades dos nossos modelos. Seja para buscar da‑
dos, interagir com APIs ou até executar ações específicas, as tools – incluindo as que criamos
personalizadas – são essenciais para transformar ideias em soluções reais.
Asimov Academy
72


---