## Página 8

Agents de IA com Python e LangChain
02. Criando uma chain com LCEL
Neste capítulo, vamos entender o que é o LangChain Expression Language (LCEL) e como utilizá-lo
para criação de chains.
O que é LCEL?
A LangChain Expression Language, ou LCEL, é uma forma declarativa e intuitiva de compor chains, de
maneira fácil e escalável. A LCEL foi criada para facilitar a vida dos desenvolvedores, permitindo que
protótipos sejam rapidamente colocados em produção, desde a cadeia mais simples “prompt + LLM”
até as cadeias mais complexas (com centenas de etapas).
Principais Características da LCEL
• Suporte a Streaming: Isso significa que você pode começar a receber resultados assim que o
primeiro token é produzido, sem esperar pelo processamento completo.
• Execução Paralela: Se sua chain tem etapas que podem ser executadas simultaneamente, a
LCEL cuida disso automaticamente.
• Fallbacks e Retentativas: Em caso de erros, você pode definir ações alternativas para garantir a
confiabilidade de suas chains.
• Acesso a Resultados Intermediários: Essencial para depuração, permitindo que você entenda
e refine cada etapa da sua chain.
Criando sua Primeira Chain com LCEL
Vamos começar com um exemplo simples para entender como tudo funciona. Primeiro, precisamos
configurar nosso ambiente e importar as bibliotecas necessárias:
from dotenv import load_dotenv, find_dotenv
_ = load_dotenv(find_dotenv())
from langchain_openai import ChatOpenAI
model = ChatOpenAI(model='gpt-3.5-turbo-0125')
Vamos criar a cadeia mais simples possível, composta de um prompt combinado a um modelo de
linguagem. Para isso, importamos o promptTemplate:
from langchain_core.prompts import ChatPromptTemplate
prompt = ChatPromptTemplate.from_template('Crie uma frase sobre o seguinte: {assunto}')
Asimov Academy
7


---
## Página 9

Agents de IA com Python e LangChain
Agora, vamos compor nossa chain. A beleza da LCEL está na simplicidade com que podemos encadear
diferentes componentes:
chain = prompt | model
Para invocar a chain com um exemplo prático, vamos usar:
response = chain.invoke({'assunto': 'gatinhos'})
print(response)
AIMessage(content='Os gatinhos são seres adoráveis que conseguem conquistar nossos corações
com seu charme e fofura.', response_metadata={'token_usage': {'completion_tokens': 28,
'prompt_tokens': 19, 'total_tokens': 47}, 'model_name': 'gpt-3.5-turbo-0125',
'system_fingerprint': None, 'finish_reason': 'stop', 'logprobs': None},
id='run-b9e445f5-5ba9-4aea-9813-eda76880def5-0')
�→
�→
�→
�→
Adicionando mais elementos à chain
Suponha que queremos apenas o texto da resposta, sem metadados adicionais. Podemos adicionar
um output_parser à nossa chain:
from langchain_core.output_parsers import StrOutputParser
output_parser = StrOutputParser()
chain = prompt | model | output_parser
print(chain.invoke({'assunto': 'gatinhos'}))
'"Gatinhos são fofos, brincalhões e cheios de amor para dar."'
E veja como é simples ir compondo nossa chain e adicionando novos elementos. Pense que após esta
chain, poderíamos adicionar um novo prompt que pega a resposta produzida após o output parser e
processa ele novamente, para gerar uma nova resposta e assim por diante.
Atenção: A ordem importa!
É crucial que os componentes da chain sejam organizados na ordem correta para que os dados fluam
corretamente de um estágio para o outro. Por exemplo, inverter a ordem resultará em erro, pois cada
componente espera um tipo específico de entrada.
chain = model | prompt | output_parser #ORDEM INCORRETA!
chain.invoke({'assunto': 'gatinhos'}) #Invoke retornará um erro
Entendendo a ordem correta
Para garantir que você não cometa erros, é importante entender o tipo de entrada e saída de cada
componente:
Asimov Academy
8


---