## Página 25

Criando Multi Agent Systems com CrewAI
Classe
Parâmetro
Agent
role
goal
backstory
Task
description
agent
expected_output
Todos estes são textos que utilizamos para descrever nosso agent e nossa crew, e podemos aproveitar
o Chat para nos ajudar a criá‑los. Por exemplo, posso usar a seguinte solicitação:
Agora descreva o sistema como agents e tasks, da seguinte forma:
- Cada cargo representa um agente
- Cada agente é descrito por três argumentos:
- role: Descreve a função do agent dentro do sistema, indicando qual tarefa ele es
- goal: Define o objetivo principal do agent, ou seja, o que se espera que ele alc
- backstory: Fornece um contexto que ajuda a moldar a personalidade e a abordagem 
- Cada task é descrita por três argumentos:
- description: Orienta sobre o que a task deve realizar, detalhando as ações espe
- expected_output: Descreve o resultado esperado da task, que é utilizado para va
- agent: Indica qual agent é responsável pela execução da task.
E temos a seguinte resposta:
1. **Estrategista de Conteúdo**
- **role:** Definir a estratégia e elaborar o briefing do artigo.
- **goal:** Criar um briefing robusto que inclua objetivos, público-alvo, direci
- **backstory:** Experiente em marketing de conteúdo, analisa temas e direciona e
2. **Editor de Conteúdo**
- **role:** Planejar e estruturar o conteúdo do artigo.
- **goal:** Organizar as ideias em um outline claro e lógico, definindo seções, t
- **backstory:** Com vasta experiência em edição, atua como elo entre a estratégi
Asimov Academy
24


---
## Página 26

Criando Multi Agent Systems com CrewAI
3. **Redator de Conteúdo**
- **role:** Produzir o rascunho inicial do artigo.
- **goal:** Transformar o briefing e o outline em um texto coeso, engajador e info
- **backstory:** Apaixonado pela escrita, tem habilidade para traduzir ideias co
4. **Revisor de Texto**
- **role:** Revisar e aperfeiçoar o artigo.
- **goal:** Garantir que o texto esteja livre de erros gramaticais e ortográficos
- **backstory:** Detalhista e rigoroso, possui profundo conhecimento em gramátic
5. **Gestor de Conteúdo**
- **role:** Validar e aprovar o artigo para publicação.
- **goal:** Assegurar que o artigo final esteja alinhado com os objetivos estraté
- **backstory:** Com visão holística do processo de criação, coordena a entrega d
---
## **Tasks**
1. **Task 1 – Elaborar Briefing e Pesquisa**
- **description:** Definir o tema, identificar o público-alvo, estabelecer objet
- **expected_output:** Documento de briefing completo, contendo objetivos claros
- **agent:** Estrategista de Conteúdo
7. **Task 2 – Estruturar o Conteúdo**
- **description:** Criar um outline que organize os tópicos e seções do artigo, d
- **expected_output:** Outline detalhado e organizado do artigo.
- **agent:** Editor de Conteúdo
8. **Task 3 – Redação do Artigo**
- **description:** Produzir o rascunho inicial do artigo com base no briefing e n
- **expected_output:** Rascunho completo e coerente do artigo, com narrativa flu
- **agent:** Redator de Conteúdo
9. **Task 4 – Revisar e Editar o Texto**
- **description:** Revisar o artigo para corrigir erros gramaticais, ortográfico
Asimov Academy
25


---