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
## Página 17

Agents de IA com Python e LangChain
messages=mensagens,
tools=tools,
tool_choice='auto'
)
resposta
A resposta será:
ChatCompletion(id='chatcmpl-9S4IXDcfVOj869V1pS1fzXBToOrPy', choices=[Choice(fini
E finalmente, podemos extrair a resposta final.
resposta.choices[0].message.content
A saída será:
'A temperatura em Porto Alegre agora é de 25°C.'
E assim criamos um loop onde o modelo não havia capacidade por si só de dar uma resposta a
pergunta. Mas ao ter acesso a uma ferramenta externa, ele pode solicitar a execução desta ferramenta
com parâmetros definidos por e ele e a partir da observação gerada, devolver uma resposta correta ao
usuário.
Explorando Diferentes Perguntas e o Parâmetro tool_choice
Por fim, vamos explorar como o parâmetro tool_choice afeta o comportamento do modelo. Esse
parâmetro pode ser auto, none ou um dicionário com a key function.
Parâmetro “auto”
O parâmetro “auto” permite ao modelo definir automaticamente se é necessária a utilização de uma
função ou não.
mensagens = [
{'role': 'user', 'content': 'Qual é temperatura em Porto Alegre agora?'}
]
resposta = client.chat.completions.create(
model='gpt-3.5-turbo-0125',
messages=mensagens,
tools=tools,
tool_choice='auto'
)
mensagem = resposta.choices[0].message
print('Conteúdo:', mensagem.content)
print('Tools:', mensagem.tool_calls)
Asimov Academy
16


---