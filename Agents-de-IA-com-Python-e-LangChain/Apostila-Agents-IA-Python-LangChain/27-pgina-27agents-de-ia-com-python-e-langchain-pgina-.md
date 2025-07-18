## Página 27

Agents de IA com Python e LangChain
'lingua': {'description': 'Língua que o texto foi escrito (deve estar no formato ISO
639-1)',
�→
'type': 'string'}},
'required': ['sentimento', 'lingua']}}
Vamos testar com um texto de exemplo:
texto = 'Eu gosto muito de massa aos quatro queijos'
Agora, vamos configurar o prompt e o modelo de chat:
from langchain.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
prompt = ChatPromptTemplate.from_messages([
('system', 'Pense com cuidado ao categorizar o texto conforme as instruções'),
('user', '{input}')
])
chat = ChatOpenAI()
chain = prompt | chat.bind(functions=[tool_sentimento], function_call={'name': 'Sentimento'})
Vamos invocar a chain com o nosso texto:
chain.invoke({'input': 'Eu gosto muito de massa aos quatro queijos'})
AIMessage(content='', additional_kwargs={'function_call': {'arguments':
'{"sentimento":"pos","lingua":"pt"}', 'name': 'Sentimento'}},
response_metadata={'token_usage': {'completion_tokens': 11, 'prompt_tokens': 145,
'total_tokens': 156}, 'model_name': 'gpt-3.5-turbo', 'system_fingerprint': None,
'finish_reason': 'stop', 'logprobs': None},
id='run-e68e3dfc-105c-4cc9-9a2a-f08e9c359f67-0')
�→
�→
�→
�→
�→
Vamos testar com outro texto:
chain.invoke({'input': 'I dont like this food'})
AIMessage(content='', additional_kwargs={'function_call': {'arguments':
'{"sentimento":"neg","lingua":"en"}', 'name': 'Sentimento'}},
response_metadata={'token_usage': {'completion_tokens': 11, 'prompt_tokens': 138,
'total_tokens': 149}, 'model_name': 'gpt-3.5-turbo', 'system_fingerprint': None,
'finish_reason': 'stop', 'logprobs': None},
id='run-101f6bd8-b4b9-4e49-b076-f18619b06d14-0')
�→
�→
�→
�→
�→
Parseando a Saída para Obtermos Apenas o que Interessa
Podemos utilizar o JsonOutputFunctionsParser para obtermos como resultado final da nossa
chain apenas o que nos interessa, que é o dicionário com as tags do conteúdo.
from langchain.output_parsers.openai_functions import JsonOutputFunctionsParser
chain = (prompt
| chat.bind(functions=[tool_sentimento], function_call={'name': 'Sentimento'})
Asimov Academy
26


---
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