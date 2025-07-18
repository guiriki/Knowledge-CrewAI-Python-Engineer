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
## Página 67

Criando Multi Agent Systems com CrewAI
@crew
def crew(self) -> Crew:
return Crew(
agents=self.agents,
tasks=self.tasks,
verbose=True,
)
Podemos ver que estamos utilizando 3 ferramentas: ‑ SerperDevTool: Faz uma busca no Google
para um determinado assunto, encontrando assim páginas na web que possam ser relevantes. ‑
ScrapeWebsiteTool: É responsável por acessar essas páginas web e fazer o download do conteúdo
delas, permitindo que os modelos leiam seus conteúdos. ‑ FileWriterTool: Pode escrever um arquivo
no computador onde a aplicação está rodando.
Já demos passos importantes para transformar o gerador de blog posts em uma ferramenta real‑
mente útil!
Asimov Academy
66


---