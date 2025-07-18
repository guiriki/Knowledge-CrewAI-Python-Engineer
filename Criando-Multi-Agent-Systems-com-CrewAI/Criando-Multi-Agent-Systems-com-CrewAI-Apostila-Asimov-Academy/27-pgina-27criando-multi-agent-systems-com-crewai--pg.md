## Página 27

Criando Multi Agent Systems com CrewAI
- **expected_output:** Versão do artigo revisada e otimizada, sem erros e com flu
- **agent:** Revisor de Texto
10. **Task 5 – Aprovar e Preparar para Publicação**
- **description:** Validar o artigo final, integrar feedbacks e realizar os ajust
- **expected_output:** Artigo final aprovado, formatado e pronto para ser public
- **agent:** Gestor de Conteúdo
Perfeito, assim nossa estrutura de CrewAI já está perfeitamente construída! Muito incrível!
Na próxima aula, vamos explorar formas um pouco mais complexas e, consequentemente, mais
poderosas de criação de crews: as estruturas YAML!
Asimov Academy
26


---
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