## Página 13

Deploy para CrewAI
• Verificação da API:
Na próxima aula, será o momento de testar a API que foi criada. Esse teste confirmará se o
deploy foi realizado com sucesso e se a aplicação está funcionando como esperado.
• Observação Importante:
Se durante o processo ocorrer algum erro, utilize o recurso de redeploy fornecido pela
plataforma. Geralmente, uma nova tentativa resolve problemas pontuais sem a necessidade
de alterações no projeto.
Asimov Academy
12


---
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