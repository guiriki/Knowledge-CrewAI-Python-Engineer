## Página 32

Agents de IA com Python e LangChain
06. Extraction - Extraindo e Estruturando Informações de Textos
Olá, pessoal! Bem-vindos a mais um capítulo do nosso curso de Agents de IA com Python e LangChain.
Hoje vamos explorar mais uma aplicação muito interessante e prática ao utilizarmos funções com
modelos de linguagem: a extração de informações de textos. Essa técnica é extremamente útil quando
precisamos lidar com grandes volumes de dados textuais e queremos extrair informações específicas
de forma estruturada. Nosso objetivo hoje será:
• Entender o conceito de extração de informações de textos.
• Aprender a utilizar funções externas para extrair dados específicos.
• Implementar um exemplo prático de extração de datas e acontecimentos de um texto.
• Explorar a aplicação de extração de informações da web utilizando WebScraping.
Vamos começar com um exemplo simples, extraindo datas e acontecimentos de um texto.
Extraindo de Dados de Textos
Vamos supor que temos o seguinte texto e queremos extrair as datas e os acontecimentos mencionados.
Aqui temos um texto que utilizarmos como exemplo:
texto = '''A Apple foi fundada em 1 de abril de 1976 por Steve Wozniak, Steve Jobs e Ronald
Wayne com o nome de Apple Computers, na Califórnia. O nome foi escolhido por Jobs após a
visita do pomar de maçãs da fazenda de Robert Friedland, também pelo fato do nome soar bem
e ficar antes da Atari
�→
�→
�→
nas listas telefônicas.
O primeiro protótipo da empresa foi o Apple I que foi demonstrado na Homebrew Computer Club em
1975, as vendas começaram em julho de 1976 com o preço de US$ 666,66, aproximadamente 200
unidades foram vendidas,[21] em 1977 a empresa conseguiu o aporte de Mike Markkula e um
empréstimo do Bank of America.'''
�→
�→
�→
Para extrair essas informações, vamos criar uma estrutura de dados que represente um acontecimento
com uma data e uma descrição:
from pydantic import BaseModel, Field
from typing import List
from langchain_core.utils.function_calling import convert_to_openai_function
class Acontecimento(BaseModel):
'''Informação sobre um acontecimento'''
data: str = Field(description='Data do acontecimento no formato YYYY-MM-DD')
acontecimento: str = Field(description='Acontecimento extraído do texto')
class ListaAcontecimentos(BaseModel):
"""Acontecimentos para extração"""
acontecimentos: List[Acontecimento] = Field(description='Lista de acontecimentos presentes
no texto informado')
�→
Asimov Academy
31


---
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