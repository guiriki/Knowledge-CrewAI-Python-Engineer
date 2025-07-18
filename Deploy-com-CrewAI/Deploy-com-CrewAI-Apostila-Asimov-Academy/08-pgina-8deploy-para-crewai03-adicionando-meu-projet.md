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
## Página 9

Deploy para CrewAI
• Variáveis de Ambiente:
O arquivo .env contém segredos, como a chave da API da OpenAI. Não faça o commit deste
arquivo para o repositório público. ### Exemplificação
Abra (ou crie) o arquivo .gitignore e adicione as seguintes linhas (personalize conforme
necessário):
# Ignorar o ambiente virtual
.venv/
venv/
# Ignorar arquivo de variáveis de ambiente
.env
Fazendo o Primeiro Commit
1. Staging das Alterações:
No VS Code, clique no ícone de “Stage All Changes” para preparar todas as alterações para com‑
mit.
2. Mensagem do Commit:
Insira uma mensagem descritiva, como “Primeiro commit” e confirme o commit.
3. Verificação:
Confirme que os arquivos indesejados (como .env e o diretório do ambiente virtual) não estão
presentes na listagem de arquivos versionados, graças ao .gitignore.
Sincronizando o Repositório Local com o GitHub
• Acesse sua conta no GitHub e crie um novo repositório.
Observação: No exemplo, o nome do repositório será “crew for Depli”. Não é necessário adi‑
cionar um README ou .gitignore, pois esses arquivos já foram configurados localmente.
Adicionando o Remote no VS Code
1. Adicionar Remote:
No VS Code, na área de Git, clique no ícone de “Mais ações” (três pontinhos) e escolha a opção
Remote: Add Remote.
2. Selecionando o Repositório:
O VS Code pode sugerir o repositório criado recentemente. Caso contrário, insira a URL do
repositório remoto manualmente.
Asimov Academy
8


---