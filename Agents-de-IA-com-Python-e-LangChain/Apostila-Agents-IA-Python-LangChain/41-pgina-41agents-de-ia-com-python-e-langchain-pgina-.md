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