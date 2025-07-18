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
## Página 18

Deploy para CrewAI
Consultando os inputs
Para saber quais parâmetros a API espera, faça um GET em /inputs:
response = requests.get(f"{url}/inputs", headers=headers)
if response.status_code == 200:
print("Inputs disponíveis:", response.json()["inputs"])
else:
print(f"Falha ao obter inputs: {response.status_code}")
A saída deve listar os campos, por exemplo:
Inputs disponíveis: ['topic', 'current_year']
Iniciando uma execução (kickoff)
Com os inputs identificados, dispare a execução com um POST em /kickoff:
body = {
'inputs': {
'topic': 'CrewAI',
'current_year': 2025
}
}
response = requests.post(f"{url}/kickoff", headers=headers, json=body)
if response.status_code == 200:
kickoff_id = response.json().get('kickoff_id')
print("Kickoff iniciado com ID:", kickoff_id)
else:
print(f"Erro no kickoff: {response.status_code}", response.text)
• **json=body** serializa automaticamente o dicionário em JSON.
• O retorno contém kickoff_id, que identifica essa execução.
Acompanhando o status da execução
Para verificar o andamento, faça um GET em /status/{kickoff_id}:
kickoff_id = '579d6d03-2b4d-4230-b716-cbcd5273615f'
response = requests.get(f"{url}/status/{kickoff_id}", headers=headers)
if response.status_code == 200:
result = response.json().get('result')
print("Resultado final:", result)
else:
print(f"Erro ao checar status: {response.status_code}")
Quando o state for “success”, o campo result traz o output completo gerado pela sua CREW.
Asimov Academy
17


---