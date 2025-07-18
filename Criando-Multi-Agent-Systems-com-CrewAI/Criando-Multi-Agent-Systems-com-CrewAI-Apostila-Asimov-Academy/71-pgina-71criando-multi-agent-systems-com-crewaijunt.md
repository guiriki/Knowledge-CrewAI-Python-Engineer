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
## Página 72

Criando Multi Agent Systems com CrewAI
Integrando Ferramentas do LangChain ao CrewAI
Mas vamos ver, na prática, como podemos fazer isso. A estrutura será similar à criação de uma ferra‑
menta personalizada, com a diferença de que a classe da ferramenta do LangChain será importada e
o método _run apenas executará a Tool da seguinte forma:
import os
from dotenv import load_dotenv
from crewai import Agent, Task, Crew
from crewai.tools import BaseTool
from pydantic import Field
from langchain_community.utilities import GoogleSerperAPIWrapper
# Configure sua chave SERPER_API_KEY em um arquivo .env, por exemplo:
# SERPER_API_KEY=<sua chave da API>
load_dotenv()
class SearchTool(BaseTool):
name: str = "Search"
description: str = "Útil para consultas baseadas em busca. Use isso para encontrar
informações atuais sobre mercados, empresas e tendências."
↪
search: GoogleSerperAPIWrapper = Field(default_factory=GoogleSerperAPIWrapper)
def _run(self, query: str) -> str:
"""Executa a consulta de busca e retorna os resultados"""
try:
return self.search.run(query)
except Exception as e:
return f"Erro ao realizar a busca: {str(e)}"
No exemplo acima, estamos criando uma ferramenta de busca chamada SearchTool, que utiliza a
classe GoogleSerperAPIWrapper do LangChain para buscar resultados no Google.
Notem que definimos a ferramenta GoogleSerperAPIWrapper do LangChain como um atributo
da classe que estamos criando:
class SearchTool(BaseTool):
#...
search: GoogleSerperAPIWrapper = Field(default_factory=GoogleSerperAPIWrapper)
E depois podemos utilizar essa ferramenta dentro do nosso método _run:
def _run(self, query: str) -> str:
#...
return self.search.run(query)
#...
Com essa simplicidade, temos acesso a todas as ferramentas do framework LangChain!
Aproveitem para dar uma olhada nas ferramentas existentes e comentem aqui conosco quais delas
fazem sentido para vocês!
Asimov Academy
71


---