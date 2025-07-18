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
## Página 45

Agents de IA com Python e LangChain
pass
if not resumos:
return 'Busca não teve retorno'
else:
return '\n\n'.join(resumos)
Testando a Tool
Vamos testar a função busca_wikipedia para garantir que está funcionando corretamente.
busca_wikipedia.invoke({'query': 'futebol'})
'Título da página: Futebol\nResumo: O futebol, também referido como futebol de c
...
Integrando as Tools em uma Chain
Vamos agora integrar essas tools em uma chain para que possamos utilizá-las em conjunto com um
modelo de linguagem, como o OpenAI.
Configurando a Chain
from langchain.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
from langchain_core.utils.function_calling import convert_to_openai_function
prompt = ChatPromptTemplate.from_messages([
('system', 'Você é um assistente amigável chamado Isaac'),
('user', '{input}')
])
chat = ChatOpenAI()
tools = [convert_to_openai_function(busca_wikipedia),
convert_to_openai_function(retorna_temperatura_atual)]
�→
chain = prompt | chat.bind(functions=tools)
Testando a Chain
Vamos testar nossa chain para garantir que ela está funcionando corretamente.
chain.invoke({'input': 'Olá'})
Asimov Academy
44


---