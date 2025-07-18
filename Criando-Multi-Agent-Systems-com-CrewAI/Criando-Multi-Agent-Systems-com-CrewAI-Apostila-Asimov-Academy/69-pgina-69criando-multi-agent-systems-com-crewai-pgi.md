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