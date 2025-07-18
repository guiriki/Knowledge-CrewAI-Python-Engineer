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
## Página 19

Deploy para CrewAI
Conclusão
Você agora tem um notebook completo para testar a API Crew AI via Python, capaz de:
• Confirmar a disponibilidade da API;
• Listar inputs necessários;
• Iniciar execuções programaticamente;
• Acompanhar o resultado final.
Com o conteúdo apresentado, percorremos todo o fluxo de deploy de projetos na plataforma CrewAI
Enterprise, da criação da API à sua validação prática com Postman e Python. A proposta foi ofere‑
cer uma base clara, aplicável e objetiva, capacitando desenvolvedores a integrarem e testarem suas
soluções com autonomia e segurança.
Agora, com esses fundamentos em mãos, você está pronto para explorar novos desafios, integrar sis‑
temas mais robustos e transformar suas ideias em aplicações inteligentes e escaláveis. A tecnologia
está ao seu alcance — e seu próximo passo depende apenas da sua iniciativa.
Siga praticando, experimentando e evoluindo. O domínio do deploy com CrewAI é só o começo.
Asimov Academy
18