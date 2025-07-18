## Página 39

Criando Multi Agent Systems com CrewAI
Agora crie um arquivo yaml para as tasks, com as seguinte formatação:
nome_da_task:
description: >
Descrição aqui
expected_output: >
Saída esperada aqui
agent: agente_aqui
Lembrando que os agentes e tasks devem ter um nome em snake case
E temos a seguinte resposta:
definir_requisitos_e_escopo:
description: >
Identificar as funcionalidades necessárias para o sistema e documentar os requisitos de
forma clara.
↪
expected_output: >
Documento de requisitos detalhado, alinhado com as expectativas dos stakeholders.
agent: product_owner
especificar_agentes:
description: >
Definir os agentes no agents.yaml, incluindo seus papéis e permissões dentro do sistema.
expected_output: >
Arquivo agents.yaml completo, com agentes especificados e documentados.
agent: desenvolvedor_de_agentes
definir_tarefas:
description: >
Criar o tasks.yaml, descrevendo as ações necessárias para cada task, incluindo entradas e
saídas.
↪
expected_output: >
Arquivo tasks.yaml estruturado com tasks claras e detalhadas.
agent: desenvolvedor_de_tarefas
orquestrar_agentes_e_tarefas:
description: >
Implementar o crew.py conectando agentes e tasks, configurando o fluxo de execução.
expected_output: >
Arquivo crew.py funcional, com integração completa entre agents.yaml e tasks.yaml.
agent: desenvolvedor_de_orquestracao
Refinando as expected_output’s
Paraauxiliarosagentesaproduzirsaídasválidas, éimportantedarexemplosdecomoqueremosestas
saídas. Podemos adicioanr as formatações esperadas nas tasks especificar_agentes, definir_tarefas
Asimov Academy
38


---
## Página 40

Criando Multi Agent Systems com CrewAI
e orquestrar_agentes_e_tarefas, da seguinte forma:
definir_requisitos_e_escopo:
description: >
Identificar as funcionalidades necessárias para o sistema e documentar os requis
expected_output: >
Documento de requisitos detalhado, alinhado com as expectativas dos stakeholders
agent: product_owner
especificar_agentes:
description: >
Definir os agentes no agents.yaml, incluindo seus papéis e permissões dentro do s
expected_output: >
Arquivo agents.yaml completo, com agentes especificados e documentados.
O formato é o seguinte:
nome_do_agente:
role: >
Descreve a função e a especialização do agente dentro da equipe. Aqui você defi
goal: >
O objetivo individual que guia a tomada de decisões do agente. Este campo defin
backstory: >
Contextualiza o agente, fornecendo informações sobre sua personalidade, exper
nome_do_agente_2:
...
agent: desenvolvedor_de_agentes
definir_tarefas:
description: >
Criar o tasks.yaml, descrevendo as ações necessárias para cada task, incluindo en
expected_output: >
Arquivo tasks.yaml estruturado com tasks claras e detalhadas.
O formato é o seguinte:
nome_da_task:
description: >
Uma declaração clara e concisa sobre o que a tarefa envole. Este campo deve esp
expected_output: >
Uma descrição detalhada do que a conclusão da tarefa deve produzir. O que se es
agent: nome_do_agente (nome conforme arquivo de agentes)
Asimov Academy
39


---