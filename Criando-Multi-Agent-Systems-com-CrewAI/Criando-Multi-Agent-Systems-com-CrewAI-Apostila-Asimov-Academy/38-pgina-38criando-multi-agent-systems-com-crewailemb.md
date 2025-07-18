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