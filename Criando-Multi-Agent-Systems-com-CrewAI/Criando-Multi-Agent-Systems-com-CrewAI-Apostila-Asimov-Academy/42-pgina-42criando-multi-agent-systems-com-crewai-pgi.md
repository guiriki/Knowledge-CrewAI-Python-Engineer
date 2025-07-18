## Página 42

Criando Multi Agent Systems com CrewAI
@task
def nome_da_primeira_task(self) -> Task:
return Task(
config=self.tasks_config['nome_da_primeira_task'],
)
@task
def nome_da_primeira_task(self) -> Task:
return Task(
config=self.tasks_config['revisa_arquivo_yaml_agentes'],
)
@task
def nome_da_segunda_task(self) -> Task:
return Task(
config=self.tasks_config['nome_da_segunda_task'],
)
@crew
def crew(self) -> Crew:
return Crew(
agents=self.agents,
tasks=self.tasks,
verbose=True,
)
```
agent: desenvolvedor_de_orquestracao
E já temos a base dono nosso projeto. Na próxima aula vamos testá‑lo e colocá‑lo para rodar!
Até lá!
Asimov Academy
41


---
## Página 43

Criando Multi Agent Systems com CrewAI
09. Projeto ‑ Refinando a crew para criar crews
Bem‑vindos de volta, pessoal! Finalizamos agora os elementos básicos de CrewAI e já vamos começar
a pensar na criação de estruturas para produção. Pois nosso objetivo é criar soluções que realmente
serão utilizadas; então, quando quisermos oferecê‑las ao mundo, elas precisam estar prontas!
Para facilitar este processo, a CrewAI criou recentemente uma nova estrutura de construção de uma
Crew, baseada em arquivos YAML. De início, isso pode assustar um pouco, pois há uma complexidade
maior na forma como os arquivos são organizados. Porém, eles são mais limpos, modularizados e
facilitam a manutenção do projeto.
Iniciando um projeto
ComoCrewAIinstaladonoseuambiente, vocêganhaacessoaalgunscomandoscriadosnabiblioteca.
Vamos utilizar o comando create para iniciar um novo projeto. Para isso, abra um terminal e digite:
crewai create crew projeto_teste
No exemplo, demos o nome do projeto como projeto_teste, mas você pode modificar para um
nome que faça sentido para a sua aplicação.
Primeiro, será solicitado que você selecione o provedor de modelos que será utilizado no seu projeto,
e você perceberá que temos diversas opções no caso do CrewAI:
Asimov Academy
42


---