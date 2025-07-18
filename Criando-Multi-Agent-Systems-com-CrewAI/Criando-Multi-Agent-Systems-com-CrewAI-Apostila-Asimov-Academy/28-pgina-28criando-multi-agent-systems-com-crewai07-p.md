## Página 28

Criando Multi Agent Systems com CrewAI
07. Projeto finalizado ‑ Criando uma crew para criar crews
Após alguns ajustes no projeto, chagamos aos seguintes arquivos:
agents.yaml
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
Asimov Academy
27


---
## Página 29

Criando Multi Agent Systems com CrewAI
tasks.yaml
definir_requisitos_e_escopo:
description: >
Identificar as funcionalidades necessárias para o sistema e documentar os requisitos de
forma clara.
↪
Sistema solicitado: {especificacoes_sistema}
expected_output: >
Documento de requisitos detalhado, alinhado com as expectativas dos stakeholders.
agent: product_owner
especificar_agentes:
description: >
Definir os agentes no agents.yaml, incluindo seus papéis e permissões dentro do sistema.
Sistema solicitado: {especificacoes_sistema}
expected_output: >
Arquivo agents.yaml completo, com agentes especificados e documentados.
O formato é o seguinte:
nome_do_agente:
role: >
Descreve a função e a especialização do agente dentro da equipe. Aqui você define o
papel do agente e sua expertise na aplicação.
↪
goal: >
O objetivo individual que guia a tomada de decisões do agente. Este campo define o que o
agente busca alcançar com suas ações.
↪
backstory: >
Contextualiza o agente, fornecendo informações sobre sua personalidade, experiência e
como ele se relaciona com o restante da equipe.
↪
nome_do_agente_2:
...
Retorne apenas o arquivo solicitado!
agent: desenvolvedor_de_agentes
definir_tarefas:
description: >
Criar o tasks.yaml, descrevendo as ações necessárias para cada task, incluindo entradas e
saídas.
↪
Sistema solicitado: {especificacoes_sistema}
expected_output: >
Arquivo tasks.yaml estruturado com tasks claras e detalhadas.
O formato é o seguinte:
nome_da_task:
description: >
Uma declaração clara e concisa sobre o que a tarefa envole. Este campo deve especificar
exatamente o que o agente precisa fazer para completar a tarefa. Ele não deve descrever o
agente, e sim a task que ele executará.
↪
↪
expected_output: >
Uma descrição detalhada do que a conclusão da tarefa deve produzir. O que se espera como
resultado final após a tarefa ser executada.
↪
agent: nome_do_agente (nome conforme arquivo de agentes)
nome_da_task_2:
...
Retorne apenas o arquivo solicitado!
agent: desenvolvedor_de_tarefas
Asimov Academy
28


---