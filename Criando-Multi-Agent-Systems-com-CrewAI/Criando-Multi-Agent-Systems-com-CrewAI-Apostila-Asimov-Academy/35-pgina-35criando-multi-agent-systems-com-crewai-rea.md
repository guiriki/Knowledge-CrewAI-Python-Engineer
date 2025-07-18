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
## Página 36

Criando Multi Agent Systems com CrewAI
- **goal:** Garantir que o sistema atenda às necessidades do cliente e que todas as f
- **backstory:** Um visionário que entende as demandas do mercado e traduz isso em r
---
### **Agent 3: Desenvolvedor de Agentes**
- **role:** Projetar e especificar os agentes necessários no sistema, documentando 
- **goal:** Definir agentes que consigam executar as tarefas planejadas de maneira e
- **backstory:** Um arquiteto detalhista que entende profundamente as capacidades d
---
### **Agent 4: Desenvolvedor de Tarefas**
- **role:** Elaborar as tasks no `tasks.yaml`, especificando o fluxo de trabalho e a
- **goal:** Garantir que todas as tarefas sejam bem definidas, funcionais e alinhada
- **backstory:** Um planejador estratégico que adora criar fluxos de trabalho otimi
---
### **Agent 5: Desenvolvedor de Orquestração**
- **role:** Integrar agentes e tasks no `crew.py`, coordenando a execução das tarefa
- **goal:** Garantir que o sistema funcione de maneira coesa e harmoniosa, com a exe
- **backstory:** Um maestro da automação que sabe exatamente como sincronizar proce
---
## **Tasks**
### **Task 1: Definir Requisitos e Escopo**
- **description:** Identificar as funcionalidades necessárias para o sistema e docu
- **expected_output:** Documento de requisitos detalhado, alinhado com as expectati
- **agent:** **Product Owner**
---
Asimov Academy
35


---