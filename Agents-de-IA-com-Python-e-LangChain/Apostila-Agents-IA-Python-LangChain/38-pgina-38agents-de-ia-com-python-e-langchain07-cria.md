## Página 38

Agents de IA com Python e LangChain
07. Criação de Tools com LangChain
Olá, pessoal! Bem-vindos a mais um capítulo da nossa apostila. Hoje, vamos nos aprofundar em um
dos aspectos mais essenciais para a construção de agentes inteligentes: as Tools (ferramentas). As
ferramentas são o que realmente diferenciam um Agent, permitindo que ele interaja com o mundo de
maneira mais eficiente e eficaz. Nosso objetivo agora será:
• Entender o que são Tools e sua importância para os Agents.
• Aprender a criar Tools utilizando o decorador @tool.
• Explorar a criação de Tools com a metaclasse StructuredTool.
• Compreender como descrever argumentos de forma clara e precisa.
• Ver exemplos práticos de como chamar e utilizar essas Tools.
O que são tools?
As tools (ferramentas) são componentes essenciais no ecossistema do LangChain, permitindo que
agentes, cadeias ou modelos de linguagem (LLMs) interajam com o mundo externo. Elas funcionam
como interfaces que possibilitam a execução de ações específicas, facilitando a integração de fun-
cionalidades externas nas aplicações de IA.
Como as Tools se Relacionam com Modelos de Linguagem
As tools são especialmente poderosas quando combinadas com as capacidades de tool calling dos
modelos de linguagem. Isso significa que, ao invés de apenas gerar texto, os LLMs podem agora
chamar funções externas para realizar ações específicas, como buscar informações, processar dados
ou interagir com APIs.
Por exemplo, ao criar uma tool que retorna a temperatura atual de uma localidade, o modelo de
linguagem pode ser instruído a chamar essa função quando um usuário faz uma pergunta sobre o
clima. Isso não só enriquece a interação, mas também permite que o modelo forneça respostas mais
precisas e contextuais.
Criando Tools com o Decorador @tool
Vamos começar criando uma ferramenta utilizando o decorador @tool. O decorador @tool modifica
uma função, permitindo que ela seja usada como uma ferramenta pelo LangChain.
from langchain.agents import tool
Asimov Academy
37


---
## Página 39

Agents de IA com Python e LangChain
@tool
def retorna_temperatura_atual(localidade: str):
'''Faz busca online de temperatura de uma localidade'''
return '25ºC'
retorna_temperatura_atual
Quando executamos o código acima, obtemos uma StructuredTool com todas as informações
necessárias:
StructuredTool(name='retorna_temperatura_atual',
description='retorna_temperatura_atual(localidade: str) - Faz busca online de temperatura
de uma localidade', args_schema=<class
'pydantic.v1.main.retorna_temperatura_atualSchema'>, func=<function
retorna_temperatura_atual at 0x000001EE78100D60>)
�→
�→
�→
�→
Podemos acessar o nome, a descrição e os argumentos da ferramenta:
retorna_temperatura_atual.name
# 'retorna_temperatura_atual'
retorna_temperatura_atual.description
# 'retorna_temperatura_atual(localidade: str) - Faz busca online de temperatura de uma
localidade'
�→
retorna_temperatura_atual.args
# {'localidade': {'title': 'Localidade', 'type': 'string'}}
Descrevendo os Argumentos
Para garantir que a ferramenta seja utilizada corretamente, é importante descrever melhor os argu-
mentos. Vamos usar a biblioteca pydantic para isso.
from langchain.agents import tool
from pydantic import BaseModel, Field
class RetornaTempArgs(BaseModel):
localidade: str = Field(description='Localidade a ser buscada', examples=['São Paulo',
'Porto Alegre'])
�→
@tool(args_schema=RetornaTempArgs)
def retorna_temperatura_atual(localidade: str):
'''Faz busca online de temperatura de uma localidade'''
return '25ºC'
retorna_temperatura_atual
Agora, a descrição dos argumentos é mais detalhada, o que aumenta as chances do modelo entender
como utilizar bem a ferramenta.
Asimov Academy
38


---