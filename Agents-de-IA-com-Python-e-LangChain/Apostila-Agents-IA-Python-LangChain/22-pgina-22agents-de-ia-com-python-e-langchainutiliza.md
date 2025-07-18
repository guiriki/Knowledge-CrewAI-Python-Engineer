## Página 22

Agents de IA com Python e LangChain
Utilizando Pydantic para Criação de Tools da OpenAI
Lembram que para criarmos uma função de temperatura atual que a API da OpenAI reconece precisá-
vamos criar um dicionário cheio de argumentos, que facilmente poderia nos confundir:
import json
def obter_temperatura_atual(local, unidade="celsius"):
if "são paulo" in local.lower():
return json.dumps({"local": "São Paulo", "temperatura": "32", "unidade": unidade})
elif "porto alegre" in local.lower():
return json.dumps({"local": "Porto Alegre", "temperatura": "25", "unidade": unidade})
else:
return json.dumps({"local": local, "temperatura": "unknown"})
tools = [
{
"type": "function",
"function": {
"name": "obter_temperatura_atual",
"description": "Obtém a temperatura atual em uma dada cidade",
"parameters": {
"type": "object",
"properties": {
"local": {
"type": "string",
"description": "O nome da cidade. Ex: São Paulo",
},
"unidade": {
"type": "string",
"enum": ["celsius", "fahrenheit"]
},
},
"required": ["local"],
},
},
}
]
Utilizando Pydantic para Criar a Tool
Vamos agora utilizar Pydantic para criar a mesma função, mas de uma forma mais robusta e com
validação de dados.
from pydantic import BaseModel, Field
from typing import Optional
from enum import Enum
class UnidadeEnum(str, Enum):
celsius = 'celsius'
fahrenheit = 'fahrenheit'
Asimov Academy
21


---
## Página 23

Agents de IA com Python e LangChain
class ObterTemperaturaAtual(BaseModel):
"""Obtém a temperatura atual de uma determinada localidade"""
local: str = Field(description='O nome da cidade', examples=['São Paulo', 'Porto Alegre'])
unidade: Optional[UnidadeEnum]
Convertendo para uma Função da OpenAI
Agora vamos converter essa classe para uma função que a API da OpenAI consiga entender.
from langchain_core.utils.function_calling import convert_to_openai_function
tool_temperatura = convert_to_openai_function(ObterTemperaturaAtual)
print(tool_temperatura)
E obtemos o seguinte dicionário descrevendo a ferramenta:
{'name': 'ObterTemperaturaAtual',
'description': 'Obtém a temperatura atual de uma determinada localidade',
'parameters': {'type': 'object',
'properties': {'local': {'description': 'O nome da cidade',
'examples': ['São Paulo', 'Porto Alegre'],
'type': 'string'},
'unidade': {'description': 'An enumeration.',
'enum': ['celsius', 'fahrenheit'],
'type': 'string'}},
'required': ['local']}}
Adicionando Função Externa Utilizando LangChain
Agora que já sabemos criar funções que os modelos de LLM entendam, podemos passar essas funções
para os modelos de linguagem através da biblioteca LangChain.
Utilizando o Parâmetro functions
O parâmetro functions permite a adição de ferramentas externas aos chat_models do LangChain:
from langchain_openai import ChatOpenAI
chat = ChatOpenAI()
resposta = chat.invoke('Qual é a temperatura de Porto Alegre', functions=[tool_temperatura])
print(resposta)
Asimov Academy
22


---