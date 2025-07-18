## Página 33

Agents de IA com Python e LangChain
tool_acontecimentos = convert_to_openai_function(ListaAcontecimentos)
tool_acontecimentos
Agora, vamos criar uma chain para extrair essas informações do texto:
from langchain.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
prompt = ChatPromptTemplate.from_messages([
('system', 'Extraia as frases de acontecimentos. Elas devem ser extraídas integralmente'),
('user', '{input}')
])
chat = ChatOpenAI()
chain = (prompt
| chat.bind(functions=[tool_acontecimentos], function_call={'name':
'ListaAcontecimentos'}))
�→
Vamos invocar a chain com o nosso texto:
chain.invoke({'input': texto})
O resultado será algo assim:
AIMessage(content='', additional_kwargs={'function_call': {'arguments':
'{"acontecimentos":[{"data":"1976-04-01","acontecimento":"A Apple foi fundada por Steve
Wozniak, Steve Jobs e Ronald Wayne."},{"data":"1975-07","acontecimento":"Início das vendas
do Apple I com o preço de US$ 666,66."},{"data":"1977","acontecimento":"A Apple recebeu
aporte de Mike Markkula e um empréstimo do Bank of America."}]}', 'name':
'ListaAcontecimentos'}}, response_metadata={'token_usage': {'completion_tokens': 101,
'prompt_tokens': 325, 'total_tokens': 426}, 'model_name': 'gpt-3.5-turbo',
'system_fingerprint': None, 'finish_reason': 'stop', 'logprobs': None},
id='run-ad3b401a-654f-4d2a-b120-630b0d964429-0')
�→
�→
�→
�→
�→
�→
�→
�→
Para tornar a saída mais limpa, podemos utilizar um OutputParser:
from langchain.output_parsers.openai_functions import JsonOutputFunctionsParser
chain = (prompt
| chat.bind(functions=[tool_acontecimentos], function_call={'name':
'ListaAcontecimentos'})
�→
| JsonOutputFunctionsParser())
chain.invoke({'input': texto})
O resultado será:
{'acontecimentos': [{'data': '1976-04-01',
'acontecimento': 'A Apple foi fundada em 1 de abril de 1976 por Steve Wozniak, Steve Jobs e
Ronald Wayne com o nome de Apple Computers, na Califórnia.'},
�→
{'data': '1975-07',
'acontecimento': 'As vendas do Apple I começaram em julho de 1976 com o preço de US$
666,66, aproximadamente 200 unidades foram vendidas.'},
�→
Asimov Academy
32


---
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