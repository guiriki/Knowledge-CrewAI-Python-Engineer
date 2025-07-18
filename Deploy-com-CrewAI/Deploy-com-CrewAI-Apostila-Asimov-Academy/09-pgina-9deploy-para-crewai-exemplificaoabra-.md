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
## Página 10

Deploy para CrewAI
3. Verificação:
Certifique‑se de que o remote foi adicionado corretamente e que a branch principal (geral‑
mente, main) está configurada para sincronização com o repositório GitHub.
Realizando o Push para o GitHub
• Com o remote configurado, clique em “Push” para enviar todas as alterações do repositório
local para o GitHub.
• Verifique, na interface web do GitHub, se os arquivos apareceram corretamente e se os arquivos
sensíveis (como .env) foram devidamente ignorados.
Conclusão e Próximos Passos
• Revisão:
Aqui, você aprendeu a transformar a pasta do projeto local em um repositório Git, configurar
o .gitignore para garantir que arquivos sensíveis ou desnecessários sejam ignorados e sin‑
cronizar o repositório com o GitHub.
• Próximas Etapas:
A seguir, veremos como realizar o deploy do seu projeto utilizando o CrewAI Enterprise, que fará
a conexão e a execução do deploy a partir do repositório do GitHub.
Asimov Academy
9


---