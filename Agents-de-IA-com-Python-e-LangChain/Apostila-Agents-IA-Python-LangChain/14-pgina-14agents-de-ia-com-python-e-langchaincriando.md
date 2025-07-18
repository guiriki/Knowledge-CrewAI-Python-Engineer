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
## Página 15

Agents de IA com Python e LangChain
"type": "string",
"enum": ["celsius", "fahrenheit"]
},
},
"required": ["local"],
},
},
}
]
Chamando o Modelo com a Nova Ferramenta
Vamos agora fazer uma pergunta ao modelo e ver como ele utiliza a função que adicionamos.
mensagens = [
{'role': 'user', 'content': 'Qual é temperatura em Porto Alegre agora?'}
]
resposta = client.chat.completions.create(
model='gpt-3.5-turbo-0125',
messages=mensagens,
tools=tools,
tool_choice='auto'
)
resposta
A resposta será algo como:
ChatCompletion(id='chatcmpl-9S4Dz4a8Om4R33B0IGUIUzDI3Dtcb',
choices=[Choice(finish_reason='tool_calls', index=0, logprobs=None,
message=ChatCompletionMessage(content=None, role='assistant', function_call=None,
tool_calls=[ChatCompletionMessageToolCall(id='call_yOuegMyCjHRpZXkYkWFMmrUL',
function=Function(arguments='{"local":"Porto Alegre"}', name='obter_temperatura_atual'),
type='function')]))], created=1716476451, model='gpt-3.5-turbo-0125',
object='chat.completion', system_fingerprint=None,
usage=CompletionUsage(completion_tokens=22, prompt_tokens=87, total_tokens=109))
�→
�→
�→
�→
�→
�→
�→
Podemos perceber que o conteúdo da resposta veio vazio, pois para a pergunta “Qual é a temperatura
em Porto Alegre?” ele necessitará chamar a função antes.
mensagem = resposta.choices[0].message
mensagem
Você pode perceber que a variável content da mensagem está vazia (None), mostrando que o modelo
ainda não foi capaz de gerar uma resposta.
ChatCompletionMessage(content=None, role='assistant', function_call=None,
tool_calls=[ChatCompletionMessageToolCall(id='call_yOuegMyCjHRpZXkYkWFMmrUL',
function=Function(arguments='{"local":"Porto Alegre"}', name='obter_temperatura_atual'),
type='function')])
�→
�→
�→
Vamos extrair o nome da função e os argumentos que o modelo quer utilizar.
Asimov Academy
14


---