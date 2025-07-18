## Página 60

Agents de IA com Python e LangChain
11. Como um Agent é construído
Finalmente! Chegamos aos Agents! Parabéns, meus amigos e minhas amigas, por terem chegado até
aqui. Precisamos de uma base bem sólida para entender profundamente os Agents, mas agora que
estamos aqui, tudo vai fluir mais rápido. Vocês já estão familiarizados com a criação de chains, Prompt
Templates, Output Parsers e Tools, então estamos prontos para dar o próximo passo. Mas antes, vamos
fazer uma pequena definição conceitual sobre o que são os agents!
Definindo um agente
Os agentes baseados em modelos de linguagem são aplicações que podem executar tarefas complexas
utilizandoumaarquiteturaquecombinaLLMscommódulosessenciais, comoplanejamentoememória.
Em essência, um agente atua como um assistente inteligente que pode processar informações, tomar
decisões e realizar ações com base nas solicitações dos usuários.
Estrutura de um Agente
Um agente é composto por alguns componentes principais:
• Modelo LLM: Este é o “cérebro” do agente, que coordena a lógica e as ações necessárias para
responder a uma solicitação.
• Planejamento: Esse módulo ajuda o agente a decompor tarefas complexas em subtarefas mais
simples, facilitando a resolução de problemas.
• Memória: Os agentes têm a capacidade de armazenar informações sobre interações passadas,
o que os ajuda a manter o contexto e a continuidade nas conversas.
• Ferramentas: Os agentes podem utilizar ferramentas externas para realizar ações específicas,
como buscar informações em APIs ou executar comandos.
Entendendo cada componente
Modelo LLM
Este é o núcleo do agente é o componente central que gerencia a lógica e as ações necessárias para
responder a uma solicitação. Um modelo de linguagem grande (LLM) com capacidades de uso geral
serve como o “cérebro” do agente. Esse núcleo é ativado usando um template de prompt que contém
detalhes importantes sobre como o agente operará e quais ferramentas ele terá acesso.
Asimov Academy
59


---
## Página 61

Agents de IA com Python e LangChain
Embora não seja obrigatório, um agente pode ser perfilado ou receber uma persona para definir
seu papel. Essas informações de perfil geralmente são escritas no prompt e podem incluir detalhes
específicos, como informações sobre o papel, personalidade, informações sociais e outras informações
demográficas. Isso ajuda a moldar a forma como o agente interage com os usuários e como ele toma
decisões. As estratégias para definir um perfil de agente podem incluir elaboração manual, geração
por LLM ou orientada por dados.
Planejamento
O módulo de planejamento é fundamental para que o agente consiga dividir os passos necessários
ou subtarefas que ele resolverá individualmente para responder à solicitação do usuário. Essa etapa
é crucial, pois permite que o agente raciocine melhor sobre o problema e encontre uma solução de
forma confiável. O planejamento utiliza um LLM para decompor um plano detalhado que incluirá
subtarefas para ajudar a abordar a pergunta do usuário.
Memória
A memória é responsável por armazenar os registros internos do agente, incluindo pensamentos,
ações e observações passadas do ambiente, além de todas as interações entre o agente e o usuário.
Existem dois tipos principais de memória:
• Memória de Curto Prazo: Inclui informações contextuais sobre as situações atuais do agente.
Isso é tipicamente realizado por meio de aprendizado em contexto, o que significa que é curto e
finito devido a restrições de janela de contexto.
• Memória de Longo Prazo: Inclui os comportamentos e pensamentos passados do agente que
precisam ser retidos e recuperados ao longo de um período prolongado. Isso geralmente utiliza
um armazenamento vetorial externo acessível por meio de recuperação rápida e escalável para
fornecer informações relevantes para o agente conforme necessário.
A memória híbrida combina tanto a memória de curto prazo quanto a de longo prazo, melhorando a
capacidade do agente de raciocinar a longo prazo e acumular experiências.
Ferramentas
As ferramentas são um conjunto de recursos que permitem que o agente LLM interaja com ambientes
externos, como a API de busca do Wikipedia, ferramentas de busca na web ou interpretadores de
código. Elas também podem incluir bancos de dados, bases de conhecimento e modelos externos.
Quando o agente interage com ferramentas externas, ele executa tarefas por meio de fluxos de trabalho
Asimov Academy
60


---