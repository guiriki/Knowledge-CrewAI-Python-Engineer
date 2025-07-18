## Página 56

Criando Multi Agent Systems com CrewAI
está disponível dentro de sua inteligência. É como se os modelos vivessem sempre há um ano atrás
do dia de hoje, ignorando completamente a informação nova que ocorreu neste último ano. Por isso,
quando tentamos gerar código para bibliotecas novas, como a própria CrewAI, os códigos estão sem‑
pre desatualizados, pois o modelo ignora toda evolução da biblioteca no último ano.
Paracontornaressalimitação, podemoscriarferramentasdebuscadeinformações. Algunsexemplos
incluem:
• Ferramentas de web crawl para buscar na internet informações recentes.
• Ferramentas de acesso a bancos de dados, oferecendo ao modelo acesso a informações em
diversos tipos de banco de dados, como SQL, Postgres, MongoDB, etc.
• Ferramentas de leitura de arquivos de texto, arquivos PDF, CSV, etc.
• Ferramentas de acesso a informações de APIs diversas, como APIs de clima, trânsito, tráfego
aéreo, etc.
Tools de atuação
Agora estamos falando de dar mais autonomia aos modelos. Queremos que nossos modelos possam
gerar soluções além da geração de texto — queremos que eles interajam, atuem e modifiquem seu
entorno. É aqui que entram as tools de atuação, capazes de mudar o estado de aplicações e sistemas
fora do escopo da aplicação. São ferramentas que atuam no mundo real.
Alguns exemplos incluem:
• Ferramentas para enviar um e‑mail, uma mensagem SMS, ou uma mensagem no WhatsApp ou
Telegram.
• Ferramentas para adicionar ou deletar dados de diversos bancos de dados, como SQL, Postgres,
MongoDB, etc.
• Ferramentas para criar e deletar arquivos em um computador.
• Ferramentas para criação de imagens, áudio, etc.
Como usar tools?
Para usar as Tools no CrewAI, você precisa começar instalando o pacote de ferramentas adicionais.
Basta rodar o seguinte comando no seu terminal:
pip install 'crewai[tools]'
Aqui está um exemplo de como você pode usar algumas Tools no seu código:
import os
from crewai import Agent, Task, Crew
Asimov Academy
55


---
## Página 57

Criando Multi Agent Systems com CrewAI
from crewai_tools import (
DirectoryReadTool,
FileReadTool,
SerperDevTool,
WebsiteSearchTool
)
# Configurando as chaves de API
os.environ["SERPER_API_KEY"] = "Sua Chave"
# Chave da API serper.dev
os.environ["OPENAI_API_KEY"] = "Sua Chave"
# Instanciando as ferramentas
docs_tool = DirectoryReadTool(directory='./blog-posts')
file_tool = FileReadTool()
search_tool = SerperDevTool()
web_rag_tool = WebsiteSearchTool()
# Criando agentes
researcher = Agent(
role='Market Research Analyst',
goal='Provide up-to-date market analysis of the AI industry',
backstory='An expert analyst with a keen eye for market trends.',
tools=[search_tool, web_rag_tool],
verbose=True
)
writer = Agent(
role='Content Writer',
goal='Craft engaging blog posts about the AI industry',
backstory='A skilled writer with a passion for technology.',
tools=[docs_tool, file_tool],
verbose=True
)
# Definindo tarefas
research = Task(
description='Research the latest trends in the AI industry and provide a summary.',
expected_output='A summary of the top 3 trending developments in the AI industry with a
unique perspective on their significance.',
↪
agent=researcher
)
write = Task(
description='Write an engaging blog post about the AI industry, based on the research
analyst’s summary. Draw inspiration from the latest blog posts in the directory.',
↪
expected_output='A 4-paragraph blog post formatted in markdown with engaging, informative,
and accessible content, avoiding complex jargon.',
↪
agent=writer,
output_file='blog-posts/new_post.md'
# O post final será salvo aqui
)
# Montando uma crew
crew = Crew(
agents=[researcher, writer],
Asimov Academy
56


---