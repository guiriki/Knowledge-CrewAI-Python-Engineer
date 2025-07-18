## Página 54

Agents de IA com Python e LangChain
Criando Tool Manualmente Através do Wrapper
Primeira tool que a gente vai explorar vai ser a
do ArXiv. Caso você não saiba, o ArXiv é um repositório de papers, de artigos científicos, e a gente
consegue acessar o ArXiv através do LangChain e buscar o resumo de vários artigos científicos que
estão na internet.
from langchain_community.utilities.arxiv import ArxivAPIWrapper
from pydantic import BaseModel, Field
from langchain.tools import StructuredTool
class ArxivArgs(BaseModel):
query: str = Field(description='Query de busca no ArXiv')
tool_arxiv = StructuredTool.from_function(
func=ArxivAPIWrapper(top_k_results=2).run,
args_schema=ArxivArgs,
name='arxiv',
description=(
"Uma ferramenta em torno do Arxiv.org. "
"Útil para quando você precisa responder a perguntas sobre Física, Matemática, "
"Ciência da Computação, Biologia Quantitativa, Finanças Quantitativas, Estatística, "
"Engenharia Elétrica e Economia utilizando artigos científicos do arxiv.org. "
"A entrada deve ser uma consulta de pesquisa em inglês."
),
return_direct=True
)
print('Descrição:', tool_arxiv.description)
print('Args:', tool_arxiv.args)
Instanciando a Tool Já Criada
Outra forma de criar a tool é instanciando diretamente a tool já
criada dentro da biblioteca.
from langchain_community.tools.arxiv import ArxivQueryRun
tool_arxiv = ArxivQueryRun(api_wrapper=ArxivAPIWrapper(top_k_results=2))
print('Descrição:', tool_arxiv.description)
Utilizando o load_tools
A última forma é utilizando o load_tools, que é mais alto nível e
menos customizável, mas também mais simples.
from langchain.agents import load_tools
tools = load_tools(['arxiv'])
tool_arxiv = tools[0]
print('Descrição:', tool_arxiv.description)
Exemplo de uso
E para rodar, basta utilizar o método run ou invoke:
tool_arxiv.run({'query': 'llm'})
Asimov Academy
53


---
## Página 55

Agents de IA com Python e LangChain
E a resposta será:
"Published: 2024-01-08\nTitle: A Survey of Large Language Models for Code: Evolution,
Benchmarking, and Future Trends\nAuthors: Zibin Zheng, Kaiwen Ning, Yanlin Wang, Jingwen
Zhang, Dewu Zheng, Mingxi Ye, Jiachi Chen\nSummary: General large language models (LLMs),
represented by ChatGPT, have\ndemonstrated
�→
�→
�→
...
Python REPL
Outra ferramenta interessante é o Python REPL, que permite pode dar a um modelo a capacidade de
rodar códigos Python diretamente.
from langchain.experimental.tools.python import PythonREPLTool
tool_python = PythonREPLTool()
print('Descrição:', tool_repl.description)
print('Args:', tool_repl.args)
Descrição: A Python shell. Use this to execute python commands. Input should be a valid python
command. If you want to see the output of a value, you should print it out with
`print(...)`.
�→
�→
Args: {'query': {'title': 'Query', 'type': 'string'}}
Exemplo de uso
result = tool_python.run("print('Hello, World!')")
print(result)
E a resposta será:
'Hello, World!'
StackOverflow
Podemos também utilizar a ferramenta do StackOverflow para buscar respostas de programação.
from langchain.agents import load_tools
tools = load_tools(['stack_exchange'])
tool_stack = tools[0]
print('Descrição:', tool_stack.description)
print('Args:', tool_stack.args)
Descrição: A wrapper around StackExchange. Useful for when you need to answer specific
programming questionscode excerpts, code examples and solutionsInput should be a fully
formed question.
�→
�→
Args: {'query': {'title': 'Query', 'type': 'string'}}
Asimov Academy
54


---