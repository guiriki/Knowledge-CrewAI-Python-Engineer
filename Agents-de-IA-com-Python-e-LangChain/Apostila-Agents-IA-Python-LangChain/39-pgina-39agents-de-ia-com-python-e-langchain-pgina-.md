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
## Página 40

Agents de IA com Python e LangChain
retorna_temperatura_atual.args
# {'localidade': {'title': 'Localidade', 'description': 'Localidade a ser buscada',
'examples': ['São Paulo', 'Porto Alegre'], 'type': 'string'}}
�→
Chamando a Tool
Depois de passar o decorador, a ferramenta ganha o método invoke, que permite chamá-la com os
argumentos necessários.
retorna_temperatura_atual.invoke({'localidade': 'Porto Alegre'})
# '25ºC'
Criando Tools com StructuredTool
Outra forma de criar uma ferramenta é utilizando a metaclasse StructuredTool do LangChain. As
funcionalidades são bem similares ao uso do decorador.
from langchain.tools import StructuredTool
from pydantic import BaseModel, Field
class RetornaTempArgs(BaseModel):
localidade: str = Field(description='Localidade a ser buscada', examples=['São Paulo',
'Porto Alegre'])
�→
def retorna_temperatura_atual(localidade: str):
return '25ºC'
tool_temp = StructuredTool.from_function(
func=retorna_temperatura_atual,
name='ToolTemperatura',
args_schema=RetornaTempArgs,
description='Faz busca online de temperatura de uma localidade',
return_direct=True
)
tool_temp
A StructuredTool criada possui todas as informações necessárias:
StructuredTool(name='ToolTemperatura', description='ToolTemperatura(localidade: str) - Faz
busca online de temperatura de uma localidade', args_schema=<class
'__main__.RetornaTempArgs'>, return_direct=True, func=<function retorna_temperatura_atual
at 0x000001EE79A29440>)
�→
�→
�→
Podemos acessar o nome, a descrição e os argumentos da ferramenta:
tool_temp.name
# 'ToolTemperatura'
tool_temp.args
Asimov Academy
39


---