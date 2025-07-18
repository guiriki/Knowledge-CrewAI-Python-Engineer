## Página 61

Agents de IA com Python e LangChain
Embora não seja obrigatório, um agente pode ser perfilado ou receber uma persona para definir
seu papel. Essas informações de perfil geralmente são escritas no prompt e podem incluir detalhes
específicos, como informações sobre o papel, personalidade, informações sociais e outras informações
demográficas. Isso ajuda a moldar a forma como o agente interage com os usuários e como ele toma
decisões. As estratégias para definir um perfil de agente podem incluir elaboração manual, geração
por LLM ou orientada por dados.
Planejamento
O módulo de planejamento é fundamental para que o agente consiga dividir os passos necessários
ou subtarefas que ele resolverá individualmente para responder à solicitação do usuário. Essa etapa
é crucial, pois permite que o agente raciocine melhor sobre o problema e encontre uma solução de
forma confiável. O planejamento utiliza um LLM para decompor um plano detalhado que incluirá
subtarefas para ajudar a abordar a pergunta do usuário.
Memória
A memória é responsável por armazenar os registros internos do agente, incluindo pensamentos,
ações e observações passadas do ambiente, além de todas as interações entre o agente e o usuário.
Existem dois tipos principais de memória:
• Memória de Curto Prazo: Inclui informações contextuais sobre as situações atuais do agente.
Isso é tipicamente realizado por meio de aprendizado em contexto, o que significa que é curto e
finito devido a restrições de janela de contexto.
• Memória de Longo Prazo: Inclui os comportamentos e pensamentos passados do agente que
precisam ser retidos e recuperados ao longo de um período prolongado. Isso geralmente utiliza
um armazenamento vetorial externo acessível por meio de recuperação rápida e escalável para
fornecer informações relevantes para o agente conforme necessário.
A memória híbrida combina tanto a memória de curto prazo quanto a de longo prazo, melhorando a
capacidade do agente de raciocinar a longo prazo e acumular experiências.
Ferramentas
As ferramentas são um conjunto de recursos que permitem que o agente LLM interaja com ambientes
externos, como a API de busca do Wikipedia, ferramentas de busca na web ou interpretadores de
código. Elas também podem incluir bancos de dados, bases de conhecimento e modelos externos.
Quando o agente interage com ferramentas externas, ele executa tarefas por meio de fluxos de trabalho
Asimov Academy
60


---
## Página 62

Agents de IA com Python e LangChain
que ajudam a obter observações ou informações necessárias para completar subtarefas e satisfazer a
solicitação do usuário.
Construindo um Agent
A ideia central dos Agents é usar um modelo de linguagem para escolher uma sequência de ações a
serem executadas. Nas chains, uma sequência de ações é definida diretamente no código, ou seja,
recebe uma input do usuário, depois faz um parsing da output, depois passa para outra chain, utiliza
uma ferramenta, etc. Tudo é pré-definido por quem desenvolveu a chain. Já nos Agents, um modelo
de linguagem é usado como um motor de raciocínio para determinar quais ações devem ser
tomadas e em qual ordem.
Criando as Tools que Usaremos
Vamos começar criando as Tools que nossos Agents utilizarão. Essas Tools são funções que o modelo
de linguagem pode chamar para obter informações ou realizar ações específicas.
import requests
import datetime
from langchain.agents import tool
from pydantic import BaseModel, Field
import wikipedia
wikipedia.set_lang('pt')
class RetornTempArgs(BaseModel):
latitude: float = Field(description='Latitude da localidade que buscamos a temperatura')
longitude: float = Field(description='Longitude da localidade que buscamos a temperatura')
@tool(args_schema=RetornTempArgs)
def retorna_temperatura_atual(latitude: float, longitude: float):
'''Retorna a temperatura atual para uma dada coordenada'''
URL = 'https://api.open-meteo.com/v1/forecast'
params = {
'latitude': latitude,
'longitude': longitude,
'hourly': 'temperature_2m',
'forecast_days': 1,
}
resposta = requests.get(URL, params=params)
if resposta.status_code == 200:
resultado = resposta.json()
Asimov Academy
61


---