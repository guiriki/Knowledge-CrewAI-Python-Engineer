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
## Página 20

Agents de IA com Python e LangChain
04. Adição de Funções Externas Utilizando LangChain
Olá, pessoal! Bem-vindos de volta :)
Agora que entendemos como adicionar funções externas a modelos da OpenAI, vamos ver como o
LangChain nos auxilia a tornar esse processo muito mais fácil e intuitivo. Nosso objetivos, portanto,
serão:
• Aprender a usar a biblioteca Pydantic para validação de dados.
• Criar funções externas utilizando LangChain e Pydantic e integrá-las com a API da OpenAI.
• Utilizar o LangChain para adicionar essas funções aos nossos modelos de linguagem.
Introduzindo Pydantic
Como vimos no último capítulo, o trabalho de adicionar funções externas passa muito por saber-
mos descrever bem a utilidade das nossas funções e seus argumentos. Os modelos de linguagem
compreendem apenas texto, então o entendimento de para que as funções que estamos oferecendo
servem também deve ser feita por texto. Para que tenhamos funções e argumentos bem definidos,
o LangChain passou a utilizar a biblioteca Pydantic, por ser esta a principal ferramenta de validação
de estruturas de dados em Python. Agora vamos entender por que e como essa validação pode ser
importante para nós.
Como Criamos uma Estrutura de Dados Sem Pydantic
Antes de entendermos como criar estruturas no Pydantic, vamos ver como criar uma estrutura de
dados simples em Python sem usar essa biblioteca. Essa será nossa base de comparação e tornará
mais evidente a importância de utilizarmos Pydantic:
class Pessoa:
def __init__(self, nome: str, idade: int, peso: float) -> None:
self.nome = nome
self.idade = idade
self.peso = peso
adriano = Pessoa('Adriano', 32, 68)
print(adriano.idade)
# Saída: 32
A forma básica em Python é utilizando classes como feito acima. Acabamos de criar uma estrutura
para representar uma pessoa, e criamos uma instância dessa estrutura com argumentos referentes ao
professor Adriano.
No entanto, sem validação de tipos, podemos acabar com dados inconsistentes:
Asimov Academy
19


---