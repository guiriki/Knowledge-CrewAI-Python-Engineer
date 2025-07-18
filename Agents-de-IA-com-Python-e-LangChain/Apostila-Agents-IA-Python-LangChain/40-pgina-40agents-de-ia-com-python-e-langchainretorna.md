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
## Página 41

Agents de IA com Python e LangChain
# {'localidade': {'title': 'Localidade', 'description': 'Localidade a ser buscada',
'examples': ['São Paulo', 'Porto Alegre'], 'type': 'string'}}
�→
tool_temp.description
# 'ToolTemperatura(localidade: str) - Faz busca online de temperatura de uma localidade'
E também podemos chamar a ferramenta:
tool_temp.invoke({'localidade': 'Porto Alegre'})
# '25ºC'
E é isso aí, pessoal! Agora vocês sabem como criar Tools utilizando o LangChain. Na próxima aula,
vamos criar ferramentas reais que buscam informações através de APIs, como a temperatura de uma
localidade e buscas no Wikipedia. As coisas estão começando a ficar cada vez mais reais, e logo
chegaremos aos Agents. Até o próximo capítulo!
Asimov Academy
40


---