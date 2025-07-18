## Página 35

Agents de IA com Python e LangChain
O conteúdo da página estará desformatado, então precisamos definir uma estrutura para os posts do
blog:
from pydantic import BaseModel, Field
from typing import List
from langchain_core.utils.function_calling import convert_to_openai_function
class BlogPost(BaseModel):
'''Informações sobre um post de blog'''
titulo: str = Field(description='O título do post de blog')
autor: str = Field(description='O autor do post de blog')
data: str = Field(description='A data de publicação do post de blog')
class BlogSite(BaseModel):
'''Lista de blog posts de um site'''
posts: List[BlogPost] = Field(description='Lista de posts de blog do site')
tool_blog = convert_to_openai_function(BlogSite)
tool_blog
Agora, vamos criar uma chain para extrair essas informações:
from langchain.output_parsers.openai_functions import JsonKeyOutputFunctionsParser
from langchain.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
prompt = ChatPromptTemplate.from_messages([
('system', 'Extraia da página todos os posts de blog com autor e data de publicação'),
('user', '{input}')
])
chat = ChatOpenAI()
chain = (prompt
| chat.bind(functions=[tool_blog], function_call={'name': 'BlogSite'})
| JsonKeyOutputFunctionsParser(key_name='posts'))
Vamos invocar a chain com o conteúdo da página:
chain.invoke({'input': page})
O resultado será:
[{'titulo': 'Python ou Power BI: qual ferramenta é melhor para criar dashboards?',
'autor': 'Renata Lopes',
'data': '23-05-24'},
{'titulo': 'Try e Except em Python - Entenda como lidar com erros',
'autor': 'Adriano Soares',
'data': '22-05-24'},
{'titulo': 'Print em Python: entenda o que é a função print e onde usá-la',
'autor': 'Juliano Faccioni',
'data': '21-05-24'},
{'titulo': 'Exemplos de programas em Python - Aprenda fazendo',
'autor': 'Adriano Soares',
'data': '16-05-24'},
{'titulo': 'Qual linguagem de programação aprender? Guia completo para iniciantes',
Asimov Academy
34


---
## Página 36

Agents de IA com Python e LangChain
'autor': 'Renata Lopes',
'data': '15-05-24'},
Ecomextremafacilidadeconseguimosestruturarinformaçõescapturadasdepáginaswebcombinando
Web Scraping com modelos de linguagem.
E é isso, pessoal! Vimos como é possível extrair informações específicas de textos e páginas web
utilizando Python e LangChain. Essas técnicas são extremamente úteis para transformar dados não
estruturados em informações organizadas e utilizáveis.
Desafio
Após este conteúdo sobre extração de informações utilizando LLMs, quero propor um desafio para
vocês! É um exercício simples e bem pedagógico, mas a ideia é reforçar o aprendizado de vocês e
mostrar como as LLMs podem ser utilizadas até nas atividades mais simples do cotidiano.
Vamos aplicar o que aprendemos e extrair dados da seguinte receita que encontrei na internet. Após a
extração, vamos criar uma lista de compras. Pensem que este poderia ser muito facilmente o primeiro
passo para um agente que faz compras automaticamente ao fornecermos uma receita para ele. A
receita que temos é a seguinte:
Receita de Bolo de Cenoura
Massa 1. Em um liquidificador, adicione a cenoura, os ovos e o óleo, depois misture. 2. Acrescente o
açúcar e bata novamente por 5 minutos. 3. Em uma tigela ou na batedeira, adicione a farinha de trigo
e depois misture novamente. 4. Acrescente o fermento e misture lentamente com uma colher. 5. Asse
em um forno preaquecido a 180° C por aproximadamente 40 minutos. Cobertura 6. Despeje em uma
tigela a manteiga, o chocolate em pó, o açúcar e o leite, depois misture. 7. Leve a mistura ao fogo e
continue misturando até obter uma consistência cremosa, depois despeje a calda por cima do bolo.
O que você precisa fazer?
A partir da receita acima, você deve extrair as seguintes informações:
• Utensílios de Cozinha: Liste todos os utensílios que são mencionados na receita (por exemplo,
liquidificador, tigela, batedeira).
• Ingredientes: Liste todos os ingredientes necessários para preparar o bolo (por exemplo, ce-
noura, ovos, óleo, açúcar, farinha de trigo, fermento, manteiga, chocolate em pó, leite).
• Salvar em CSV: Após extrair as informações, salve os dados de ingredientes em um arquivo CSV
e os utensílios em outro.
Asimov Academy
35


---