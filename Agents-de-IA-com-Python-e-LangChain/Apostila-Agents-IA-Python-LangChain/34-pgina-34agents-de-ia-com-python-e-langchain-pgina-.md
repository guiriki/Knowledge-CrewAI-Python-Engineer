## Página 34

Agents de IA com Python e LangChain
{'data': '1977',
'acontecimento': 'Em 1977 a empresa conseguiu o aporte de Mike Markkula e um empréstimo do
Bank of America.'}]}
�→
Se quisermos uma saída ainda mais limpa, podemos especificar a chave de saída ao utilizarmos o
JsonKeyOutputFunctionsParser:
from langchain.output_parsers.openai_functions import JsonKeyOutputFunctionsParser
chain = (prompt
| chat.bind(functions=[tool_acontecimentos], function_call={'name':
'ListaAcontecimentos'})
�→
| JsonKeyOutputFunctionsParser(key_name='acontecimentos'))
chain.invoke({'input': texto})
O resultado final será:
[{'data': '1976-04-01',
'acontecimento': 'Apple foi fundada por Steve Wozniak, Steve Jobs e Ronald Wayne.'},
{'data': '1975',
'acontecimento': 'Demonstração do primeiro protótipo da empresa, o Apple I, na Homebrew
Computer Club.'},
�→
{'data': '1976-07',
'acontecimento': 'Início das vendas do Apple I com o preço de US$ 666,66.'},
{'data': '1977',
'acontecimento': 'Empresa recebeu aporte de Mike Markkula e empréstimo do Bank of
America.'}]
�→
Extraindo Informações da Web
A extração de informações também pode ser muito útil quando combinada com técnicas de WebScrap-
ing. Vamos ver um exemplo de como extrair informações de uma página web.
Vamos utilizar a página de blog da Asimov Academy como exemplo:
Primeiro, vamos carregar a página utilizando o document_loader do LangChain:
from langchain_community.document_loaders.web_base import WebBaseLoader
loader = WebBaseLoader('https://hub.asimov.academy/blog/')
page = loader.load()
page
Asimov Academy
33


---
## Página 35

Agents de IA com Python e LangChain
O conteúdo da página estará desformatado, então precisamos definir uma estrutura para os posts do
blog:
from pydantic import BaseModel, Field
from typing import List
from langchain_core.utils.function_calling import convert_to_openai_function
class BlogPost(BaseModel):
'''Informações sobre um post de blog'''
titulo: str = Field(description='O título do post de blog')
autor: str = Field(description='O autor do post de blog')
data: str = Field(description='A data de publicação do post de blog')
class BlogSite(BaseModel):
'''Lista de blog posts de um site'''
posts: List[BlogPost] = Field(description='Lista de posts de blog do site')
tool_blog = convert_to_openai_function(BlogSite)
tool_blog
Agora, vamos criar uma chain para extrair essas informações:
from langchain.output_parsers.openai_functions import JsonKeyOutputFunctionsParser
from langchain.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
prompt = ChatPromptTemplate.from_messages([
('system', 'Extraia da página todos os posts de blog com autor e data de publicação'),
('user', '{input}')
])
chat = ChatOpenAI()
chain = (prompt
| chat.bind(functions=[tool_blog], function_call={'name': 'BlogSite'})
| JsonKeyOutputFunctionsParser(key_name='posts'))
Vamos invocar a chain com o conteúdo da página:
chain.invoke({'input': page})
O resultado será:
[{'titulo': 'Python ou Power BI: qual ferramenta é melhor para criar dashboards?',
'autor': 'Renata Lopes',
'data': '23-05-24'},
{'titulo': 'Try e Except em Python - Entenda como lidar com erros',
'autor': 'Adriano Soares',
'data': '22-05-24'},
{'titulo': 'Print em Python: entenda o que é a função print e onde usá-la',
'autor': 'Juliano Faccioni',
'data': '21-05-24'},
{'titulo': 'Exemplos de programas em Python - Aprenda fazendo',
'autor': 'Adriano Soares',
'data': '16-05-24'},
{'titulo': 'Qual linguagem de programação aprender? Guia completo para iniciantes',
Asimov Academy
34


---