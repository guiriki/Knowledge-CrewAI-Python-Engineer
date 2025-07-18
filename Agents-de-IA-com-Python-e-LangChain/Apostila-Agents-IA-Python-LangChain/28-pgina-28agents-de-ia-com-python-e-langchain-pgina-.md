## Página 28

Agents de IA com Python e LangChain
| JsonOutputFunctionsParser())
chain.invoke({'input': 'Eu gosto muito de massa aos quatro queijos'})
{'sentimento': 'pos', 'lingua': 'pt'}
chain.invoke({'input': 'I dont like this food'})
{'sentimento': 'neg', 'lingua': 'en'}
Um Exemplo Mais Interessante
Vamos agora para um exemplo um pouco mais complexo. Digamos que temos um chatbot e queremos
fazerumroteamentoparaossetoresdeinteresse,nonossocaso: atendimento_cliente,duvidas_alunos,
vendas, spam. A primeira etapa é criar um modelo que entenda a solicitação do cliente e direcione
para o setor certo.
Retiramos as seguintes mensagens de email recebidos pela nossa equipe de atendimento e vamos
tentar criar um direcionamento para elas:
duvidas = [
'Bom dia, gostaria de saber se há um certificado final para cada trilha ou se os
certificados são somente para os cursos e projetos? Obrigado!',
�→
'In Etsy, Amazon, eBay, Shopify https://pint77.com Pinterest+SEO +II = high sales
results',
�→
'Boa tarde, estou iniciando hoje e estou perdido. Tenho vários objetivos. Não sei nada
programação, exceto que utilizo o Power automate desktop da Microsoft. Quero aprender
tudo na plataforma que se relacione ao Trading de criptomoedas. Quero automatizar
Tradings, fazer o sistema reconhecer padrões, comprar e vender segundo critérios que
eu defina, etc. Também tenho objetivos de aprender o máximo para utilizar em
automações no trabalho também, que envolve a área jurídica e trabalho em processos.
Como sou fã de eletrônica e tenho cursos na área, também queria aprender o que precisa
para automatizacões diversas. Existe algum curso ou trilha que me prepare com base
para todas essas áreas ao mesmo tempo e a partir dele eu aprenda isoladamente aquilo
que seria exigido para aplicar aos meus projetos?',
�→
�→
�→
�→
�→
�→
�→
�→
�→
'Bom dia, Havia pedido cancelamento de minha mensalidade no mes 2 e continuaram cobrando.
Peço cancelamento da assinatura. Peço por gentileza, para efetivarem o cancelamento da
assomatura e pagamento.',
�→
�→
'Bom dia. Não estou conseguindo tirar os certificados dos cursos que concluí. Por exemplo,
já consegui 100% no python starter, porém, não consigo tirar o certificado. Como
faço?',
�→
�→
'Bom dia. Não enconte no site o preço de um curso avulso. SAberiam me informar?'
]
Vamos criar um modelo que entenda a solicitação do cliente e direcione para o setor certo:
from enum import Enum
from pydantic import BaseModel, Field
class SetorEnum(str, Enum):
atendimento_cliente = 'atendimento_cliente'
duvidas_aluno = 'duvidas_aluno'
Asimov Academy
27


---
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