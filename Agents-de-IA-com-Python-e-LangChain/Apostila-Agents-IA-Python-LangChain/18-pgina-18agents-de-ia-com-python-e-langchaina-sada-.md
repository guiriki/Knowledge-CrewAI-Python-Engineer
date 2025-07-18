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
## Página 19

Agents de IA com Python e LangChain
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
Conteúdo: Olá! Como posso ajudar você hoje?
Tools: None
Parâmetro “dicionário com a key function”
Podemos fazer o modelo rodar obrigatoriamente a função, passando dentro de um dicionário a função
que o modelo deve rodar.
mensagens = [
{'role': 'user', 'content': 'Qual é temperatura em Porto Alegre agora?'}
]
resposta = client.chat.completions.create(
model='gpt-3.5-turbo-0125',
messages=mensagens,
tools=tools,
tool_choice={'function': 'obter_temperatura_atual'}
)
mensagem = resposta.choices[0].message
print('Conteúdo:', mensagem.content)
print('Tools:', mensagem.tool_calls)
A saída será:
Conteúdo: None
Tools: [ChatCompletionMessageToolCall(id='call_PS1Nw8caOtDo9Q48ygEumxDa',
function=Function(arguments='{"local":"Porto Alegre"}', name='obter_temperatura_atual'),
type='function')]
�→
�→
E é isso, pessoal! Agora vocês sabem como adicionar funções externas à API da OpenAI e como isso
pode tornar seus modelos de linguagem muito mais poderosos e úteis.
Asimov Academy
18


---