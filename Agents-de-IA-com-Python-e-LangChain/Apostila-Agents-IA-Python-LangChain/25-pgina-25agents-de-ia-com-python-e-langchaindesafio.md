## Página 25

Agents de IA com Python e LangChain
Desafio - Criando uma Função para Obter Emails
Após este conteúdo sobre adição de funções, quero propor um desafio para vocês! Em vez de criar uma
função para obter a temperatura, que tal desenvolver uma função para obter emails? Essa é uma ótima
oportunidade para vocês praticarem e consolidar suas habilidades! ### O que você precisa fazer?
Crie uma função chamada obter_emails que tenha os seguintes parâmetros:
• tipo: um argumento que define o tipo de emails a serem obtidos. Os valores possíveis são:
– 'todos': para obter todos os emails.
– 'não lidos': para obter apenas os emails que ainda não foram lidos.
– 'lidos': para obter apenas os emails que já foram lidos.
• quantidade: um argumento que define quantos emails você deseja obter.
Essa função será o primeiro passo para criar um assistente pessoal que possa ler e responder aos
nossos emails. Pense em como você pode estruturar a função e quais dados ela deve retornar. ###
Lembre-se!
Nós vimos anteriormente como obter a temperatura atual utilizando LangChain e Pydantic. O processo
envolveu a definição de uma classe de dados com Pydantic e a criação de uma função que poderia ser
chamada pelo modelo. Aqui estão alguns trechos de código que utilizamos:
from pydantic import BaseModel, Field
from typing import Optional
from enum import Enum
from langchain_core.utils.function_calling import convert_to_openai_function
class UnidadeEnum(str, Enum):
celsius = 'celsius'
fahrenheit = 'fahrenheit'
class ObterTemperaturaAtual(BaseModel):
"""Obtém a temperatura atual de uma determinada localidade"""
local: str = Field(description='O nome da cidade', examples=['São Paulo', 'Porto Alegre'])
unidade: Optional[UnidadeEnum]
tool_temperatura = convert_to_openai_function(ObterTemperaturaAtual)
tool_temperatura
Agora, aplique esse conhecimento para criar sua função de obter emails!
Asimov Academy
24


---
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