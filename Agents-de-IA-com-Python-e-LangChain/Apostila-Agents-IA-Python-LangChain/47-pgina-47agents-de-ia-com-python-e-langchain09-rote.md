## Página 47

Agents de IA com Python e LangChain
09. Roteamento para Execução Automática de Tools
Olá, pessoal! Bem-vindos a mais um capítulo da nossa apostila. Nós vamos abordar agora um tema
essencial para a construção de agentes inteligentes: o roteamento para execução automática de tools.
Isso permitirá que o seu modelo de IA utilize ferramentas específicas de forma automática. O passo
que estava faltando para criarmos nossa primeira estrutura de Agents. Nossos objetivos, portanto,
serão:
• Criar um roteamento: Desenvolver um sistema de roteamento que decide quando e como
executar uma ferramenta.
• Utilizar o OpenAIFunctionsAgentOutputParser: Entender como utilizar esse parser para pro-
cessar a saída do modelo.
Lembrando que na última aula, criamos duas ferramentas: uma para obter a temperatura atual de
uma localização específica e outra para buscar informações na Wikipedia. Agora, vamos dar um passo
adiante e integrar essas ferramentas ao nosso modelo de IA, criando um sistema de roteamento que
decide automaticamente quando e como executar essas ferramentas. Isso é crucial para construir
agentes inteligentes que podem interagir de forma mais eficaz e eficiente com os usuários.
Recriando as Tools
Vamos começar recriando as tools que desenvolvemos na última aula. Isso nos ajudará a refrescar a
memória e garantir que estamos todos na mesma página.
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
Asimov Academy
46


---
## Página 48

Agents de IA com Python e LangChain
'longitude': longitude,
'hourly': 'temperature_2m',
'forecast_days': 1,
}
resposta = requests.get(URL, params=params)
if resposta.status_code == 200:
resultado = resposta.json()
hora_agora = datetime.datetime.now(datetime.UTC).replace(tzinfo=None)
lista_horas = [datetime.datetime.fromisoformat(temp_str) for temp_str in
resultado['hourly']['time']]
�→
index_mais_prox = min(range(len(lista_horas)), key=lambda x: abs(lista_horas[x] -
hora_agora))
�→
temp_atual = resultado['hourly']['temperature_2m'][index_mais_prox]
return temp_atual
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
Integrando as Tools ao Modelo
Agora que recriamos nossas tools, vamos integrá-las ao nosso modelo de IA. Isso envolve criar uma
chain que combina o prompt, o modelo de chat e as tools.
from langchain.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
from langchain_core.utils.function_calling import convert_to_openai_function
prompt = ChatPromptTemplate.from_messages([
('system', 'Você é um assistente amigável chamado Isaac'),
('user', '{input}')
])
chat = ChatOpenAI()
tools = [busca_wikipedia, retorna_temperatura_atual]
Asimov Academy
47


---