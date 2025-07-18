## Página 62

Agents de IA com Python e LangChain
que ajudam a obter observações ou informações necessárias para completar subtarefas e satisfazer a
solicitação do usuário.
Construindo um Agent
A ideia central dos Agents é usar um modelo de linguagem para escolher uma sequência de ações a
serem executadas. Nas chains, uma sequência de ações é definida diretamente no código, ou seja,
recebe uma input do usuário, depois faz um parsing da output, depois passa para outra chain, utiliza
uma ferramenta, etc. Tudo é pré-definido por quem desenvolveu a chain. Já nos Agents, um modelo
de linguagem é usado como um motor de raciocínio para determinar quais ações devem ser
tomadas e em qual ordem.
Criando as Tools que Usaremos
Vamos começar criando as Tools que nossos Agents utilizarão. Essas Tools são funções que o modelo
de linguagem pode chamar para obter informações ou realizar ações específicas.
import requests
import datetime
from langchain.agents import tool
from pydantic import BaseModel, Field
import wikipedia
wikipedia.set_lang('pt')
class RetornTempArgs(BaseModel):
latitude: float = Field(description='Latitude da localidade que buscamos a temperatura')
longitude: float = Field(description='Longitude da localidade que buscamos a temperatura')
@tool(args_schema=RetornTempArgs)
def retorna_temperatura_atual(latitude: float, longitude: float):
'''Retorna a temperatura atual para uma dada coordenada'''
URL = 'https://api.open-meteo.com/v1/forecast'
params = {
'latitude': latitude,
'longitude': longitude,
'hourly': 'temperature_2m',
'forecast_days': 1,
}
resposta = requests.get(URL, params=params)
if resposta.status_code == 200:
resultado = resposta.json()
Asimov Academy
61


---
## Página 63

Agents de IA com Python e LangChain
hora_agora = datetime.datetime.now(datetime.UTC).replace(tzinfo=None)
lista_horas = [datetime.datetime.fromisoformat(temp_str) for temp_str in
resultado['hourly']['time']]
�→
index_mais_prox = min(range(len(lista_horas)), key=lambda x: abs(lista_horas[x] -
hora_agora))
�→
temp_atual = resultado['hourly']['temperature_2m'][index_mais_prox]
return f'{temp_atual}ºC'
else:
raise Exception(f'Request para API {URL} falhou: {resposta.status_code}')
@tool
def busca_wikipedia(query: str):
"""Faz busca no wikipedia e retorna resumos de páginas para a query"""
titulos_paginas = wikipedia.search(query)
resumos = []
for titulo in titulos_paginas[:3]:
try:
wiki_page = wikipedia.page(title=titulo, auto_suggest=True)
resumos.append(f'Título da página: {titulo}\nResumo: {wiki_page.summary}')
except:
pass
if not resumos:
return 'Busca não teve retorno'
else:
return '\n\n'.join(resumos)
Revisando a Utilização das Tools
Vamos revisar a utilização das Tools que acabamos de criar. Primeiro, configuramos o prompt e o
modelo de linguagem.
from langchain.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
from langchain_core.utils.function_calling import convert_to_openai_function
prompt = ChatPromptTemplate.from_messages([
('system', 'Você é um assistente amigável chamado Isaac'),
('user', '{input}')
])
chat = ChatOpenAI()
tools = [busca_wikipedia, retorna_temperatura_atual]
tools_json = [convert_to_openai_function(tool) for tool in tools]
tool_run = {tool.name: tool for tool in tools}
chain = prompt | chat.bind(functions=tools_json)
Em seguida, adicionamos o OutputParser para interpretar as respostas do modelo.
from langchain.agents.output_parsers import OpenAIFunctionsAgentOutputParser
Asimov Academy
62


---