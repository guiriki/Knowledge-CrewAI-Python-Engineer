## Página 70

Criando Multi Agent Systems com CrewAI
class RetornaCotacaoAtual(BaseTool):
name: str = "Retorna cotação atual"
description: str = "Obtém a cotação mais recente de uma ação através da API do Yahoo
Finance."
↪
def _run(self, acao: str) -> str:
try:
ticker = yf.Ticker(acao)
dados = ticker.history(period="1d")
# Obtém os dados do último dia
if not dados.empty:
ultima_linha = dados.iloc[-1]
return json.dumps({
"acao": acao,
"preco_atual": ultima_linha["Close"],
"ultima_atualizacao": ultima_linha.name.strftime("%Y-%m-%d %H:%M:%S"),
})
else:
return json.dumps({"erro": "Nenhum dado encontrado para a ação fornecida."})
except Exception as e:
return json.dumps({"erro": str(e)})
Vocêpodeperceberquemodificamosasaídadafunçãoaoutilizarométodojson.dumps, quetrans‑
forma um dicionário (tipo de saída original) em uma string!
Descrevendo os argumentos
Para garantir que os argumentos da Tool sejam bem compreendidos pelo modelo, podemos utilizar
o parâmetro args_schema para declará‑los explicitamente, da seguinte forma:
from pydantic import BaseModel, Field
class RetornaCotacaoAtualInput(BaseModel):
"""Inputs da Tool RetornaCotacaoAtual."""
acao: str = Field(..., description='Código da ação (ex: "AAPL" para Apple, "PETR4.SA" para
Petrobras)')
↪
E podemos fornecer este esquema à Tool utilizando o parâmetro args_schema, da seguinte
forma:
from typing import Type
class RetornaCotacaoAtual(BaseTool):
name: str = "Retorna cotação atual"
description: str = "Obtém a cotação mais recente de uma ação através da API do Yahoo
Finance."
↪
args_schema: Type[BaseModel] = RetornaCotacaoAtualInput
def _run(self, acao: str) -> str:
# Continuação da função ....
Asimov Academy
69


---
## Página 71

Criando Multi Agent Systems com CrewAI
Juntando tudo
Ao final, temos o seguinte código:
from typing import Type
from crewai.tools import BaseTool
from pydantic import BaseModel, Field
import json
import yfinance as yf
class RetornaCotacaoAtualInput(BaseModel):
"""Inputs da Tool RetornaCotacaoAtual."""
acao: str = Field(..., description='Código da ação (ex: "AAPL" para Apple, "PETR4.SA" para
Petrobras)')
↪
class RetornaCotacaoAtual(BaseTool):
name: str = "Retorna cotação atual"
description: str = "Obtém a cotação mais recente de uma ação através da API do Yahoo
Finance."
↪
args_schema: Type[BaseModel] = RetornaCotacaoAtualInput
def _run(self, acao: str) -> str:
try:
ticker = yf.Ticker(acao)
dados = ticker.history(period="1d")
# Obtém os dados do último dia
if not dados.empty:
ultima_linha = dados.iloc[-1]
return json.dumps({
"acao": acao,
"preco_atual": ultima_linha["Close"],
"ultima_atualizacao": ultima_linha.name.strftime("%Y-%m-%d %H:%M:%S"),
})
else:
return json.dumps({"erro": "Nenhum dado encontrado para a ação fornecida."})
except Exception as e:
return json.dumps({"erro": str(e)})
E pronto, temos um exemplo completo e funcional de como criar uma Tool!
Utilizando Tools do LangChain
Saber utilizar Tools nos dá flexibilidade, inclusive para integrar ferramentas de outros frameworks
com o CrewAI, e é o caso do LangChain.
Podemos aproveitar as diversas ferramentas já desenvolvidas pela comunidade do LangChain e
integrá‑las aos nossos projetos. Para verificar as ferramentas disponíveis, você pode acessar esta
página: LangChain Tools.
Asimov Academy
70


---