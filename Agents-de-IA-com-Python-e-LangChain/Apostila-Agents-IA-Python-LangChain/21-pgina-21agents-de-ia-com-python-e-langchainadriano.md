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
## Página 22

Agents de IA com Python e LangChain
Utilizando Pydantic para Criação de Tools da OpenAI
Lembram que para criarmos uma função de temperatura atual que a API da OpenAI reconece precisá-
vamos criar um dicionário cheio de argumentos, que facilmente poderia nos confundir:
import json
def obter_temperatura_atual(local, unidade="celsius"):
if "são paulo" in local.lower():
return json.dumps({"local": "São Paulo", "temperatura": "32", "unidade": unidade})
elif "porto alegre" in local.lower():
return json.dumps({"local": "Porto Alegre", "temperatura": "25", "unidade": unidade})
else:
return json.dumps({"local": local, "temperatura": "unknown"})
tools = [
{
"type": "function",
"function": {
"name": "obter_temperatura_atual",
"description": "Obtém a temperatura atual em uma dada cidade",
"parameters": {
"type": "object",
"properties": {
"local": {
"type": "string",
"description": "O nome da cidade. Ex: São Paulo",
},
"unidade": {
"type": "string",
"enum": ["celsius", "fahrenheit"]
},
},
"required": ["local"],
},
},
}
]
Utilizando Pydantic para Criar a Tool
Vamos agora utilizar Pydantic para criar a mesma função, mas de uma forma mais robusta e com
validação de dados.
from pydantic import BaseModel, Field
from typing import Optional
from enum import Enum
class UnidadeEnum(str, Enum):
celsius = 'celsius'
fahrenheit = 'fahrenheit'
Asimov Academy
21


---