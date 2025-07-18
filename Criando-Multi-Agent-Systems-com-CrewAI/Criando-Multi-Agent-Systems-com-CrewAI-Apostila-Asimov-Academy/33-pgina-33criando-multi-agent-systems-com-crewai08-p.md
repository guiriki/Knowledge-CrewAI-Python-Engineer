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
## Página 34

Criando Multi Agent Systems com CrewAI
---
### **Etapa 2: Design da Arquitetura e Fluxo de Trabalho**
- **Cargo Responsável:** **Arquiteto de Software**
- **Tarefas:**
- Estruturar o fluxo de interação entre agentes e tarefas.
- Definir a arquitetura do sistema para orquestração no `crew.py`.
- Planejar a organização dos arquivos `agents.yaml`, `tasks.yaml` e `crew.py`.
---
### **Etapa 3: Definição dos Agentes**
- **Cargo Responsável:** **Desenvolvedor de Agentes**
- **Tarefas:**
- Especificar os agentes no arquivo `agents.yaml`, incluindo papéis e permissões
- Definir as capacidades e limites de cada agente.
- Validar se os agentes cobrem todos os requisitos definidos.
---
### **Etapa 4: Definição das Tarefas**
- **Cargo Responsável:** **Desenvolvedor de Tarefas**
- **Tarefas:**
- Descrever as tarefas no arquivo `tasks.yaml`, incluindo entradas, saídas e cond
- Garantir que as tarefas estejam alinhadas com os agentes definidos.
- Testar cada tarefa individualmente para verificar sua funcionalidade.
---
### **Etapa 5: Orquestração e Integração**
- **Cargo Responsável:** **Desenvolvedor de Orquestração**
- **Tarefas:**
- Implementar a lógica de orquestração no `crew.py`, conectando agentes e tarefas
- Configurar o fluxo de execução entre as tarefas.
Asimov Academy
33


---