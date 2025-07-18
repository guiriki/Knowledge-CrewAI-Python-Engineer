## Página 42

Agents de IA com Python e LangChain
08. Processo Completo para Criação de Tool de Temperatura e do
Wikipedia
Olá, pessoal! Bem-vindos a mais um capítulo do nosso curso. Hoje, vamos colocar a mão na massa e
criar duas ferramentas (ou “tools”) reais e funcionais: uma para buscar a temperatura atual de uma
localidade específica e outra para fazer buscas no Wikipedia. Essas ferramentas são ótimos exemplos
de como podemos integrar APIs externas e bibliotecas em nossos projetos de IA. Nossos objetivos,
portanto, serão:
• Entender como criar uma tool de busca de temperatura utilizando a API da OpenMeteo.
• Aprender a criar uma tool de busca no Wikipedia utilizando a biblioteca wikipedia.
• Testar as tools para garantir que estão funcionando corretamente.
• Integrar essas tools em uma chain utilizando LangChain.
No mundo da programação, especialmente quando estamos lidando com agentes de IA, é essencial
saber como integrar diferentes APIs e bibliotecas para ampliar as capacidades dos nossos modelos.
Hoje, vamos ver como fazer isso de forma prática e direta, criando ferramentas que podem ser usadas
em diversos contextos.
Criando uma Tool de Busca de Temperatura
Vamos começar com a criação de uma ferramenta que busca a temperatura atual de uma localidade
específica utilizando a API da OpenMeteo.
Passo a Passo para Criar a Função de Temperatura
Primeiro, vamos criar uma função que acessa a API da OpenMeteo e retorna a temperatura de um local.
Aqui está o código básico:
import requests
import datetime
# URL da API
URL = 'https://api.open-meteo.com/v1/forecast'
# Parâmetros da API
params = {
'latitude': -30,
# Latitude de Porto Alegre
'longitude': -50,
# Longitude de Porto Alegre
'hourly': 'temperature_2m',
'forecast_days': 1,
}
Asimov Academy
41


---
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