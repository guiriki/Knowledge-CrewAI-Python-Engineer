## Página 67

Criando Multi Agent Systems com CrewAI
@crew
def crew(self) -> Crew:
return Crew(
agents=self.agents,
tasks=self.tasks,
verbose=True,
)
Podemos ver que estamos utilizando 3 ferramentas: ‑ SerperDevTool: Faz uma busca no Google
para um determinado assunto, encontrando assim páginas na web que possam ser relevantes. ‑
ScrapeWebsiteTool: É responsável por acessar essas páginas web e fazer o download do conteúdo
delas, permitindo que os modelos leiam seus conteúdos. ‑ FileWriterTool: Pode escrever um arquivo
no computador onde a aplicação está rodando.
Já demos passos importantes para transformar o gerador de blog posts em uma ferramenta real‑
mente útil!
Asimov Academy
66


---
## Página 68

Criando Multi Agent Systems com CrewAI
13. Criando tools presonalizadas para CrewAI
Fala, pessoal! Estamos chegando ao final do nosso curso e considero que já aprendemos todas as
bases do CrewAI. Agora quero passar um conceito um pouco mais avançado, que exige um pouco
mais de conhecimento de programação: a criação de Tools próprias.
Como vocês viram, já existem diversas opções de ferramentas disponíveis na biblioteca para
utilizarmos. No entanto, sabemos que a realidade é sempre mais complexa do que planejamos.
Como programadores, precisamos usar a capacidade que a programação Python nos dá para nos
adaptarmos às situações.
SabercriarumaToolpersonalizadanosdáautonomia. Assim, deixamosdedependerdosdesenvolve‑
dores da biblioteca e de restringir nossas aplicações ao que já foi criado, passando a nos tornarmos,
de fato, criadores!
Criando e utilizando Tools em CrewAI
Vou passar um passo a passo completo sobre como criar Tools. Não é nada tão complexo, mas vai
exigir de vocês um pouco de atenção.
Para que o modelo consiga entender as nossas ferramentas, é importante descrever bem elas, tanto
adicionando docstrings (aquelas explicações que vêm logo após a definição de uma função) quanto
nos parâmetros de descrição.
Outro ponto importante é que precisamos cuidar bem dos nomes que damos às nossas ferramentas e
aos argumentos delas, pois o modelo precisa ler aquela função, aquele argumento e suas definições
para entender o que ela faz. Se o modelo não entender, ele não utilizará a ferramenta!
Função que será usada como exemplo
Como exemplo, vamos criar uma ferramenta para buscar a cotação atual de uma ação utilizando a
biblioteca Yahoo Finance.
Antes de criarmos a tool propriamente, vamos criar uma função em Python que faz uma chamada a
api do Yahoo Finance e retorna um dicionário com a informação solicitada.
import yfinance as yf
def obter_cotacao_atual(acao: str):
"""
Obtém a cotação mais recente de uma ação.
:param acao: Código da ação (ex: "AAPL" para Apple, "PETR4.SA" para Petrobras)
Asimov Academy
67


---