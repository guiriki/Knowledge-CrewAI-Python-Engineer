## Página 16

Deploy para CrewAI
• Configurar o Postman com a URL e o Bearer Token.
• Testar a disponibilidade da API enviando uma requisição simples.
• Consultar os parâmetros necessários (inputs).
• Iniciar a execução (kickoff) e monitorar seu status.
No próximo capítulo, veremos como realizar esses mesmos testes utilizando Python, ampliando suas
ferramentas de integração.
Asimov Academy
15


---
## Página 17

Deploy para CrewAI
06. Testando a API com Python
Até aqui você viu como testar sua API via Postman; agora é hora de trazer tudo para o seu ambiente
Python. Neste capítulo, vamos replicar em código as mesmas chamadas de inputs, kickoff e status
que fizemos no Postman — mas usando um notebook e a biblioteca requests. Assim, você terá
exemplos prontos para incorporar aos seus projetos Python.
Preparando o ambiente
1. Criando o notebook
Abraoseueditor(Jupyter,VSCode,Colabetc.) ecrieumarquivochamadoAPI_Testing.ipynb.
2. Instalando a biblioteca
Caso ainda não tenha, instale o requests:
pip install requests
3. Defina URL e token: no início do notebook, armazene a URL de deploy e o Bearer Token em
variáveis, montando um cabeçalho de autenticação:
import requests
url = "https://crew-for-deply-7fb406fe-5558-4f49-9a53-7cf3-47c034f1.crewai.com"
token = "90e7968cb875"
headers = {
"Authorization": f"Bearer {token}",
"Content-Type": "application/json"
}
```
## Verificando se a API está viva
Antes de qualquer outra chamada, confirme que a API responde:
``` python
response = requests.get(url, headers=headers)
if response.status_code == 200:
print("API está saudável:", response.text)
else:
print(f"Erro ao conectar: {response.status_code}")
• **requests.get** faz o GET na URL base.
• 200 significa que a API retornou com sucesso (normalmente um JSON com {
"status":
"Healthy" }).
Asimov Academy
16


---