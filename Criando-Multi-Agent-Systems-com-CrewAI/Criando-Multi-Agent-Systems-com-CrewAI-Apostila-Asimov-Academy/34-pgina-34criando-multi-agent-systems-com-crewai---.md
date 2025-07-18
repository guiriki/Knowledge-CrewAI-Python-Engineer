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
## Página 35

Criando Multi Agent Systems com CrewAI
- Realizar testes integrados para garantir a funcionalidade do sistema.
---
### **Etapa 6: Testes Finais e Documentação**
- **Cargo Responsável:** **QA e Documentação**
- **Tarefas:**
- Executar testes de ponta a ponta para validar o sistema.
- Documentar o funcionamento do `agents.yaml`, `tasks.yaml` e `crew.py`.
- Reunir feedback e ajustar detalhes conforme necessário.
---
Destes, ficaremos com os agentes 1, 3, 4, e 5.
Vamos continuar com o seguinte prompt:
Mantenha os agentes 1, 3, 4 e 5 para o sistema final e descreva o sistema como agents 
- Cada cargo representa um agente
- Cada agente é descrevido por três argumentos:
- role: Descreve a função do agent dentro do sistema, indicando qual tarefa ele es
- goal: Define o objetivo principal do agent, ou seja, o que se espera que ele alc
- backstory: Fornece um contexto que ajuda a moldar a personalidade e a abordagem 
- Cada task é descrita por três argumentos:
- description: Orienta sobre o que a task deve realizar, detalhando as ações espe
- expected_output: Descreve o resultado esperado da task, que é utilizado para va
- agent: Indica qual agent é responsável pela execução da task.
E temos a seguinte resposta:
---
## **Agents (Cargos)**
### **Agent 1: Product Owner**
- **role:** Definir os requisitos e o escopo do sistema, alinhando as expectativas d
Asimov Academy
34


---