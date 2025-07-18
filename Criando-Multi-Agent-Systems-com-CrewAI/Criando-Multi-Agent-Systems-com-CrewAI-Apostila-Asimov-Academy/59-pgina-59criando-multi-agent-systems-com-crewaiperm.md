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
## Página 60

Criando Multi Agent Systems com CrewAI
Tool
Descrição
BrowserbaseLoadToolUma ferramenta para interagir e extrair dados de navegadores da web.
CodeDocsSearchTool Uma Tool otimizada para busca através da documentação de código e
documentos técnicos relacionados.
CodeInterpreterTool Uma ferramenta para interpretar código Python.
ComposioTool
Permite o uso de ferramentas Composio.
CSVSearchTool
Uma Tool projetada para buscar dentro de arquivos CSV, feita
especialmente para lidar com dados estruturados.
DALL‑E Tool
Uma ferramenta para gerar imagens usando a API DALL‑E.
DirectorySearchTool Uma Tool para busca dentro de diretórios, útil para navegar por sistemas
de arquivos.
DOCXSearchTool
Uma Tool voltada para buscar dentro de documentos DOCX, ideal para
processamento de arquivos do Word.
DirectoryReadTool
Facilita a leitura e o processamento das estruturas de diretórios e seu
conteúdo.
EXASearchTool
Uma ferramenta projetada para realizar buscas exaustivas em várias
fontes de dados.
FileReadTool
Permite a leitura e extração de dados de arquivos, suportando diversos
formatos de arquivo.
FirecrawlSearchTool Uma ferramenta para buscar páginas da web usando Firecrawl e retornar
os resultados.
FirecrawlCrawlWebsiteTool
Uma ferramenta para rastrear páginas da web usando Firecrawl.
FirecrawlScrapeWebsiteTool
Uma ferramenta para raspar conteúdos de páginas da web usando
Firecrawl e retornar seu conteúdo.
GithubSearchTool
Uma Tool para buscar dentro de repositórios do GitHub, útil para
pesquisa de código e documentação.
SerperDevTool
Uma ferramenta especializada para fins de desenvolvimento, com
funcionalidades específicas em desenvolvimento.
TXTSearchTool
Uma Tool focada na busca dentro de arquivos de texto (.txt), adequada
para dados não estruturados.
JSONSearchTool
Uma ferramenta projetada para busca dentro de arquivos JSON,
atendendo a manipulação de dados estruturados.
Asimov Academy
59


---