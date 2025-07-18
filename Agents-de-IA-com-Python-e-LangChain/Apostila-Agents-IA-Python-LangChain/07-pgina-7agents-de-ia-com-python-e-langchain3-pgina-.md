## Página 7

Agents de IA com Python e LangChain
3) Criação de Tools
As tools, ou ferramentas, são o passo dois das funções. No momento que o modelo consegue recon-
hecer que existe uma função externa que ele pode utilizar, podemos de fato utilizá-la, executá-la e
oferecer as obersvações que a ferramenta gera ao modelo. As tools são os grandes diferenciais dos
Agents, quanto melhores as ferramentas, melhor o Agent!
4) Criação de Agents
A última etapa é de finalmente a criação de agents. Juntamos todos os conhecimentos obtidos nos
módulos iniciias e entendemos o que é um agent, como construí-los manulamente e como criar
agents avançados, como um agent que analisa bancos de dados SQL e agents que analisam dados de
DataFrames!
Pré-requisitos para o curso
E é importante ressaltar que será necessário um conhecimento básico de LangChain para compreender
este curso. Então, caso você ainda não tenha feito nosso curso introdutório de Aplicações de IA com
LangChain, pare agora, assiste ele com calma e depois volte para cá. Caso contrário, então já pode
começar agora a explorar o incrível potencial dos agents!
E agora, sem mais delongas, vamos para nosso curso!
Asimov Academy
6


---
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