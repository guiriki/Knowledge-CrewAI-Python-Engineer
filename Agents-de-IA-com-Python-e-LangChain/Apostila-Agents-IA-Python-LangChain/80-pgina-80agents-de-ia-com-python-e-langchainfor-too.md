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
## Página 81

Agents de IA com Python e LangChain
Invoking: `sql_db_query` with `{'query': 'SELECT Artist.Name, COUNT(Album.AlbumId) AS
Number_of_Albums FROM Artist JOIN Album ON Artist.ArtistId = Album.ArtistId GROUP BY
Artist.ArtistId ORDER BY Number_of_Albums DESC LIMIT 1'}`
�→
�→
[('Iron Maiden', 21)]O artista que possui mais álbuns é "Iron Maiden", com um total de 21
álbuns.
�→
> Finished chain.
{'input': 'Qual artista possui mais albuns?',
'output': 'O artista que possui mais álbuns é "Iron Maiden", com um total de 21 álbuns.'}
Podemos ver que o agente é capaz de realizar queries complexas a base de dados, e tudo de forma
muito simples!
Neste capítulo, aprendemos a criar agents utilizando Toolkits para analisar DataFrames e bases de
dados SQL. Vimos como esses Toolkits podem simplificar e automatizar tarefas complexas de análise
de dados. Esperamos que vocês tenham gostado e que essas ferramentas sejam úteis no dia a dia de
vocês.
Asimov Academy
80


---