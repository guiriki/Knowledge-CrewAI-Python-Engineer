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
## Página 31

Agents de IA com Python e LangChain
É uma aplicação prática exatamente dos conhecimentos que abordamos nesta aula, e sugiro que vocês
deem uma conferida!
Graças ao tagging, podemos desenvolver aplicações que entendem o contexto dos dados e os organi-
zam de maneira que façam sentido.
Além disso, existem diversas atividades de categorização que podemos realizar com os modelos de
linguagem, assim como o Rodrigo fez. Esses modelos são grandes ferramentas para estruturar
dados não estruturados, transformando uma vasta gama de informações que, de outra forma, seriam
difíceis de processar, em dados acessíveis e prontos para análise.
Essa capacidade de categorizar e interpretar dados é uma verdadeira revolução na área de análise
de dados. Com o uso de tagging, podemos trabalhar cada vez mais com dados em texto, o que abre
um leque de possibilidades para aplicações em diferentes setores. Seja na análise de sentimentos, no
direcionamento de dúvidas em um chatbot ou na organização de feedbacks de clientes, o tagging se
mostra uma ferramenta poderosa que pode mudar a forma como lidamos com informações.
Portanto, não deixem de conferir o vídeo do Rodrigo e se inspirar nas diversas maneiras de aplicar o
tagging em suas próprias soluções.
Asimov Academy
30


---