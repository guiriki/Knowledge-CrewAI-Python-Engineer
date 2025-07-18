## Página 32

Criando Multi Agent Systems com CrewAI
@task
def especificar_agentes(self) -> Task:
return Task(
config=self.tasks_config['especificar_agentes'],
output_file='output/agents.yaml'
)
@task
def definir_tarefas(self) -> Task:
return Task(
config=self.tasks_config['definir_tarefas'],
output_file='output/tasks.yaml'
)
@task
def orquestrar_agentes_e_tarefas(self) -> Task:
return Task(
config=self.tasks_config['orquestrar_agentes_e_tarefas'],
output_file='output/crew.py'
)
@crew
def crew(self) -> Crew:
"""Creates the CrewCreator crew"""
return Crew(
agents=self.agents, # Automatically created by the @agent decorator
tasks=self.tasks, # Automatically created by the @task decorator
process=Process.sequential,
verbose=True,
)
Asimov Academy
31


---
## Página 33

Criando Multi Agent Systems com CrewAI
08. Projeto ‑ Criando uma crew para criar crews
Então vamos colocar a massa em um projeto! A ideia é criamos uma aplicação que já nos gere pronto
os arquivo agents.yaml, tasks.yaml e crew.py, para economizar o nossotrabalho ao longo do nosso
curso.
Istojá uma mentalidadede quem desenvolve aplicaçõesde IA, se vocêpercebe que haverá uma tarefa
que você repetirá diversas vezes, já a automatize agora e, claro, utilizando IA!
Vamoslá, seesteprojetoforcriadovaiserbemlegal, poisnãomaisprecisaremoscriarnenhumarquivo
na mão na hora ded desenvolvvemros novas crews!
Desenvolvendo a primeira versão do sistema
Comojávimos, vamostentarutilizarochatparacriarosnossosagentsetasks, conformeencimnamos
anteriormente. Vamsover se funcionará!
Primeiro utilizaremos o seguinte prompt no chat:
Dado um processo de criação de uma crew de crewai.
Este consiste em criar arquivos agents.yaml, tasks.yaml e crew.py. Sendoo arquivo a
Quebre o processo em etapas, com cargos e tarefas executadas por esses cargos, para 
Ponto inicial: uma sistema de crew que gostriamos de desenvolver
Ponto final: os arquivos agents.yaml, tasks.yaml e crew.py criados
Número máximo de etapas: 6
A resposta foi a seguinte:
### **Etapa 1: Definição de Requisitos e Escopo**
- **Cargo Responsável:** **Product Owner**
- **Tarefas:**
- Definir o objetivo do sistema e as funcionalidades necessárias.
- Identificar os agentes e tarefas que o sistema precisará.
- Documentar os requisitos em alto nível para guiar o desenvolvimento.
Asimov Academy
32


---