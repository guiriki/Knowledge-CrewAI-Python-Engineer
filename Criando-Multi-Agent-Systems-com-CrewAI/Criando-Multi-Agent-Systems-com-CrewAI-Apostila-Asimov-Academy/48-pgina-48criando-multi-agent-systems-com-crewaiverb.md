## Página 48

Criando Multi Agent Systems com CrewAI
verbose=True,
)
Você pode nunca ter se deparado com uma estrutura como a classe ProjetoTeste em Python, mas
é bem simples! Essa classe foi criada para unificar a configuração da sua crew, e você verá que não
precisará modificá‑la drasticamente.
Além das classes, temos decoradores, aquela palavras com um @ na frente. Estes decoradores tam‑
bém são padrão da bibliotecas mas de super fácil utilização!
E para tudo ficar bem claro, vou deixar uma breve explicação de o que é classe e decoradores para
quem não tem familiaridade com esses termos.
O que é uma classe?
Em Python, uma classe é como um molde que define um tipo de objeto. Dentro de uma classe, pode‑
mos definir propriedades (dados) e métodos (funções) que descrevem o comportamento desse ob‑
jeto. No caso da classe ProjetoTeste, estamos definindo como criar e gerenciar uma crew de
agentes e tarefas.
O que são decoradores?
Em termos simples, decoradores são uma forma de modificar o comportamento de uma função,
método ou classe sem alterar seu código interno. No contexto da nossa classe ProjetoTeste,
usamos decoradores para marcar quais métodos se tornarão agents, tasks e o método que define a
crew.
Por exemplo, ao criar o agente researcher, usamos o decorador @agent antes da definição
do método. Isso indica que o método subsequente será um agent. Dentro do método, simples‑
mente referenciamos o nome do agente, conforme definido no arquivo agents.yaml, utilizando
self.agents_config['researcher']. Isso garante que todas as configurações do agente
sejam carregadas automaticamente a partir do arquivo YAML.
O processo para definir as tasks é bastante semelhante. Neste caso, usamos o decorador @task,
e assim como fizemos com os agents, configuramos o método para apontar para a variável
tasks_config, onde estão definidas as tasks no arquivo tasks.yaml.
Agora, é importante notar que você precisará criar um número de métodos equivalente à quanti‑
dade de agents e tasks que a crew terá. Não se preocupe! Você pode facilmente fazer cópias dos
métodos existentes, alterar o nome (por exemplo, de researcher para reporting_analyst) e
Asimov Academy
47


---
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