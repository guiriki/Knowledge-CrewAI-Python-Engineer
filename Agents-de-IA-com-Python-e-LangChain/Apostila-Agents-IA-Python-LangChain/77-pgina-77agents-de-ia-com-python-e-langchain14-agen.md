## Página 77

Agents de IA com Python e LangChain
14. Agents Toolkits - Criando Agents para Analisar Dataframes e SQL
Bem-vindos ao nosso último capítulo da apostila de Agents de IA com Python e LangChain. Vamos
explorar estruturas muito poderosas do framework: os Agents Toolkits. Eles nos permitirão criar muito
facilmente agents que podem analisar DataFrames e bases de dados SQL. Nossos objetivos serão:
• Entender o que são Toolkits e como eles são utilizados no LangChain.
• Aprender a criar um agent para analisar DataFrames utilizando Pandas.
• Aprender a criar um agent para manipular e consultar bases de dados SQL.
O que são os Tollkits?
Os Toolkits são conjuntos de ferramentas que, quando combinadas, formam uma aplicação poderosa.
No LangChain, já existem alguns Toolkits prontos que facilitam a criação de agents para tarefas especí-
ficas. Hoje, vamos focar em dois Toolkits principais: Pandas DataFrame e SQL Database. Esses Toolkits
são extremamente úteis para quem trabalha com análise de dados, pois permitem automatizar e
simplificar muitas tarefas.
Pandas DataFrame
Vamos começar com o Toolkit de Pandas DataFrame. Este Toolkit permite que um agent analise um
DataFrame, facilitando a manipulação e a extração de informações.
Exemplo Prático
Primeiro, vamos importar as bibliotecas necessárias e carregar um DataFrame de
exemplo:
from langchain_experimental.agents.agent_toolkits import create_pandas_dataframe_agent
from langchain_openai import ChatOpenAI
import pandas as pd
df = pd.read_csv(
"https://raw.githubusercontent.com/pandas-dev/pandas/main/doc/data/titanic.csv"
)
df.head(5)
Isso nos dá uma visão inicial do DataFrame:
PassengerId
Survived
Pclass
\
0
1
0
3
1
2
1
1
2
3
1
3
3
4
1
1
4
5
0
3
Asimov Academy
76


---
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