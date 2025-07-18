## Página 9

Agents de IA com Python e LangChain
Agora, vamos compor nossa chain. A beleza da LCEL está na simplicidade com que podemos encadear
diferentes componentes:
chain = prompt | model
Para invocar a chain com um exemplo prático, vamos usar:
response = chain.invoke({'assunto': 'gatinhos'})
print(response)
AIMessage(content='Os gatinhos são seres adoráveis que conseguem conquistar nossos corações
com seu charme e fofura.', response_metadata={'token_usage': {'completion_tokens': 28,
'prompt_tokens': 19, 'total_tokens': 47}, 'model_name': 'gpt-3.5-turbo-0125',
'system_fingerprint': None, 'finish_reason': 'stop', 'logprobs': None},
id='run-b9e445f5-5ba9-4aea-9813-eda76880def5-0')
�→
�→
�→
�→
Adicionando mais elementos à chain
Suponha que queremos apenas o texto da resposta, sem metadados adicionais. Podemos adicionar
um output_parser à nossa chain:
from langchain_core.output_parsers import StrOutputParser
output_parser = StrOutputParser()
chain = prompt | model | output_parser
print(chain.invoke({'assunto': 'gatinhos'}))
'"Gatinhos são fofos, brincalhões e cheios de amor para dar."'
E veja como é simples ir compondo nossa chain e adicionando novos elementos. Pense que após esta
chain, poderíamos adicionar um novo prompt que pega a resposta produzida após o output parser e
processa ele novamente, para gerar uma nova resposta e assim por diante.
Atenção: A ordem importa!
É crucial que os componentes da chain sejam organizados na ordem correta para que os dados fluam
corretamente de um estágio para o outro. Por exemplo, inverter a ordem resultará em erro, pois cada
componente espera um tipo específico de entrada.
chain = model | prompt | output_parser #ORDEM INCORRETA!
chain.invoke({'assunto': 'gatinhos'}) #Invoke retornará um erro
Entendendo a ordem correta
Para garantir que você não cometa erros, é importante entender o tipo de entrada e saída de cada
componente:
Asimov Academy
8


---
## Página 10

Agents de IA com Python e LangChain
• Prompt: Recebe um dicionário e retorna um PromptValue.
• Model (ChatModel): Recebe uma string, uma lista de mensagens de chat ou um PromptValue
e retorna uma ChatMessage.
• OutputParser: Recebe a saída de um LLM ou ChatModel e retorna um tipo de dado específico,
dependendo do parser.
Este é um esquema geral dos principais componentes do LangChain e os tipos de entada e saída que
eles suportam:
Component
Tipo de Entrada
Tipo de Saída
Prompt
Dicionário
PromptValue
ChatModel
String única, lista de mensagens de chat ou
PromptValue
Mensagem de Chat
LLM
String única, lista de mensagens de chat ou
PromptValue
String
OutputParser
A saída de um LLM ou ChatModel
Depende do parser
Retriever
String única
Lista de Documentos
Tool
String única ou dicionário, dependendo da ferramenta
Depende da
ferramenta
Você pode também verificar os tipos de entrada e saída utilizando os métodos input_schema e out-
put_schema:
print(prompt.input_schema.schema_json(indent=4))
{
"title": "PromptInput",
"type": "object",
"properties": {
"assunto": {
"title": "Assunto",
"type": "string"
}
}
}
Chains Clássicas vs. LCEL
Antes da LCEL, criar chains era mais complexo e menos intuitivo. Veja como seria com a abordagem
clássica:
Asimov Academy
9


---