## Página 12

Criando Multi Agent Systems com CrewAI
Figure 1: Estrutura da Crew
Asimov Academy
11


---
## Página 13

Criando Multi Agent Systems com CrewAI
Esses agents terão as seguintes tasks:
• Desenvolvedor de Ideias
– Criar Ideias: Gera uma lista com 10 ideias criativas e relevantes para posts de blog sobre
um tema específico, assegurando a diversidade nas sugestões.
– Selecionar Ideias: Analisa a lista de ideias geradas e seleciona a melhor, justificando a
escolha com base na relevância e no alinhamento com os objetivos do blog.
• Planejador de Conteúdo
– Planejar Conteúdo: Cria um briefing detalhado, incluindo informações essenciais como
objetivo, público‑alvo, tom de voz, palavras‑chave e formato do post.
• Escritor do Post
– Escrever Post: Redige o conteúdo completo do post de blog, seguindo as diretrizes do
briefing e a ideia selecionada, garantindo que o texto seja envolvente e bem estruturado.
• Revisor do Post
– Revisar Post: Revê o post de blog, corrigindo erros gramaticais e de pontuação, e melho‑
rando a fluidez do texto, garantindo que o conteúdo esteja alinhado com o briefing.
Agora, vamos passo a passo criando a aplicação!
Configuração do Ambiente
Vamos iniciar importando as bibliotecas necessárias, carregando as variáveis de ambiente e impor‑
tando os elementos essenciais da biblioteca CrewAI:
from dotenv import load_dotenv, find_dotenv
_ = load_dotenv(find_dotenv())
from crewai import Crew, Process, Agent, Task
Observação: A variável de ambiente carrega o arquivo .env, que deve estar junto ao projeto. Nele,
devemos guardar uma variável chamada OPENAI_API_KEY com a chave da API da OpenAI. Desta
forma, estaremos executando a Crew através da OpenAI.
Criação dos Agents
Vamos à criação dos agents. Cada agent é definido com parâmetros essenciais como role, goal,
backstory e verbose. Esses parâmetros determinam a função do agent no sistema.
Asimov Academy
12


---