## Página 24

Agents de IA com Python e LangChain
Criando um Novo Componente de chat_model
Também é possível vincular essa ferramenta indefinidamente a um chat_model utilizando o método
bind:
chat_com_func = chat.bind(functions=[tool_temperatura])
resposta = chat_com_func.invoke('Qual é a temperatura de Porto Alegre')
print(resposta)
Agora todas as próximas vezes que a instância chat_com_func for chamada, ela terá acesso a ferra-
menta.
Forçando o Modelo a Chamar uma Função
Da mesma forma que utilizando diretamente a biblioteca da OpenAI podemos forçar o modelo a
chamar a função, podemos fazê-lo com LangChain da seguinte forma:
resposta = chat.invoke(
'Qual é a temperatura de Porto Alegre',
functions=[tool_temperatura],
function_call={'name': 'ObterTemperaturaAtual'}
)
print(resposta)
Quando não passamos o parâmetro function_call, o modelo estará decidindo automaticamente a
necessidade de rodar a função (estará utilizando o “auto”, como visto no capítulo anterior).
Adicionando a uma Chain
Podemos adicionar agora este modelo com funções a um prompt e criar uma chain.
from langchain.prompts import ChatPromptTemplate
prompt = ChatPromptTemplate.from_messages([
('system', 'Você é um assistente amigável chamado Isaac'),
('user', '{input}')
])
chain = prompt | chat.bind(functions=[tool_temperatura])
resposta = chain.invoke({'input': 'Olá'})
print(resposta)
E é isso, pessoal! Hoje aprendemos como adicionar funções externas utilizando o LangChain e a
biblioteca Pydantic para validação de dados. O framework LangChain se mostrou novamente uma
grande arma para facilitar nosso trabalho ao criarmos aplicações com modelos de linguagem. Vamos
pro próximo capítulo, pois temos muito ainda a conhecer sobre nosso querido LangChain!
Asimov Academy
23


---
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