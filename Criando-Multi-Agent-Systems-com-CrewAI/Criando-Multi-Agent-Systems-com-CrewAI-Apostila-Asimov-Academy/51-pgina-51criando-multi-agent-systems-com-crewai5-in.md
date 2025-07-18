## Página 51

Criando Multi Agent Systems com CrewAI
5. Interface do Painel: O painel do AgentOps proporciona uma visão geral de estatísticas altas
sobre agentes em desenvolvimento e produção, além de permitir um drilldown para ver inter‑
ações em tempo real.
Como Utilizar o AgentOps
Para começar a usar o AgentOps, você deve realizar algumas etapas simples:
Crie uma conta na AgentOps
Acesse o seguinte link para fazer o cadastro: https://app.agentops.ai/signin
Crie um novo projeto
Entre na página de projetos e crie um novo projeto.
Salve sua chave de API
Salve a chave de API apresentada durante a criação do projeto.
Asimov Academy
50


---
## Página 52

Criando Multi Agent Systems com CrewAI
Configure seu Ambiente
Adicione sua chave de API às variáveis de ambiente, garantindo que o AgentOps tenha acesso às cre‑
denciais necessárias.
AGENTOPS_API_KEY=sua-chave-aqui
Instale a biblioteca do AgentOps
Utilize o comando pip install 'crewai[agentops]' para integrar o AgentOps ao seu pro‑
jeto.
Inicialize o AgentOps:
Antes de usar o Crew no seu script, inclua as linhas de importação e inicialização para rastrear auto‑
maticamente os agentes do Crew.
Asimov Academy
51


---