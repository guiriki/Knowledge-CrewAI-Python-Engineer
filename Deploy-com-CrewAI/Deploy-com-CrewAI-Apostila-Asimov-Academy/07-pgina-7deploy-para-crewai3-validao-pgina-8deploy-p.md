## Página 7

Deploy para CrewAI
3. Validação:
Se o projeto executa sem erros após o comando crewai run, significa que a estrutura está
correta e pronta para o deploy.
Considerações Finais
• Setup do Projeto:
O setup realizado nesta aula assegura que seu projeto esteja devidamente configurado e
preparado para as etapas seguintes:
– Publicação no GitHub.
– Realização do deploy via CrewAI Enterprise.
• Próximos Passos:
A seguir, veremos como adicionar o projeto criado ao GitHub. Em seguida, abordaremos o pro‑
cesso completo para realizar o deploy da aplicação.
Asimov Academy
6


---
## Página 8

Deploy para CrewAI
03. Adicionando meu projeto ao GitHub
Nesta aula, vamos aprender como adicionar o projeto (já criado e preparado para deploy) ao GitHub.
Essa etapa é fundamental porque o CrewAI Enterprise utilizará o repositório hospedado no GitHub
para acessar o seu código e realizar o deploy. Embora a abordagem mostrada utilize o Visual Studio
Code (VS Code), você pode adotar outras ferramentas como Git Bash, GitHub Desktop ou a linha de
comando, conforme sua preferência.
Preparando o Ambiente no VS Code
• Contexto:
Durante a criação do projeto com o comando de criação do CrewAI, foi gerado um diretório
(neste exemplo, chamado “Crew for Deploy”) que contém tudo que é necessário para o
deploy.
• Ação:
Abra a pasta do projeto diretamente no VS Code.
Dica: Garanta que você esteja trabalhando somente com os arquivos que estão dentro desta
pasta, descartando elementos que estejam fora dela.
Inicializando o Repositório Git
• No VS Code, acesse a área de Controle de Código Fonte e clique em Initialize Repository para
transformar sua pasta em um repositório Git local.
• Após a inicialização, verifique se os arquivos do projeto aparecem na lista de mudanças pen‑
dentes (staged ou unstaged).
Configurando o Arquivo .gitignore
Importância do .gitignore
O arquivo .gitignore é essencial para evitar que arquivos ou pastas indesejadas sejam enviados para
o repositório remoto. No seu caso:
• Ambiente Virtual:
Evite subir a pasta do ambiente virtual (por exemplo, .venv ou venv). Lembre‑se de que o sis‑
tema de deploy criará um novo ambiente virtual com base no arquivo de dependências (como
o uv.lock).
Asimov Academy
7


---