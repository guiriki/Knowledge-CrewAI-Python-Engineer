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
## Página 18

Agents de IA com Python e LangChain
A saída será:
Conteúdo: None
Tools: [ChatCompletionMessageToolCall(id='call_PS1Nw8caOtDo9Q48ygEumxDa', functi
mensagens = [
{'role': 'user', 'content': 'Olá'}
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
A saída será:
Conteúdo: Olá! Como posso ajudar você hoje?
Tools: None
Parâmetro “none”
Com o parâmetro “none”, o modelo não vai utilizar funções.
mensagens = [
{'role': 'user', 'content': 'Qual a temperatura em Porto Alegre?'}
]
resposta = client.chat.completions.create(
model='gpt-3.5-turbo-0125',
messages=mensagens,
tools=tools,
tool_choice='none'
)
mensagem = resposta.choices[0].message
print('Conteúdo:', mensagem.content)
print('Tools:', mensagem.tool_calls)
A saída será:
Conteúdo: Por favor, aguarde um momento enquanto verifico a temperatura atual em Porto Alegre.
Tools: None
mensagens = [
{'role': 'user', 'content': 'Olá'}
Asimov Academy
17


---