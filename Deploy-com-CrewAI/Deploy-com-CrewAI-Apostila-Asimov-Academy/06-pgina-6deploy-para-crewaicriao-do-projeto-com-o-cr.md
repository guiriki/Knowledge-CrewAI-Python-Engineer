## Página 6

Deploy para CrewAI
Criação do Projeto com o crewai create crew
1. Inicializando o Projeto:
ComoambientevirtualativoeoCrewAIToolsinstalado,utilizeocomandodecriaçãodeprojeto.
Por exemplo, para um projeto de deploy, execute:
crewai create "Crew for Deploy"
• Esse comando gera a estrutura básica do projeto, contendo arquivos como pyProject,
README.md e o arquivo .env para configuração de variáveis.
2. Configuração da Chave de API:
• Abra o arquivo .env e insira sua chave de API da OpenAI.
• Certifique‑se de que a chave está corretamente atribuída para que o projeto funcione em
conjunto com os serviços da OpenAI.
3. Observação sobre Modificações no Projeto:
• Diferentemente de outros experimentos com o CrewAI, não serão necessárias alterações
manuais nos arquivos como o main.py ou a adição de componentes como o AgentOps.
• Utilize o projeto exatamente como criado pelo comando crewai create, pois ele já
está preparado para o deploy.
Execução do Projeto
Após a criação do projeto e configuração do ambiente, execute‑o para verificar se tudo está funcio‑
nando corretamente:
1. Navegue até o Diretório do Projeto:
cd "Crew for Deploy"
2. Executando o Projeto:
Utilize o comando específico do CrewAI para rodar o projeto:
crewai run
• Durante essa execução, o sistema cria automaticamente um novo ambiente virtual (se
necessário) e configura as dependências do projeto.
– Um arquivo de lock, por exemplo, uv.lock, é gerado. Esse arquivo é essencial para que
o servidor de deploy saiba quais versões das bibliotecas devem ser instaladas, garantindo
que o ambiente replicado seja idêntico ao utilizado durante o desenvolvimento.
Asimov Academy
5


---
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