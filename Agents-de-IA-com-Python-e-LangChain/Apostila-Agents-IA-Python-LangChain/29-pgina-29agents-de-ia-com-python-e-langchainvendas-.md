## Página 29

Agents de IA com Python e LangChain
vendas = 'vendas'
spam = 'spam'
class DirecionaSetorResponsavel(BaseModel):
"""Direciona a dúvida de um cliente ou aluno da escola de programação Asimov para o setor
responsável"""
�→
setor: SetorEnum
Vamos converter essa função para o formato da OpenAI:
from langchain_core.utils.function_calling import convert_to_openai_function
tool_direcionamento = convert_to_openai_function(DirecionaSetorResponsavel)
tool_direcionamento
{'name': 'DirecionaSetorResponsavel',
'description': 'Direciona a dúvida de um cliente ou aluno da escola de programação Asimov
para o setor responsável',
�→
'parameters': {'type': 'object',
'properties': {'setor': {'description': 'An enumeration.',
'enum': ['atendimento_cliente', 'duvidas_aluno', 'vendas', 'spam'],
'type': 'string'}},
'required': ['setor']}}
Vamos configurar o prompt e o modelo de chat:
from langchain.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
from langchain.output_parsers.openai_functions import JsonOutputFunctionsParser
prompt = ChatPromptTemplate.from_messages([
('system', 'Pense com cuidado ao categorizar o texto conforme as instruções'),
('user', '{input}')
])
chat = ChatOpenAI()
chain = (prompt
| chat.bind(functions=[tool_direcionamento], function_call={'name':
'DirecionaSetorResponsavel'})
�→
| JsonOutputFunctionsParser())
Vamos testar com uma das dúvidas:
duvida = duvidas[5]
resposta = chain.invoke({'input': duvida})
print('Dúvida:', duvida)
print('Resposta:', resposta)
Dúvida: Bom dia. Não enconte no site o preço de um curso avulso. SAberiam me informar?
Resposta: {'setor': 'atendimento_cliente'}
Neste caso, gostaríamos que a dúvida fosse direcionada para vendas. Podemos melhorar nosso prompt
para aumentar a chance do modelo responder como gostaríamos:
Asimov Academy
28


---
## Página 30

Agents de IA com Python e LangChain
from langchain.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
from langchain.output_parsers.openai_functions import JsonOutputFunctionsParser
system_message = '''Pense com cuidado ao categorizar o texto conforme as instruções.
Questões relacionadas a dúvidas de preço, sobre o produto, como funciona devem ser
direcionadas para "vendas".
�→
Questões relacionadas a conta, acesso a plataforma, a cancelamento e renovação de assinatura
devem ser direcionadas para "atendimento_cliente".
�→
Questões relacionadas a dúvidas técnicas de programação, conteúdos da plataforma ou
tecnologias na área da programação devem ser direcionadas para "duvidas_alunos".
�→
Mensagens suspeitas, em outras línguas que não português, contendo links devem ser
direcionadas para "spam".
�→
'''
prompt = ChatPromptTemplate.from_messages([
('system', system_message),
('user', '{input}')
])
chat = ChatOpenAI()
chain = (prompt
| chat.bind(functions=[tool_direcionamento], function_call={'name':
'DirecionaSetorResponsavel'})
�→
| JsonOutputFunctionsParser())
Vamos testar novamente com a mesma dúvida:
duvida = duvidas[5]
resposta = chain.invoke({'input': duvida})
print('Dúvida:', duvida)
print('Resposta:', resposta)
Dúvida: Bom dia. Não enconte no site o preço de um curso avulso. SAberiam me informar?
Resposta: {'setor': 'vendas'}
Vocês podem ver que é um conjunto de tarefas. Tem, claro, a definição da nossa função, que temos
que fazer bem, mas também tem muito de prompt, de engenharia de prompt, de forma que fique
bem claro para o modelo como ele deve categorizar. Quanto mais informação dermos, melhor será a
categorização que ele fará.
Dica de conteúdo
Na nossa aula sobre tagging, discutimos como a categorização de dados (tagging) pode ser uma
ferramenta poderosa para interpretar e estruturar informações em texto.
Um ótimo exemplo prático dessa aplicação esta no vídeo do Rodrigo, que foi postado no YouTube
recentemente. Nele, o Rodrigo mostra como utilizar tagging para categorizar suas compras do cartão
de crédito, criando assim facilmente uma ferramenta de análise para finanças pessoais.
Asimov Academy
29


---