## Página 20

Agents de IA com Python e LangChain
04. Adição de Funções Externas Utilizando LangChain
Olá, pessoal! Bem-vindos de volta :)
Agora que entendemos como adicionar funções externas a modelos da OpenAI, vamos ver como o
LangChain nos auxilia a tornar esse processo muito mais fácil e intuitivo. Nosso objetivos, portanto,
serão:
• Aprender a usar a biblioteca Pydantic para validação de dados.
• Criar funções externas utilizando LangChain e Pydantic e integrá-las com a API da OpenAI.
• Utilizar o LangChain para adicionar essas funções aos nossos modelos de linguagem.
Introduzindo Pydantic
Como vimos no último capítulo, o trabalho de adicionar funções externas passa muito por saber-
mos descrever bem a utilidade das nossas funções e seus argumentos. Os modelos de linguagem
compreendem apenas texto, então o entendimento de para que as funções que estamos oferecendo
servem também deve ser feita por texto. Para que tenhamos funções e argumentos bem definidos,
o LangChain passou a utilizar a biblioteca Pydantic, por ser esta a principal ferramenta de validação
de estruturas de dados em Python. Agora vamos entender por que e como essa validação pode ser
importante para nós.
Como Criamos uma Estrutura de Dados Sem Pydantic
Antes de entendermos como criar estruturas no Pydantic, vamos ver como criar uma estrutura de
dados simples em Python sem usar essa biblioteca. Essa será nossa base de comparação e tornará
mais evidente a importância de utilizarmos Pydantic:
class Pessoa:
def __init__(self, nome: str, idade: int, peso: float) -> None:
self.nome = nome
self.idade = idade
self.peso = peso
adriano = Pessoa('Adriano', 32, 68)
print(adriano.idade)
# Saída: 32
A forma básica em Python é utilizando classes como feito acima. Acabamos de criar uma estrutura
para representar uma pessoa, e criamos uma instância dessa estrutura com argumentos referentes ao
professor Adriano.
No entanto, sem validação de tipos, podemos acabar com dados inconsistentes:
Asimov Academy
19


---
## Página 21

Agents de IA com Python e LangChain
adriano = Pessoa('Adriano', 32, 'ashdbadgvuya')
print(adriano.peso)
# Saída: 'ashdbadgvuya'
Neste caso, apesar de ser indicado que peso deve ser um float, ao adicionarmos uma string a estrutura
de dados aceitará este sem problemas, o que gerará inconsistências.
Como Criamos uma Estrutura de Dados Usando Pydantic
Agora, vamos ver como o Pydantic pode nos ajudar a criar estruturas de dados mais robustas e com
validação automática.
from pydantic import BaseModel
class pydPessoa(BaseModel):
nome: str
idade: int
peso: float
adriano = pydPessoa(nome='Adriano', idade=32, peso=68)
print(adriano.nome)
# Saída: 'Adriano'
Podemosjáverqueaestruturaémaissimplesemaisrobustaporautomaticamentejárealizarvalidação
de dados:
try:
adriano = pydPessoa(nome='Adriano', idade=32, peso='asuhdauishg')
except ValidationError as e:
print(e)
Podemos ver que ao tentarmos iniciar uma instância com dados inconsistentes, o Pydantic gerará um
erro avisando ao usuário.
Nesting de Classes com Pydantic
Podemos até fazer um “nesting” de classes, onde uma classe de dados recebe outra como input.
from typing import List
class pydAsimoTeam(BaseModel):
funcionarios: List[pydPessoa]
team = pydAsimoTeam(funcionarios=[pydPessoa(nome='Adriano', idade=32, peso=68)])
print(team)
Asimov Academy
20


---