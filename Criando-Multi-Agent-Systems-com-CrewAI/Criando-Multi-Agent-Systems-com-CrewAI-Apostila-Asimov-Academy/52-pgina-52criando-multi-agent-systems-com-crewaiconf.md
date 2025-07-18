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
## Página 53

Criando Multi Agent Systems com CrewAI
Para isso, basta adicionar o seguinte código antes de rodar a sua Crew:
import agentops
agentops.init()
O painel do AgentOps
O painel do AgentOps é uma ferramenta poderosa que oferece uma visualização abrangente do com‑
portamento dos agentes. Após configurar o AgentOps, cada execução do seu programa é registrada
como uma sessão, e todos os dados relevantes (como prompts, execuções e eventos) são gravados
automaticamente. Você pode acessar detalhes sobre cada sessão, como tempo de execução total,
redesenhos de chamadas LLM e muito mais.
Análise de Sessões
O painel oferece um “Session Drawer” que lista todas as sessões anteriormente registradas e dados
úteissobrecadauma. O“SessionWaterfall”apresentaumavisualizaçãoemtemporealdaschamadas
de LLM, eventos de ação, chamadas de ferramentas e erros, permitindo que você obtenha detalhes
específicos sobre eventos selecionados.
Asimov Academy
52


---