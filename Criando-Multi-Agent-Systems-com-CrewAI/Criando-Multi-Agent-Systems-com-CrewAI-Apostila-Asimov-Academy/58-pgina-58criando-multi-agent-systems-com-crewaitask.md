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
## Página 59

Criando Multi Agent Systems com CrewAI
permite que você escolha e utilize as ferramentas mais adequadas para as necessidades do seu pro‑
jeto, facilitando o desenvolvimento e a implementação de soluções mais robustas.
Instanciação das Tools
docs_tool = DirectoryReadTool(directory='./blog-posts')
file_tool = FileReadTool()
search_tool = SerperDevTool()
web_rag_tool = WebsiteSearchTool()
• Aqui, criamos instâncias das Tools.
– DirectoryReadTool recebe um parâmetro (directory) que especifica qual pasta
deve ser lida para buscar arquivos.
– FileReadTool, SerperDevTool e WebsiteSearchTool são instanciados sem
parâmetros necessários. Isso significa que eles têm configurações padrão definidas na
própria classe.
Adicionando Tools aos Agentes
researcher = Agent(
role='Market Research Analyst',
goal='Provide up-to-date market analysis of the AI industry',
backstory='An expert analyst with a keen eye for market trends.',
tools=[search_tool, web_rag_tool],
verbose=True
)
• Aocriaroagenteresearcher,estamosassociandoasToolssearch_tooleweb_rag_tool
a ele. Isso significa que, durante sua execução, esse agente poderá utilizar essas ferramentas
para realizar tarefas relacionadas a busca de informações e interação com a web.
• O mesmo se aplica ao agente writer, que tem docs_tool e file_tool como suas ferra‑
mentas.
Tools disponibilizadas pela CrewAI
Uma das grandes vantagens da biblioteca CrewAI é a variedade de Tools já construídas pelos desen‑
volvedores, que facilitam o trabalho com os agentes e expandem suas capacidades. Essas ferramen‑
tassãoprojetadasparalidarcomdiferentestiposdetarefaseinterações, tornandosuaaplicaçãomais
robusta e eficiente. Vamos dar uma olhada nas principais Tools disponíveis:
Asimov Academy
58


---