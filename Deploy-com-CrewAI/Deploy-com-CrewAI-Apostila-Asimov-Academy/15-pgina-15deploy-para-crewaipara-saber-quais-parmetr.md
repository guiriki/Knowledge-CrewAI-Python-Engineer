## Página 15

Deploy para CrewAI
Para saber quais parâmetros (inputs) sua aplicação requer, envie uma requisição GET para o endpoint
/inputs (exemplo: http://sua_url/inputs). Essa requisição retornará uma lista com os in‑
puts necessários, como “Topic” e “Current Year”, que deverão ser usados nas próximas chamadas.
Exemplo de Resposta
{
"inputs": ["Topic", "Current Year"]
}
Iniciando o Processo com Kickoff
Com os inputs identificados, é hora de iniciar a execução da API utilizando o endpoint /kick-
off.
Configure uma nova requisição com método POST e insira a URL apropriada (exemplo:
http://sua_url/kickoff). No corpo da requisição, escolha o formato raw com JSON e insira
os dados conforme abaixo:
Exemplo de Corpo da Requisição
{
"inputs": {
"Topic": "CREAI",
"Current Year": 2025
}
}
Se a requisição estiver correta, a API retornará um identificador (kickoff ID) para acompanhar a exe‑
cução.
Monitorando a Execução
Para acompanhar o andamento do processamento iniciado, envie uma requisição GET para o
endpoint /status/[KICKOFF_ID], substituindo [KICKOFF_ID] pelo identificador recebido.
Essa requisição permitirá verificar se o processo está em execução, já concluído ou se ocorreu algum
erro.
Conclusão
AutilizaçãodoPostmanpossibilitatestarevalidartodososendpointsdasuaAPIdemaneirainterativa
e intuitiva. Neste capítulo, você aprendeu a:
Asimov Academy
14


---
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