## Página 76

Agents de IA com Python e LangChain
modelo menor localemnte. Ao utilizar modelos maiores, dos principais provedores de modelos de
linguagem como OpenAI, Google ou Anthropic, sugerimos que utilize o Tool Calling.
Hoje aprendemos sobre dois tipos importantes de Agents: Tool Calling e ReAct. Vimos como criar e
utilizar cada um deles, além de entender suas aplicações e limitações. Agora, você está mais preparado
para escolher e implementar o tipo de Agent que melhor se adapta às suas necessidades. Continue
praticando e explorando as possibilidades que esses Agents oferecem!
Asimov Academy
75


---
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