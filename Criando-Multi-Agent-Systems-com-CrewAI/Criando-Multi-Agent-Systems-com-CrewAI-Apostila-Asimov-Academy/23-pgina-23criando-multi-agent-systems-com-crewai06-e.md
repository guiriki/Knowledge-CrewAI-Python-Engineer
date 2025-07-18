## Página 23

Criando Multi Agent Systems com CrewAI
06. Estruturado Agents e Tasks com ajuda do ChatGPT
Muitos processos são simples de modularizar, principalmente aqueles que já conhecemos bem.
Agora, quando temos um processo novo, que ainda não pensamos profundamente sobre, sempre
podemos utilizar o ChatGPT para auxiliar no processo de modularização.
Vamos ver isto especificamente nesta aula!
Prompt 1: Descrevendo o processo
Pegando novamente nosso exemplo de escrita de um post de blog, posso solicitar o seguinte:
Dado um processo de criação de um artigo de blog
Quebre o processo em etapas, com cargos e tarefas executadas por esses cargos, para 
Ponto inicial: o tema do conteúdo do post que será definido pelo usuário
Ponto final: texto pronto e revisado
Número máximo de etapas: 5
E resposta que ele me deu é a seguinte:
### **Etapa 1: Briefing e Pesquisa**
- **Cargo Principal:** Estrategista de Conteúdo
- **Cargos de Apoio:** Pesquisador / Analista de SEO
- **Tarefas:**
- **Definição de Objetivos:** Entender o propósito do artigo, público-alvo e os r
- **Levantamento de Informações:** Coletar dados, estatísticas e referências rel
- **Pesquisa de Palavras-Chave:** Identificar termos e tendências para orientar 
- **Elaboração do Briefing:** Documentar todos os insights e direcionamentos par
### **Etapa 2: Planejamento e Estruturação do Conteúdo**
- **Cargo Principal:** Editor de Conteúdo
- **Cargos de Apoio:** Redator Sênior / Copywriter
Asimov Academy
22


---
## Página 24

Criando Multi Agent Systems com CrewAI
- **Tarefas:**
- **Criação do Outline (Roteiro):** Definir a estrutura do artigo, com tópicos e 
- **Definição do Tom e Estilo:** Estabelecer a voz do texto e os elementos que dev
- **Organização das Ideias:** Distribuir o conteúdo de forma lógica, alinhada com
### **Etapa 3: Redação do Artigo**
- **Cargo Principal:** Redator de Conteúdo
- **Tarefas:**
- **Produção do Rascunho Inicial:** Escrever o artigo seguindo o outline, integra
- **Desenvolvimento da Narrativa:** Garantir coerência, fluidez e engajamento, a
- **Incorporação de Chamadas para Ação (CTAs):** Inserir elementos que incentive
### **Etapa 4: Revisão e Edição**
- **Cargo Principal:** Revisor de Texto / Editor
- **Tarefas:**
- **Revisão Ortográfica e Gramatical:** Corrigir erros de digitação, gramática e
- **Ajustes de Coerência e Coesão:** Verificar a fluidez do texto, melhorar a est
- **Verificação de SEO e Consistência de Estilo:** Confirmar que o texto atende à
- **Feedback e Ajustes:** Se necessário, retornar o conteúdo ao redator para adeq
### **Etapa 5: Aprovação Final e Entrega**
- **Cargo Principal:** Gestor de Conteúdo / Editor Final
- **Tarefas:**
- **Validação do Conteúdo:** Conferir se todas as etapas anteriores foram cumprid
- **Integração de Feedbacks:** Realizar os últimos ajustes com base nas sugestões
- **Preparação para Publicação:** Formatar o texto de acordo com as diretrizes da
Perfeito! Agora temos uma ótima base para a criação de agents e tasks a partir do que o ChatGPT nos
indicou!
Prompt 2: Utilizando o Chat para criar Agents e Tasks
Além disso, podemos ir além e utilizar o chat para criar os argumentos necessários para a criação dos
nossos agents e tasks. Se vocês lembrarem, temos os seguintes parâmetros:
Asimov Academy
23


---