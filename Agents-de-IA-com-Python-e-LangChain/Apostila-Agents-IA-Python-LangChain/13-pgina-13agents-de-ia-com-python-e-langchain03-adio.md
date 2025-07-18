## Página 13

Agents de IA com Python e LangChain
03. Adição de Funções Externas à API da OpenAI
Bem-vindos a mais um capítulo da nossa apostila! Agora vamos explorar um tópico super interessante
e essencial para quem quer criar agentes de IA poderosos e versáteis: a adição de funções externas à API
da OpenAI. Vamos entender como essa capacidade pode transformar nossos modelos de linguagem
em ferramentas ainda mais úteis e inteligentes.
Neste capítulo, nosso objetivo é aprender como adicionar funções externas à API da OpenAI. Vamos
ver como isso permite que nossos modelos de linguagem realizem ações no mundo real e obtenham
informações atualizadas, superando uma das principais limitações dos modelos de linguagem: o fato
de serem treinados em dados antigos.
Por que adicionar ferramentas externas é relevante?
Os modelos de linguagem, como o GPT-3, são treinados em grandes quantidades de dados, mas esses
dados têm um limite temporal. Por exemplo, o GPT-3 foi treinado com dados até 2023. Isso significa que
ele não tem informações sobre eventos que ocorreram depois disso. Para criar aplicações realmente
úteis e interativas, precisamos que nossos modelos possam agir no mundo real e obter informações
atualizadas. É aí que entra a adição de funções externas.
A OpenAI foi pioneira em criar modelos que interpretam funções externas, permitindo que frameworks
como o LangChain integrem essas capacidades. Vamos começar revisando como adicionar funções
diretamente na API da OpenAI, para depois compararmos com a facilidade que o LangChain nos
proporciona.
Importações Iniciais
Primeiro, vamos configurar nosso ambiente e importar as bibliotecas necessárias. Vamos utilizar a
biblioteca da OpenAI e algumas outras para facilitar nosso trabalho.
import json
import openai
from dotenv import load_dotenv, find_dotenv
_ = load_dotenv(find_dotenv())
client = openai.Client()
Asimov Academy
12


---
## Página 14

Agents de IA com Python e LangChain
Criando a Função que Será Adicionada ao Modelo
Para adicionar uma função ao modelo, precisamos primeiro definir essa função. Vamos criar uma
função simples que retorna a temperatura atual de uma localidade. No nosso exemplo, a função é
hardcoded (ou seja, é fictícia e retorna sempre os mesmos valores), mas em um cenário real, você
poderia integrar uma API de clima.
def obter_temperatura_atual(local, unidade="celsius"):
if "são paulo" in local.lower():
return json.dumps(
{"local": "São Paulo", "temperatura": "32", "unidade": unidade}
)
elif "porto alegre" in local.lower():
return json.dumps(
{"local": "Porto Alegre", "temperatura": "25", "unidade": unidade}
)
else:
return json.dumps(
{"local": local, "temperatura": "unknown"}
)
Vamos testar nossa função para ver se ela está funcionando corretamente.
obter_temperatura_atual('Porto Alegre')
A saída será:
'{"local": "Porto Alegre", "temperatura": "25", "unidade": "celsius"}'
Criando a Descrição da Função
Agora que temos nossa função, precisamos criar um dicionário que descreva essa função para o modelo
de linguagem. Esse dicionário deve ser bem detalhado para que o modelo entenda como e quando
usar a função.
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
Asimov Academy
13


---