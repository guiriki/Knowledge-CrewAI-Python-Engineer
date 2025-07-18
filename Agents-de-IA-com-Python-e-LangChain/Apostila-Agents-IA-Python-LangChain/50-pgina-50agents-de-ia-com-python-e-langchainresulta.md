## Página 50

Agents de IA com Python e LangChain
resultado.tool
'busca_wikipedia'
resultado.tool_input
{'query': 'Isaac Asimov'}
E um AgentFinish, caso a mensagem esteja finalizada.
resultado = chain.invoke({'input': 'Olá'})
resultado
AgentFinish(return_values={'output': 'Olá! Como posso te ajudar hoje?'}, log='Olá! Como posso
te ajudar hoje?')
�→
resultado.return_values['output']
'Olá! Como posso te ajudar hoje?'
Rodando as Ferramentas
Podemos criar uma função simples de roteamento para lidar com os dois estados possíveis:
from langchain_core.agents import AgentFinish
def roteamento(resultado):
if isinstance(resultado, AgentFinish):
return resultado.return_values['output']
else:
return tool_run[resultado.tool].run(resultado.tool_input)
Podemos adicionar essa função a nossa chain:
chain = prompt | chat.bind(functions=tools_json) | OpenAIFunctionsAgentOutputParser() |
roteamento
�→
E rodamos primeiro com uma input que não necessitará utilização de tools:
chain.invoke({'input': 'Olá'})
E a resposta será diretamente a string de resposta:
'Olá! Como posso ajudar você hoje?'
Agora quando fazemos uma pergunta que necessita de uma tool:
chain.invoke({'input': 'Quem foi Isaac Asimov?'})
E o resultado é a observação gerada pela tool:
Asimov Academy
49


---
## Página 51

Agents de IA com Python e LangChain
'Título da página: Isaac Asimov\nResumo: Isaac Asimov foi um escritor e bioquímico
norte-americano, nascido na Rússia, autor de obras de ficção científica e divulgação
científica.\nAsimov é considerado um dos mestres da ficção científica e, junto com Robert
A. Heinlein e Arthur C. Clarke, foi considerado um dos "três grandes" dessa área da
literatura. A obra mais famosa de Asimov é a Série da Fundação, também conhecida como
Trilogia da Fundação, que faz parte da série do Império Galáctico e que logo combinou com
a Série Robôs.
�→
�→
�→
�→
�→
�→
...
Então, pessoal, nessa aula aprendemos a criar um sistema de roteamento para execução automática
de tools. Com isso, estamos cada vez mais próximos de criar agentes completos e funcionais.
Desafio - Enviando um Email
E agora que vocês já sabem como criar uma tool, vou propor um desafio para vocês!
Vamos criar uma tool de envio de email e depois fornecê-la ao nosso modelo de linguagem, criando
uma estrutura mais simples de um agente.
Vocês podem utilizar o seguinte código em Python retirado do projeto Central de Emails para envio de
emails:
from email.message import EmailMessage
import smtplib
import ssl
def envia_email(destinatario, titulo, corpo):
email_usuario = 'ADICIONE SEU EMAIL AQUI'
senha_app = 'ADICIONE SUA APP KEY AQUI'
message_email = EmailMessage()
message_email['From'] = email_usuario
message_email['To'] = destinatario
message_email['Subject'] = titulo
message_email.set_content(corpo)
safe = ssl.create_default_context()
with smtplib.SMTP_SSL('smtp.gmail.com', 465, context=safe) as smtp:
smtp.login(email_usuario, senha_app)
smtp.sendmail(email_usuario, destinatario, message_email.as_string())
Vocês precisam fazer o seguinte: 1. A partir da função, criem uma tool 2. Desenvolvam o argschema da
tool, lembrando que todos os argumentos são strings. 3. Combinem a tool a um modelo de linguagem.
4. Enviem um email utilizando o modelo de linguagem para ‘aluno@asimov.academy’ com o título
‘Enviando um email com llm’ e uma mensagem bonita no corpo do texto.
Asimov Academy
50


---