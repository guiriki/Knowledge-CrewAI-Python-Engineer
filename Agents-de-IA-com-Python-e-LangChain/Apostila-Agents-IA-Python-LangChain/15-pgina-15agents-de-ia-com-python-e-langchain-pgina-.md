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
## Página 16

Agents de IA com Python e LangChain
tools_call = mensagem.tool_calls[0]
print(tools_call.function.name)
print(tools_call.function.arguments)
A saída será:
obter_temperatura_atual
{"local":"Porto Alegre"}
Adicionando Resultado da Função às Mensagens
Vamos agora rodar a função e adicionar o resultado às mensagens.
observacao = obter_temperatura_atual(**json.loads(tools_call.function.arguments))
observacao
A saída será:
'{"local": "Porto Alegre", "temperatura": "25", "unidade": "celsius"}'
Vamos adicionar essa observação às mensagens e chamar o modelo novamente.
mensagens.append(mensagem)
mensagens.append({
'tool_call_id': tools_call.id,
'role': 'tool',
'name': tools_call.function.name,
'content': observacao
})
mensagens
A lista de mensagens ficará assim:
[{'role': 'user', 'content': 'Qual é temperatura em Porto Alegre agora?'},
ChatCompletionMessage(content=None, role='assistant', function_call=None,
tool_calls=[ChatCompletionMessageToolCall(id='call_yOuegMyCjHRpZXkYkWFMmrUL',
function=Function(arguments='{"local":"Porto Alegre"}', name='obter_temperatura_atual'),
type='function')]),
�→
�→
�→
{'tool_call_id': 'call_yOuegMyCjHRpZXkYkWFMmrUL',
'role': 'tool',
'name': 'obter_temperatura_atual',
'content': '{"local": "Porto Alegre", "temperatura": "25", "unidade": "celsius"}'}]
Agora podemos chamar o modelo novamente.
resposta = client.chat.completions.create(
model='gpt-3.5-turbo-0125',
Asimov Academy
15


---