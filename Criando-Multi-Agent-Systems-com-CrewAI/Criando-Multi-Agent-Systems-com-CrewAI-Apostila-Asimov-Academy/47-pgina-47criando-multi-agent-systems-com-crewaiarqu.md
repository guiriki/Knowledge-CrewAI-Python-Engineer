## Página 47

Criando Multi Agent Systems com CrewAI
Arquivo crew.py
Agora vamos para o arquivo crew.py, onde fazemos a criação da nossa Crew de fato. É ele que im‑
portará as definições de agents e tasks, definirá o tipo do processo e combinará as tools aos agents,
conforme necessário, o que veremos mais adiante no curso.
Este é o exemplo que vem ao criarmos o projeto inicialmente:
from crewai import Agent, Crew, Process, Task
from crewai.project import CrewBase, agent, crew, task
@CrewBase
class ProjetoTeste():
"""ProjetoTeste crew"""
agents_config = 'config/agents.yaml'
tasks_config = 'config/tasks.yaml'
@agent
def researcher(self) -> Agent:
return Agent(
config=self.agents_config['researcher'],
verbose=True
)
@agent
def reporting_analyst(self) -> Agent:
return Agent(
config=self.agents_config['reporting_analyst'],
verbose=True
)
@task
def research_task(self) -> Task:
return Task(
config=self.tasks_config['research_task'],
)
@task
def reporting_task(self) -> Task:
return Task(
config=self.tasks_config['reporting_task'],
output_file='report.md'
)
@crew
def crew(self) -> Crew:
"""Creates the ProjetoTeste crew"""
return Crew(
agents=self.agents,
tasks=self.tasks,
process=Process.sequential,
Asimov Academy
46


---
## Página 48

Criando Multi Agent Systems com CrewAI
verbose=True,
)
Você pode nunca ter se deparado com uma estrutura como a classe ProjetoTeste em Python, mas
é bem simples! Essa classe foi criada para unificar a configuração da sua crew, e você verá que não
precisará modificá‑la drasticamente.
Além das classes, temos decoradores, aquela palavras com um @ na frente. Estes decoradores tam‑
bém são padrão da bibliotecas mas de super fácil utilização!
E para tudo ficar bem claro, vou deixar uma breve explicação de o que é classe e decoradores para
quem não tem familiaridade com esses termos.
O que é uma classe?
Em Python, uma classe é como um molde que define um tipo de objeto. Dentro de uma classe, pode‑
mos definir propriedades (dados) e métodos (funções) que descrevem o comportamento desse ob‑
jeto. No caso da classe ProjetoTeste, estamos definindo como criar e gerenciar uma crew de
agentes e tarefas.
O que são decoradores?
Em termos simples, decoradores são uma forma de modificar o comportamento de uma função,
método ou classe sem alterar seu código interno. No contexto da nossa classe ProjetoTeste,
usamos decoradores para marcar quais métodos se tornarão agents, tasks e o método que define a
crew.
Por exemplo, ao criar o agente researcher, usamos o decorador @agent antes da definição
do método. Isso indica que o método subsequente será um agent. Dentro do método, simples‑
mente referenciamos o nome do agente, conforme definido no arquivo agents.yaml, utilizando
self.agents_config['researcher']. Isso garante que todas as configurações do agente
sejam carregadas automaticamente a partir do arquivo YAML.
O processo para definir as tasks é bastante semelhante. Neste caso, usamos o decorador @task,
e assim como fizemos com os agents, configuramos o método para apontar para a variável
tasks_config, onde estão definidas as tasks no arquivo tasks.yaml.
Agora, é importante notar que você precisará criar um número de métodos equivalente à quanti‑
dade de agents e tasks que a crew terá. Não se preocupe! Você pode facilmente fazer cópias dos
métodos existentes, alterar o nome (por exemplo, de researcher para reporting_analyst) e
Asimov Academy
47


---