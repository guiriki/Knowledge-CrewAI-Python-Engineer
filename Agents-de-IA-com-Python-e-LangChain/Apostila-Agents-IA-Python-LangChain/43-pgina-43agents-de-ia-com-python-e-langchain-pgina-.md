## Página 43

Agents de IA com Python e LangChain
# Fazendo a requisição para a API
resposta = requests.get(URL, params=params)
if resposta.status_code == 200:
resultado = resposta.json()
# Obtendo a hora atual em UTC
hora_agora = datetime.datetime.now(datetime.UTC).replace(tzinfo=None)
# Convertendo a lista de horas para o formato datetime
lista_horas = [datetime.datetime.fromisoformat(temp_str) for temp_str in
resultado['hourly']['time']]
�→
# Encontrando o índice da hora mais próxima
index_mais_prox = min(range(len(lista_horas)), key=lambda x: abs(lista_horas[x] -
hora_agora))
�→
# Obtendo a temperatura atual
temp_atual = resultado['hourly']['temperature_2m'][index_mais_prox]
print(temp_atual)
else:
raise Exception(f'Request para API {URL} falhou: {resposta.status_code}')
Encapsulando em uma Função
Agora que temos o código básico funcionando, vamos encapsulá-lo em uma função para facilitar o uso
e utilizar o decorator @tool para gerar uma ferramenta, adicionando um ArgsSchema para definir os
argumentos:
from langchain.agents import tool
from pydantic import BaseModel, Field
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
Asimov Academy
42


---
## Página 44

Agents de IA com Python e LangChain
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
Testando a Tool
Vamos testar a função retorna_temperatura_atual para garantir que está funcionando corre-
tamente.
retorna_temperatura_atual.invoke({'latitude': -30, 'longitude': -50})
20.3
Criando uma Tool de Busca no Wikipedia
Agora, vamos criar uma ferramenta que faz buscas no Wikipedia e retorna resumos das páginas
encontradas. Para isso, utilizaremos a biblioteca wikipedia.
Passo a Passo para Criar a Função de Busca no Wikipedia
Primeiro, vamos configurar a biblioteca wikipedia para utilizar o idioma português e, em seguida,
criar a função de busca. Vamos encapsular o código em uma função para facilitar o uso e já o utilizar o
decorator tool para gerar uma ferramenta:
from langchain.agents import tool
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
Asimov Academy
43


---