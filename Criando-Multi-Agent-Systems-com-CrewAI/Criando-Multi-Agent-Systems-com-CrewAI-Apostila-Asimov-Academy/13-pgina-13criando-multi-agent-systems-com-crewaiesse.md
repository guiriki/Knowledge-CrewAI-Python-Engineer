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
## Página 14

Criando Multi Agent Systems com CrewAI
O parâmetro role descreve a função do agent, enquanto goal e backstory detalham o objetivo
e o contexto do agent. O parâmetro verbose, quando definido como True, permite que o agent
registre informações detalhadas durante sua execução.
Aqui está o trecho de código para a criação dos agents:
desenvolvedor_de_ideais = Agent(
role='Criador de Ideias Criativas para Blog Posts',
goal='Gerar ideias originais e relevantes para posts de blog dentro de um tema específico',
backstory='Você é um criador criativo, sempre antenado nas últimas tendências e com uma
habilidade impressionante para transformar conceitos em ideias inovadoras. Sua curiosidade
e energia o ajudam a criar sugestões únicas que atraem o público-alvo de forma eficaz.',
↪
↪
verbose=True
)
planejador_de_conteudo = Agent(
role='Estrategista de Conteúdo para Blogs',
goal='Planejar e estruturar o conteúdo de maneira eficaz, com base no briefing fornecido',
backstory='Você é um estrategista detalhista, apaixonado por alinhar objetivos e dados com a
criação de conteúdo. Você adora criar planos bem estruturados que orientam os redatores
para alcançar os melhores resultados. Seu foco está sempre em garantir que o conteúdo
atenda às expectativas do público e aos objetivos de marketing.',
↪
↪
↪
verbose=True
)
escritor_do_post = Agent(
role='Redator Criativo de Blog Posts',
goal='Escrever posts de blog envolventes e de alta qualidade, seguindo o briefing e as
diretrizes definidas',
↪
backstory='Você é um escritor versátil, capaz de adaptar seu estilo de escrita ao tom e ao
formato desejado. Seu objetivo é sempre criar conteúdo claro, interessante e que prenda a
atenção do leitor, transformando ideias e informações em histórias envolventes e bem
estruturadas.',
↪
↪
↪
verbose=True
)
revisor_do_post = Agent(
role='Revisor de Conteúdo de Blog Posts',
goal='Garantir que o post esteja livre de erros e pronto para ser publicado',
backstory='Você é um revisor minucioso e atento aos detalhes. Sua missão é corrigir erros
ortográficos, melhorar a fluidez do texto e garantir que o conteúdo esteja perfeitamente
alinhado com o briefing e os padrões de qualidade. Seu trabalho é garantir que cada post
esteja impecável antes da publicação.',
↪
↪
↪
verbose=True
)
Definição das Tasks
Após a criação dos agents, passamos para as tasks, que representam as atividades que cada agent
deve executar. Cada task é composta por uma description que orienta o que deve ser feito e um
expected_output que descreve o resultado esperado, ajudando a validar a execução.
Asimov Academy
13


---