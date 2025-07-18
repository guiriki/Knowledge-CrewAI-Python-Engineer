## Página 79

Agents de IA com Python e LangChain
> Finished chain.
{'input': 'Qual a média da idade dos passageiros?',
'output': 'A média da idade dos passageiros é de aproximadamente 29.70 anos.'}
agent.invoke({'input': 'Quantos passageiros sobreviveram?'})
> Entering new AgentExecutor chain...
Invoking: `python_repl_ast` with `{'query': "df['Survived'].sum()"}`
342
Houve um total de 342 passageiros que sobreviveram ao acidente.
> Finished chain.
{'input': 'Quantos passageiros sobreviveram?',
'output': 'Houve um total de 342 passageiros que sobreviveram ao acidente.'}
E é impressionante como ele consegue fazer análises que, por mais que sejam simples, seriam comple-
tamente impossíveis para quem desconhece análise de dados. Isso permite uma acessibilidade muito
maior de pessoas a principal ferramenta de análise de dados, o Python!
SQL Database
Agora, vamos ver como criar um agent para manipular e consultar uma base de dados SQL.
Exemplo Prático
Primeiro, vamos importar as bibliotecas necessárias e carregar uma base de dados
de exemplo:
from langchain_community.utilities.sql_database import SQLDatabase
db = SQLDatabase.from_uri('sqlite:///arquivos/Chinook.db')
Vamos criar o nosso agent para SQL:
from langchain_community.agent_toolkits.sql.base import create_sql_agent
from langchain_openai import ChatOpenAI
chat = ChatOpenAI(model='gpt-3.5-turbo-0125')
agent_executor = create_sql_agent(
chat,
db=db,
agent_type='tool-calling',
verbose=True
)
Podemos listar as tools disponíveis no agent:
Asimov Academy
78


---
## Página 80

Agents de IA com Python e LangChain
for tool in agent_executor.tools:
print(tool.name)
print(tool.description)
print()
sql_db_query
Input to this tool is a detailed and correct SQL query, output is a result from the database.
If the query is not correct, an error message will be returned. If an error is returned,
rewrite the query, check the query, and try again. If you encounter an issue with Unknown
column 'xxxx' in 'field list', use sql_db_schema to query the correct table fields.
�→
�→
�→
sql_db_schema
Input to this tool is a comma-separated list of tables, output is the schema and sample rows
for those tables. Be sure that the tables actually exist by calling sql_db_list_tables
first! Example Input: table1, table2, table3
�→
�→
sql_db_list_tables
Input is an empty string, output is a comma-separated list of tables in the database.
sql_db_query_checker
Use this tool to double check if your query is correct before executing it. Always use this
tool before executing a query with sql_db_query!
�→
Vemos que ele possui as seguintes ferramentas acopladas:
• sql_db_query: para realizar uma query na base de dados
• sql_db_schema: para entender a estrutura da base de dados
• sql_db_list_tables: para listar as tabelas da base de dados
• sql_db_query_checker: para verificar se a query gerada pelo sql_db_query está correta.
Vamos fazer uma consulta para descrever a base de dados:
agent_executor.invoke({'input': 'Me descreva a base de dados'})
> Entering new SQL Agent Executor chain...
Invoking: `sql_db_list_tables` with `{}`
Album, Artist, Customer, Employee, Genre, Invoice, InvoiceLine, MediaType, Playlist,
PlaylistTrack, Track
�→
Invoking: `sql_db_schema` with `{'table_names': 'Album, Artist, Customer, Employee, Genre,
Invoice, InvoiceLine, MediaType, Playlist, PlaylistTrack, Track'}`
�→
...
agent_executor.invoke({'input': 'Qual artista possui mais albuns?'})
...
Asimov Academy
79


---