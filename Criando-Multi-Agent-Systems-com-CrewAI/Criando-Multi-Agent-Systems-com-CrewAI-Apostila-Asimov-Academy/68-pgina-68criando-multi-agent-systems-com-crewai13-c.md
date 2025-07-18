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
## Página 69

Criando Multi Agent Systems com CrewAI
:return: Dicionário com o preço atual e o horário da última atualização.
"""
try:
ticker = yf.Ticker(acao)
dados = ticker.history(period="1d")
# Obtém os dados do último dia
if not dados.empty:
ultima_linha = dados.iloc[-1]
return {
"acao": acao,
"preco_atual": ultima_linha["Close"],
"ultima_atualizacao": ultima_linha.name.strftime("%Y-%m-%d %H:%M:%S"),
}
else:
return {"erro": "Nenhum dado encontrado para a ação fornecida."}
except Exception as e:
return {"erro": str(e)}
# Exemplo de uso:
cotacao = obter_cotacao_atual("AAPL")
print(cotacao)
Atenção! Isto ainda não é uma tool. Precisamos convertê‑la a um formato que seja compreen‑
sível por um modelo dentro do framework CrewAI, e é o que veremos na sequência.
Criando Tools com BaseTool
Vamos utilizar a classe BaseTool para criar nossa ferramenta. Ela deve seguir o seguinte formato,
sendo que a execução da ferramenta se dará dentro do método _run.
from crewai.tools import BaseTool
class MinhaFerramentaPersonalizada(BaseTool):
name: str = "Nome da minha ferramenta"
description: str = "O que esta ferramenta faz. Isso é vital para uma utilização eficaz."
def _run(self, argumento: str) -> str:
# A lógica da sua ferramenta aqui
return "Resultado da ferramenta"
É importante que o nome da ferramenta já indique seu propósito, além de ser relevante escrever boas
descrições. O retorno do método _run deve obrigatoriamente ser uma string!
Aplicando para o nosso exemplo de função utilizando o Yahoo Finance, temos o seguinte:
from crewai.tools import BaseTool
import json
import yfinance as yf
Asimov Academy
68


---