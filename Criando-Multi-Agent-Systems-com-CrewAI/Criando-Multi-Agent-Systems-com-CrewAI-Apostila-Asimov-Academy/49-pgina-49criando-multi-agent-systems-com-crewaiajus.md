## Página 49

Criando Multi Agent Systems com CrewAI
ajustar a configuração que corresponde ao novo agente ou task. Se você definiu um agent chamado
reporting_analyst no arquivo agents.yaml, basta copiaro método researcher, renomeá‑
lo e garantir que a configuração referencie self.agents_config['reporting_analyst'].
O mesmo se aplica às tasks.
E pronto! Assim, você pode configurar sua crew de forma simples e eficiente.
Arquivo main.py
Antes de começarmos, vamos ignorar as funções train, replay e test, pois não será conteúdo
deste curso. O foco será na função run(), que é crucial para a execução da sua crew.
Na função run(), o mais importante a perceber é que é ali que passamos os parâmetros necessários
para a nossa crew. Esses parâmetros são representados por um dicionário chamado inputs. No
exemplo, estamos passando um tópico ('AI
LLMs') e o ano atual, que é obtido dinamicamente
através de datetime.now().year.
Após definir os inputs, a crew é executada com o método kickoff(inputs=inputs). Esse
método inicia o processo e utiliza os dados fornecidos para orquestrar as interações entre os agents
e tasks.
Portanto, o ponto central da função run() é a passagem dos parâmetros e a execução da crew, que
são essenciais para o funcionamento da sua aplicação.
Conclusão
Nestemódulo, tivemosumavisãogeraldaestruturabaseadaemarquivosYAMLqueconfiguraanossa
aplicação com o CrewAI. Ao modificar essa estrutura para criar seu próprio projeto, o processo deve
começar pelo arquivo agents.yaml, onde definimos os agentes e suas funções. Em seguida, pas‑
samos para o arquivo tasks.yaml, onde configuramos as tarefas que cada agente executará.
Depois disso, ajustamos o arquivo crew.py para orquestrar a interação entre os agentes e tarefas,
utilizando decoradores para estabelecer a configuração da crew. Por fim, finalizamos com o arquivo
main.py, que será responsável pela execução do nosso projeto, permitindo a passagem de parâmet‑
ros e o controle do fluxo da aplicação.
Nas próximas aulas, estaremos mais envolvidos em como modificar essa estrutura, permitindo que
você crie um projeto personalizado a partir dela. Aproveite este conhecimento, pois ele será funda‑
mentalparaodesenvolvimentodesuasaplicaçõesdeinteligênciaartificialcomeficiênciaeclareza!
Asimov Academy
48


---
## Página 50

Criando Multi Agent Systems com CrewAI
10. Observabilidade com AgentOps
Quando criamos aplicações de IA, trabalhamos com muito texto, tanto na criação de prompts dos
nossos agentes quanto nas respostas que eles geram. Estes textos representam a inteligência e os
resultados da nossa aplicação, portanto, são fundamentais. A nossa capacidade de entendê‑los e
de analisá‑los vai determinar o quão rápido conseguiremos criar e depurar nossas aplicações. Mas
como podemos estabelecer uma forma fácil e prática para analisar todos os prompts utilizados no
nosso sistema, assim como as respostas dos nossos agentes e a sequência de interações entre eles,
especialmente em sistemas multiagentes? Para isso, podemos utilizar a ferramenta AgentOps, que
nos proporciona observabilidade.
O que é Observabilidade?
Observabilidade é uma abordagem que nos permite entender o comportamento de sistemas com‑
plexos, como agentes conversacionais, ao registrar e analisar dados sobre sua performance. Ela nos
permite responder questões como: Como meus agentes estão interagindo com os usuários? Como
estão utilizando ferramentas externas e APIs? Quais métricas são relevantes para avaliar a eficácia e
eficiência dos agentes?
Introduzindo o AgentOps
AgentOps é um produto independente do CrewAI que fornece uma solução abrangente de observabil‑
idade para agentes. Com o AgentOps, você tem acesso a um painel que permite monitorar o custo,
uso de tokens, latência, falhas de agentes e muito mais.
Principais Funcionalidades do AgentOps
1. Gerenciamento e Rastreamento de Custos: Monitore os gastos com provedores de modelos
fundacionais, garantindo que você esteja ciente dos custos associados ao uso de suas APIs.
2. Análises de Replay: Assista a gráficos de execução passo a passo dos agentes, permitindo que
você compreenda o fluxo de operações em detalhes.
3. Detecção de Pensamento Recursivo: Identifique quando os agentes caem em loops infinitos,
possibilitando intervenções imediatas.
4. Relatórios Personalizados: Crie análises personalizadas sobre o desempenho do agente, aju‑
stando as métricas que são mais relevantes para o seu caso de uso.
Asimov Academy
49


---