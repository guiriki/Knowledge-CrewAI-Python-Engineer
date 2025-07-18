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
## Página 13

Agents de IA com Python e LangChain
03. Adição de Funções Externas à API da OpenAI
Bem-vindos a mais um capítulo da nossa apostila! Agora vamos explorar um tópico super interessante
e essencial para quem quer criar agentes de IA poderosos e versáteis: a adição de funções externas à API
da OpenAI. Vamos entender como essa capacidade pode transformar nossos modelos de linguagem
em ferramentas ainda mais úteis e inteligentes.
Neste capítulo, nosso objetivo é aprender como adicionar funções externas à API da OpenAI. Vamos
ver como isso permite que nossos modelos de linguagem realizem ações no mundo real e obtenham
informações atualizadas, superando uma das principais limitações dos modelos de linguagem: o fato
de serem treinados em dados antigos.
Por que adicionar ferramentas externas é relevante?
Os modelos de linguagem, como o GPT-3, são treinados em grandes quantidades de dados, mas esses
dados têm um limite temporal. Por exemplo, o GPT-3 foi treinado com dados até 2023. Isso significa que
ele não tem informações sobre eventos que ocorreram depois disso. Para criar aplicações realmente
úteis e interativas, precisamos que nossos modelos possam agir no mundo real e obter informações
atualizadas. É aí que entra a adição de funções externas.
A OpenAI foi pioneira em criar modelos que interpretam funções externas, permitindo que frameworks
como o LangChain integrem essas capacidades. Vamos começar revisando como adicionar funções
diretamente na API da OpenAI, para depois compararmos com a facilidade que o LangChain nos
proporciona.
Importações Iniciais
Primeiro, vamos configurar nosso ambiente e importar as bibliotecas necessárias. Vamos utilizar a
biblioteca da OpenAI e algumas outras para facilitar nosso trabalho.
import json
import openai
from dotenv import load_dotenv, find_dotenv
_ = load_dotenv(find_dotenv())
client = openai.Client()
Asimov Academy
12


---