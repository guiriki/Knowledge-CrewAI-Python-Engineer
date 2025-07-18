## Página 14

Deploy para CrewAI
05. Testando a API com Postman
Agora que você já fez o deploy da sua API, vamos aprender a testá‑la utilizando o Postman. Se você
ainda não conhece essa ferramenta, ela é bastante popular entre os desenvolvedores por facilitar a
criação e o envio de requisições HTTP.
Postman
O Postman é uma ferramenta essencial para desenvolvedores que trabalham com APIs. Ele permite
criar, enviar e monitorar requisições HTTP de forma interativa, simplificando o processo de testes e
o desenvolvimento de integrações. Se você ainda não conhece o Postman, saiba que ele vai ajudá‑lo
a:
• Visualizar respostas: Exibe os resultados das requisições de forma clara, com formatação au‑
tomática do JSON e outros tipos de conteúdo.
• Automatizartestes: Permiteacriaçãodescriptsparatestarautomaticamenteasrespostasdas
APIs.
• Organizar chamadas: Com Workspaces e coleções, você pode manter todas as suas requi‑
sições organizadas, facilitando o gerenciamento dos endpoints que compõem sua aplicação.
Caso ainda não tenha uma conta, acesse postman.com e crie a sua. Após o login, normalmente você
trabalhará no “My Workspace”, que agrupa todas as suas requisições de forma prática.
Preparando a Requisição
Inicie copiando a URL da API, que foi utilizada no processo de deploy. Essa URL será a base para todas
as requisições. Além disso, como a API utiliza um Bearer Token (que funciona como uma “senha”),
inclua‑o na seção de Authorization do Postman. Isso garante o acesso aos recursos protegidos da
API.
Teste Inicial da API
Para confirmar que a API está operando, envie uma requisição GET simples para a URL da API. Se
tudo estiver correto, a resposta indicará que a API está “Healthy” e funcionando. ### Consulta aos
Parâmetros
Asimov Academy
13


---
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