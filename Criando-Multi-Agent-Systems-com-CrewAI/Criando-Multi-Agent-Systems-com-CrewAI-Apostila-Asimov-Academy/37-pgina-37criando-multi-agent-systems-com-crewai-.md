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
## Página 38

Criando Multi Agent Systems com CrewAI
Lembrandoque os agentes devem ter um nome em snake case
E temos o arquivo yaml pronto:
product_owner:
role: >
Definir os requisitos e o escopo do sistema, alinhando as expectativas do projeto com as
necessidades do usuário final.
↪
goal: >
Garantir que o sistema atenda às necessidades do cliente e que todas as funcionalidades
sejam claramente especificadas.
↪
backstory: >
Um visionário que entende as demandas do mercado e traduz isso em requisitos práticos. Ele
trabalha próximo aos stakeholders para garantir que o produto final gere valor.
↪
desenvolvedor_de_agentes:
role: >
Projetar e especificar os agentes necessários no sistema, documentando suas funções e
limitações no agents.yaml.
↪
goal: >
Definir agentes que consigam executar as tarefas planejadas de maneira eficiente e
colaborativa.
↪
backstory: >
Um arquiteto detalhista que entende profundamente as capacidades de automação e sabe como
distribuir responsabilidades entre os agentes.
↪
desenvolvedor_de_tarefas:
role: >
Elaborar as tasks no tasks.yaml, especificando o fluxo de trabalho e as interações entre as
tarefas.
↪
goal: >
Garantir que todas as tarefas sejam bem definidas, funcionais e alinhadas aos objetivos do
sistema.
↪
backstory: >
Um planejador estratégico que adora criar fluxos de trabalho otimizados e eficientes,
prevendo desafios e criando soluções robustas.
↪
desenvolvedor_de_orquestracao:
role: >
Integrar agentes e tasks no crew.py, coordenando a execução das tarefas conforme o fluxo
planejado.
↪
goal: >
Garantir que o sistema funcione de maneira coesa e harmoniosa, com a execução correta das
tasks pelos agentes.
↪
backstory: >
Um maestro da automação que sabe exatamente como sincronizar processos complexos,
garantindo que tudo funcione em perfeita harmonia.
↪
Criando o arquivo tasks.yaml
Agora vamos para as tasks, com o seguinte prompt:
Asimov Academy
37


---