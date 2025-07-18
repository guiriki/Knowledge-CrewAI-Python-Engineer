## Página 46

Agents de IA com Python e LangChain
AIMessage(content='Olá! Como posso ajudar você hoje?', response_metadata={'token_usage':
{'completion_tokens': 12, 'prompt_tokens': 148, 'total_tokens': 160}, 'model_name':
'gpt-3.5-turbo', 'system_fingerprint': None, 'finish_reason': 'stop', 'logprobs': None},
id='run-81757f8e-4e55-44e8-aac4-9f0f1d8aa09f-0')
�→
�→
�→
chain.invoke({'input': 'Qual é a temperatura de Porto Alegre?'})
AIMessage(content='', additional_kwargs={'function_call': {'arguments':
'{"latitude":-30.0346,"longitude":-51.2177}', 'name': 'retorna_temperatura_atual'}},
response_metadata={'token_usage': {'completion_tokens': 28, 'prompt_tokens': 156,
'total_tokens': 184}, 'model_name': 'gpt-3.5-turbo', 'system_fingerprint': None,
'finish_reason': 'function_call', 'logprobs': None},
id='run-962073d5-6bd1-4d75-86fc-40f9535288d8-0')
�→
�→
�→
�→
�→
chain.invoke({'input': 'Quem foi Isaac Asimov?'})
AIMessage(content='', additional_kwargs={'function_call': {'arguments': '{"query":"Isaac
Asimov"}', 'name': 'busca_wikipedia'}}, response_metadata={'token_usage':
{'completion_tokens': 20, 'prompt_tokens': 154, 'total_tokens': 174}, 'model_name':
'gpt-3.5-turbo', 'system_fingerprint': None, 'finish_reason': 'function_call', 'logprobs':
None}, id='run-1c6dd1a6-a47b-4c5d-887b-beca183fa0a9-0')
�→
�→
�→
�→
Na próxima aula, vamos ver de fato como rodar essas tools, adicionando-as em um loop de forma que
o modelo não só peça para rodar a ferramenta, mas também de fato a rode e obtenha a informação
necessária. Muito obrigado por terem ficado até aqui. Finalmente entreguei umas tools para vocês
que são úteis, né? Fazer uma busca no Wikipedia é legal, pegar a temperatura atual agora é legal, e
vocês vão ver que as ferramentas vão ficando cada vez mais legais. Espero que tenham gostado, nos
vemos no próximo capítulo.
Asimov Academy
45


---
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