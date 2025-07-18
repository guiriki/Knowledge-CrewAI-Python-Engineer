## Página 26

Agents de IA com Python e LangChain
05. Tagging - Categorização de Texto Utilizando Funções
Bem-vindos de volta a nossa apostila! No último capítulo, aprendemos como adicionar funções
aos modelos utilizando o framework LangChain. Hoje, vamos explorar uma aplicação prática desse
conhecimento: a categorização de texto, ou “tagging”. Nosso objetivo será:
• Entender o conceito de tagging e sua importância.
• Aprender a criar uma função para análise de sentimento e detecção de língua.
• Implementar um modelo para direcionamento de mensagens para setores específicos.
• Melhorar a precisão do modelo utilizando técnicas de engenharia de prompt.
Por que é importante categorizar textos?
A maior parte da informação disponível hoje está na internet no formato de texto, dentro de websites.
Isso pode ser um desafio para analistas de dados, pois esses dados não estão estruturados, ou seja, se
apresentam das mais diferentes formas que você possa imaginar. Sorte a nossa que temos modelos
de linguagem, pois eles tem uma capacidade incrível para processar esses dados e estruturá-los,
possibilitando uma análise em larga escala e de forma eficiente. Tagging é um conceito que auxilia
nessa estruturação de dados, transformando dados não estruturados em dados estruturados.
Tagging para Análise de Sentimento e Detecção de Língua
Vamos começar criando uma função que vai extrair o sentimento de uma mensagem (positivo, negativo
ou indefinido) e também identificar a língua do texto.
from pydantic import BaseModel, Field
from langchain_core.utils.function_calling import convert_to_openai_function
class Sentimento(BaseModel):
'''Define o sentimento e a língua da mensagem enviada'''
sentimento: str = Field(description='Sentimento do texto. Deve ser "pos", "neg" ou "nd"
para não definido.')
�→
lingua: str = Field(description='Língua que o texto foi escrito (deve estar no formato ISO
639-1)')
�→
tool_sentimento = convert_to_openai_function(Sentimento)
tool_sentimento
{'name': 'Sentimento',
'description': 'Define o sentimento e a língua da mensagem enviada',
'parameters': {'type': 'object',
'properties': {'sentimento': {'description': 'Sentimento do texto. Deve ser "pos", "neg" ou
"nd" para não definido.',
�→
'type': 'string'},
Asimov Academy
25


---
## Página 27

Agents de IA com Python e LangChain
'lingua': {'description': 'Língua que o texto foi escrito (deve estar no formato ISO
639-1)',
�→
'type': 'string'}},
'required': ['sentimento', 'lingua']}}
Vamos testar com um texto de exemplo:
texto = 'Eu gosto muito de massa aos quatro queijos'
Agora, vamos configurar o prompt e o modelo de chat:
from langchain.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
prompt = ChatPromptTemplate.from_messages([
('system', 'Pense com cuidado ao categorizar o texto conforme as instruções'),
('user', '{input}')
])
chat = ChatOpenAI()
chain = prompt | chat.bind(functions=[tool_sentimento], function_call={'name': 'Sentimento'})
Vamos invocar a chain com o nosso texto:
chain.invoke({'input': 'Eu gosto muito de massa aos quatro queijos'})
AIMessage(content='', additional_kwargs={'function_call': {'arguments':
'{"sentimento":"pos","lingua":"pt"}', 'name': 'Sentimento'}},
response_metadata={'token_usage': {'completion_tokens': 11, 'prompt_tokens': 145,
'total_tokens': 156}, 'model_name': 'gpt-3.5-turbo', 'system_fingerprint': None,
'finish_reason': 'stop', 'logprobs': None},
id='run-e68e3dfc-105c-4cc9-9a2a-f08e9c359f67-0')
�→
�→
�→
�→
�→
Vamos testar com outro texto:
chain.invoke({'input': 'I dont like this food'})
AIMessage(content='', additional_kwargs={'function_call': {'arguments':
'{"sentimento":"neg","lingua":"en"}', 'name': 'Sentimento'}},
response_metadata={'token_usage': {'completion_tokens': 11, 'prompt_tokens': 138,
'total_tokens': 149}, 'model_name': 'gpt-3.5-turbo', 'system_fingerprint': None,
'finish_reason': 'stop', 'logprobs': None},
id='run-101f6bd8-b4b9-4e49-b076-f18619b06d14-0')
�→
�→
�→
�→
�→
Parseando a Saída para Obtermos Apenas o que Interessa
Podemos utilizar o JsonOutputFunctionsParser para obtermos como resultado final da nossa
chain apenas o que nos interessa, que é o dicionário com as tags do conteúdo.
from langchain.output_parsers.openai_functions import JsonOutputFunctionsParser
chain = (prompt
| chat.bind(functions=[tool_sentimento], function_call={'name': 'Sentimento'})
Asimov Academy
26


---