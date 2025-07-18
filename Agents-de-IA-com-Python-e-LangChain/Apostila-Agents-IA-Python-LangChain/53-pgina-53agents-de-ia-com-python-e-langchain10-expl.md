## Página 53

Agents de IA com Python e LangChain
10. Explorando Tools Padrão da Biblioteca LangChain
Olá, pessoal! Agora vamos explorar algumas das ferramentas padrão que a biblioteca LangChain
oferece. Até aqui entendemos o que são funções externas e tool e como criá-las, mas ignoramos algo
muito relevante: o LangChain já possui inúmeras tools criadas pela própria comunidade que podemos
acessar e oferecer aos nossos agentes.
Antes de começar o seu processo de criação de tools, sempre sugiro a dar uma pesquisada na docu-
mentação do LangChain e verificar se alguém já não criou uma tool para a mesma finalidade, só então
comece a criar uma tool própria!
Nesta aula, vamos, portante:
• Conhecer as ferramentas padrão do LangChain.
• Aprender a utilizar essas ferramentas padrões.
• Entender as diferentes formas de importar uma tool no LangChain.
• Explorar exemplos práticos de uso das tools.
Explorando Tools Padrão
A biblioteca LangChain já possui diversas ferramentas padrão construídas que podemos utilizar. Elas
podem ser verificadas neste link. Vamos mostrar como utilizar algumas.
ArXiv
Esta ferramenta utiliza a biblioteca do arXiv para retornar resumos de artigos científicos de um deter-
minado tema solicitado. Temos três formas em geral para chamar uma tool, da mais baixo a mais alto
nível:
1. Criando a tool utilizando o Wrapper: No LangChain foram criados diferentes wrappers para
APIs e bibliotecas externas que facilitam a utilização das mesmas e permitem uma rápida criação
de uma nova tool. Ela é mais customizável, pois podemos modificar as descrições e argumentos
da tool às nossas necessidades, além de podermos modificar facilmente os parâmetros do
wrapper.
2. Instanciando a tool já criada: Em geral, uma tool pronta já está criada dentro da biblioteca e
podemos acessá-la diretamente.
3. Utilizando o load_tools:
O LangChain possui uma ferramenta especial chamada
load_tools que permite o carregamento de diversas ferramentas ao mesmo tempo.
Vamos explorar os três métodos agora:
Asimov Academy
52


---
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