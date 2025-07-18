## Página 10

Agents de IA com Python e LangChain
• Prompt: Recebe um dicionário e retorna um PromptValue.
• Model (ChatModel): Recebe uma string, uma lista de mensagens de chat ou um PromptValue
e retorna uma ChatMessage.
• OutputParser: Recebe a saída de um LLM ou ChatModel e retorna um tipo de dado específico,
dependendo do parser.
Este é um esquema geral dos principais componentes do LangChain e os tipos de entada e saída que
eles suportam:
Component
Tipo de Entrada
Tipo de Saída
Prompt
Dicionário
PromptValue
ChatModel
String única, lista de mensagens de chat ou
PromptValue
Mensagem de Chat
LLM
String única, lista de mensagens de chat ou
PromptValue
String
OutputParser
A saída de um LLM ou ChatModel
Depende do parser
Retriever
String única
Lista de Documentos
Tool
String única ou dicionário, dependendo da ferramenta
Depende da
ferramenta
Você pode também verificar os tipos de entrada e saída utilizando os métodos input_schema e out-
put_schema:
print(prompt.input_schema.schema_json(indent=4))
{
"title": "PromptInput",
"type": "object",
"properties": {
"assunto": {
"title": "Assunto",
"type": "string"
}
}
}
Chains Clássicas vs. LCEL
Antes da LCEL, criar chains era mais complexo e menos intuitivo. Veja como seria com a abordagem
clássica:
Asimov Academy
9


---
## Página 11

Agents de IA com Python e LangChain
from langchain.chains.llm import LLMChain
from langchain_openai.chat_models import ChatOpenAI
from langchain_core.output_parsers import StrOutputParser
from langchain_core.prompts import ChatPromptTemplate
model = ChatOpenAI(model="gpt-3.5-turbo")
prompt = ChatPromptTemplate.from_template("Crie uma frase sobre o assunto: {assunto}")
output_parser = StrOutputParser()
chain = LLMChain(llm=model, prompt=prompt, output_parser=output_parser)
print(chain.invoke({'assunto': 'gatinhos'}))
Como você pode ver, a LCEL simplifica significativamente o processo de criação de chains, tornando
seu código mais limpo e fácil de entender.
Métodos de um Runnable
Agora vamos explorar mais a fundo os métodos dos Runnables de LCEL, que são essenciais para a
utilização das chains que agora sabemos criar. Vamos entender como esses métodos funcionam e
como você pode utilizá-los para tornar suas aplicações mais dinâmicas e eficientes. Mas primeiro,
precisamos entender o que são os tais dos Runnables!
O que são Runnables?
Runnables são componentes modulares que formam uma Chain. Eles são, essencialmente, estruturas
quepodemser“rodadas”ouexecutadas. QuandocriamosumaChainusandoLCEL,estamosmontando
uma sequência de Runnables que trabalham juntos para processar dados ou realizar tarefas.
Métodos Principais dos Runnables
Os Runnables possuem três métodos principais que você precisa conhecer: invoke, stream, e
batch. Cada um desses métodos tem uma versão assíncrona, que são ainvoke, astream, e
abatch. Vamos detalhar cada um deles:
Invoke
O método invoke é o mais básico e é usado para inserir uma entrada na Chain e obter uma
resposta. É bastante direto e você já deve estar familiarizado com ele de nossas aulas anteriores.
# Exemplo de uso do método invoke
chain.invoke({'assunto': 'cachorrinhos'})
Asimov Academy
10


---