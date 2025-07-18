## Página 4

Deploy para CrewAI
01. Por que o Deploy é Importante?
De que adianta desenvolver um sistema multi‑agentes incrível se ninguém consegue acessá‑lo? O
deploy é o passo que transforma sua aplicação em algo acessível: seja via web, APIs ou aplicativos,
permitindo que qualquer pessoa, em qualquer lugar do mundo, interaja com sua solução.
Visão Geral
Neste breve curso de Deploy para CrewAI, abordaremos o caminho mais simples e intuitivo para colo‑
car sua Crew em produção:
1. Criar um projeto pronto para deploy: estrutura de arquivos e configuração inicial.
2. Adicionar o projeto ao GitHub: versionamento e integração contínua.
3. Conectar o GitHub ao CrewAI Enterprise: automação do processo de build e deploy.
4. Executar o deploy: publicando a API criada, testando via Postman e integrando em código
Python.
Ao final, você terá um projeto completo — da criação à implantação — e entenderá em profundidade
como gerar uma API a partir das suas Crews.
Próximos passos
No próximo capítulo vamos detalhar como configurar o main.py para inicializar sua Crew AI,
definindo endpoints e preparando a aplicação para receber requisições.
Asimov Academy
3


---
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