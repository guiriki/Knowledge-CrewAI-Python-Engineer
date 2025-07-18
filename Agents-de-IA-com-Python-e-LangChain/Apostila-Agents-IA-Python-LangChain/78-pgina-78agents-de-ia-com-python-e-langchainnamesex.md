## Página 78

Agents de IA com Python e LangChain
Name
Sex
Age
SibSp
\
0
Braund, Mr. Owen Harris
male
22.0
1
1
Cumings, Mrs. John Bradley (Florence Briggs Th...
female
38.0
1
2
Heikkinen, Miss. Laina
female
26.0
0
3
Futrelle, Mrs. Jacques Heath (Lily May Peel)
female
35.0
1
4
Allen, Mr. William Henry
male
35.0
0
Parch
Ticket
Fare Cabin Embarked
0
0
A/5 21171
7.2500
NaN
S
1
0
PC 17599
71.2833
C85
C
2
0
STON/O2. 3101282
7.9250
NaN
S
3
0
113803
53.1000
C123
S
4
0
373450
8.0500
NaN
S
Agora, vamos criar o nosso agent:
chat = ChatOpenAI(model='gpt-3.5-turbo-0125')
agent = create_pandas_dataframe_agent(
chat,
df,
verbose=True,
agent_type='tool-calling',
allow_dangerous_code=True
)
Podemos fazer algumas perguntas ao nosso agent para ver como ele se sai:
agent.invoke({'input': 'Quantas linhas tem na tabela?'})
> Entering new AgentExecutor chain...
Invoking: `python_repl_ast` with `{'query': 'len(df)'}`
891
A tabela possui 891 linhas.
> Finished chain.
{'input': 'Quantas linhas tem na tabela?',
'output': 'A tabela possui 891 linhas.'}
Você pode perceber que o toolkit está utilizando a ferramenta python_repl_ast que nós já con-
hecemos para manipular os dados do nosso DataFrame.
agent.invoke({'input': 'Qual a média da idade dos passageiros?'})
> Entering new AgentExecutor chain...
Invoking: `python_repl_ast` with `{'query': "df['Age'].mean()"}`
29.69911764705882
A média da idade dos passageiros é de aproximadamente 29.70 anos.
Asimov Academy
77


---
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