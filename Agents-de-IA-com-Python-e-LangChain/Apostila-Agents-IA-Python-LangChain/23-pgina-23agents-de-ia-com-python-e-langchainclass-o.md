## Página 23

Agents de IA com Python e LangChain
class ObterTemperaturaAtual(BaseModel):
"""Obtém a temperatura atual de uma determinada localidade"""
local: str = Field(description='O nome da cidade', examples=['São Paulo', 'Porto Alegre'])
unidade: Optional[UnidadeEnum]
Convertendo para uma Função da OpenAI
Agora vamos converter essa classe para uma função que a API da OpenAI consiga entender.
from langchain_core.utils.function_calling import convert_to_openai_function
tool_temperatura = convert_to_openai_function(ObterTemperaturaAtual)
print(tool_temperatura)
E obtemos o seguinte dicionário descrevendo a ferramenta:
{'name': 'ObterTemperaturaAtual',
'description': 'Obtém a temperatura atual de uma determinada localidade',
'parameters': {'type': 'object',
'properties': {'local': {'description': 'O nome da cidade',
'examples': ['São Paulo', 'Porto Alegre'],
'type': 'string'},
'unidade': {'description': 'An enumeration.',
'enum': ['celsius', 'fahrenheit'],
'type': 'string'}},
'required': ['local']}}
Adicionando Função Externa Utilizando LangChain
Agora que já sabemos criar funções que os modelos de LLM entendam, podemos passar essas funções
para os modelos de linguagem através da biblioteca LangChain.
Utilizando o Parâmetro functions
O parâmetro functions permite a adição de ferramentas externas aos chat_models do LangChain:
from langchain_openai import ChatOpenAI
chat = ChatOpenAI()
resposta = chat.invoke('Qual é a temperatura de Porto Alegre', functions=[tool_temperatura])
print(resposta)
Asimov Academy
22


---
## Página 24

Agents de IA com Python e LangChain
Criando um Novo Componente de chat_model
Também é possível vincular essa ferramenta indefinidamente a um chat_model utilizando o método
bind:
chat_com_func = chat.bind(functions=[tool_temperatura])
resposta = chat_com_func.invoke('Qual é a temperatura de Porto Alegre')
print(resposta)
Agora todas as próximas vezes que a instância chat_com_func for chamada, ela terá acesso a ferra-
menta.
Forçando o Modelo a Chamar uma Função
Da mesma forma que utilizando diretamente a biblioteca da OpenAI podemos forçar o modelo a
chamar a função, podemos fazê-lo com LangChain da seguinte forma:
resposta = chat.invoke(
'Qual é a temperatura de Porto Alegre',
functions=[tool_temperatura],
function_call={'name': 'ObterTemperaturaAtual'}
)
print(resposta)
Quando não passamos o parâmetro function_call, o modelo estará decidindo automaticamente a
necessidade de rodar a função (estará utilizando o “auto”, como visto no capítulo anterior).
Adicionando a uma Chain
Podemos adicionar agora este modelo com funções a um prompt e criar uma chain.
from langchain.prompts import ChatPromptTemplate
prompt = ChatPromptTemplate.from_messages([
('system', 'Você é um assistente amigável chamado Isaac'),
('user', '{input}')
])
chain = prompt | chat.bind(functions=[tool_temperatura])
resposta = chain.invoke({'input': 'Olá'})
print(resposta)
E é isso, pessoal! Hoje aprendemos como adicionar funções externas utilizando o LangChain e a
biblioteca Pydantic para validação de dados. O framework LangChain se mostrou novamente uma
grande arma para facilitar nosso trabalho ao criarmos aplicações com modelos de linguagem. Vamos
pro próximo capítulo, pois temos muito ainda a conhecer sobre nosso querido LangChain!
Asimov Academy
23


---