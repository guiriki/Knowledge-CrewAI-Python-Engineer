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
## Página 37

Criando Multi Agent Systems com CrewAI
### **Task 2: Especificar Agentes**
- **description:** Definir os agentes no `agents.yaml`, incluindo seus papéis e per
- **expected_output:** Arquivo `agents.yaml` completo, com agentes especificados e 
- **agent:** **Desenvolvedor de Agentes**
---
### **Task 3: Definir Tarefas**
- **description:** Criar o `tasks.yaml`, descrevendo as ações necessárias para cada
- **expected_output:** Arquivo `tasks.yaml` estruturado com tasks claras e detalhad
- **agent:** **Desenvolvedor de Tarefas**
---
### **Task 4: Orquestrar Agentes e Tarefas**
- **description:** Implementar o `crew.py` conectando agentes e tasks, configurando
- **expected_output:** Arquivo `crew.py` funcional, com integração completa entre `
- **agent:** **Desenvolvedor de Orquestração**
---
Criando o arquivo agents.yaml
Agora vamos criar o arquivo yaml com o seguinte prompt:
Agora crie um arquivo yaml para os agentes, com as seguinte formatação:
nome_do_agente:
role: >
Role aqui
goal: >
Goal aqui
backstory: >
Backstory aqui
Asimov Academy
36


---