## Página 5

Deploy para CrewAI
02. Criando um projeto pronto para deploy
Nestaaula, iremosaprendercomocriarumprojetocomoCrewAIeprepará‑loparaodeploy. Odeploy
será realizado utilizando o CrewAI Enterprise, uma solução criada pela comunidade dos desenvolve‑
dores do CrewAI para a realização de deploys específicos para aplicativos construídos com CrewAI.
Atenção: A plataforma não suporta deploy para outras tecnologias, como Streamlit ou Dash.
Acessando o CrewAI Enterprise
1. Login e Integração com o GitHub:
• Acesse a interface pelo endereço: www.crewai.com/enterprise
• Realize o login na plataforma.
• Conecte sua conta do GitHub, pois o CrewAI Enterprise necessita de acesso aos seus
repositórios.
• Observação: Se o projeto não estiver hospedado no GitHub, o deploy não será possível.
2. Fluxo de Deploy Utilizando o GitHub:
• Durante o curso, veremos não apenas a criação do projeto mas também o processo de
publicação no GitHub.
• Em seguida, aprenderemos a criar uma API a partir desse projeto utilizando o CrewAI En‑
terprise.
Configuração do Ambiente e Criação do Projeto
Preparação do Ambiente Virtual
Antes de criar o projeto, é importante garantir que o ambiente virtual está configurado corretamente,
conforme os requisitos de versão do Python:
• Versões Suportadas: O CrewAI funciona melhor com Python nas versões 3.10 até 3.12.
• Criação e Ativação do Ambiente Virtual:
• Linux:
source ./venv/bin/activate
• Windows (PowerShell):
.\venv\Scripts\Activate.ps1
Asimov Academy
4


---
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