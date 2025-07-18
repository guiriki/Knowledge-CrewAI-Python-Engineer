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
## Página 58

Criando Multi Agent Systems com CrewAI
tasks=[research, write],
verbose=True,
planning=True,
# Habilitar o recurso de planejamento
)
# Executando as tarefas
crew.kickoff()
### Analisando o código
Vamos analisar passo-a-passo, compreendendo os elementos que se referem a adição da
#### Importação das Tools
```python
from crewai_tools import (
DirectoryReadTool,
FileReadTool,
SerperDevTool,
WebsiteSearchTool
)
• Aquiestamosimportandováriasclassesdeferramentasdisponíveisnomódulocrewai_tools.
Cada uma dessas classes representa uma Tool específica que pode ser utilizada pelos agentes.
Por exemplo:
– DirectoryReadTool: Essa ferramenta é utilizada para ler arquivos de um diretório
específico. É útil quando você precisa acessar e processar vários arquivos que estão orga‑
nizados em uma pasta.
– FileReadTool: Esta Tool permite que os agentes leiam o conteúdo de arquivos, sejam
eles TXT, PDF, CSV, entre outros. É ideal para operações que requerem a extração de infor‑
mações de documentos.
– SerperDevTool: Esta ferramenta interage com a API Serper.dev, possibilitando que os
agentes busquem informações na web. É extremamente útil para obter dados atualizados
e relevantes que não estão incorporados na base de conhecimento do modelo.
– WebsiteSearchTool: Similar à SerperDevTool, esta ferramentas permite a busca
de informações em páginas da web, ampliando ainda mais a capacidade dos agentes de
encontrar dados externos.
A biblioteca CrewAI possui diversas Tools diferentes já criadas e prontas para uso, cada uma com fun‑
cionalidades específicas que ajudam a melhorar a interação dos agentes com o mundo externo. Isso
Asimov Academy
57


---