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
## Página 12

Agents de IA com Python e LangChain
Stream
O método stream é usado quando queremos uma interação mais dinâmica, como em uma
conversa. Ele permite que a saída seja transmitida de volta conforme é gerada pelo modelo, criando
uma experiência mais fluida para o usuário.
# Exemplo de uso do método stream
for chunk in chain.stream({'assunto': 'cachorrinho'}):
print(chunk.content, end='', flush=True)
Batch
O método batch é utilizado para processar múltiplas entradas em paralelo. Isso é especial-
mente útil quando você precisa lidar com várias requisições ao mesmo tempo, otimizando o tempo de
resposta.
# Exemplo de uso do método batch
chain.batch([{'assunto': 'cachorrinhos'}, {'assunto': 'gatinho'}, {'assunto': 'cavalinhos'}])
Métodos Assíncronos
Os métodos assíncronos são uma extensão dos métodos síncronos que permitem que as operações
sejamrealizadasdeformanão-bloqueante. Issosignificaqueseuprogramapodecontinuarexecutando
outras tarefas enquanto espera que a Chain complete suas operações.
Ainvoke
Oainvokeéaversãoassíncronadoinvoke. Eleéusadoparafazerchamadasassíncronas
à Chain.
# Exemplo de uso do método ainvoke
import asyncio
async def processa_chain(input):
resposta = await chain.ainvoke(input)
return resposta
# Criando e esperando tarefas assíncronas
task1 = asyncio.create_task(processa_chain({'assunto': 'gatinho'}))
await task1
Espero que você tenha gostado desta introdução à LCEL e esteja tão empolgado quanto eu para
explorar mais sobre o que podemos fazer com essa poderosa ferramenta. No próximo capítulo, vamos
explorar como adicionar funções externas à API da OpenAI.
Asimov Academy
11


---