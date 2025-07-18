## Página 59

Agents de IA com Python e LangChain
E assim fizemos um modelo capaz de escrever arquivos e lê-los em nosso pc. Incrível, não?
Espero que tenham gostado e que essas ferramentas ajudem vocês em seus projetos!
Asimov Academy
58


---
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