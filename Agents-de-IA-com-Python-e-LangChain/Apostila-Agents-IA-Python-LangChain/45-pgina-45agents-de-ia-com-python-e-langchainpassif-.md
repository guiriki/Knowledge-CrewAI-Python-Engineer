## Página 45

Agents de IA com Python e LangChain
pass
if not resumos:
return 'Busca não teve retorno'
else:
return '\n\n'.join(resumos)
Testando a Tool
Vamos testar a função busca_wikipedia para garantir que está funcionando corretamente.
busca_wikipedia.invoke({'query': 'futebol'})
'Título da página: Futebol\nResumo: O futebol, também referido como futebol de c
...
Integrando as Tools em uma Chain
Vamos agora integrar essas tools em uma chain para que possamos utilizá-las em conjunto com um
modelo de linguagem, como o OpenAI.
Configurando a Chain
from langchain.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
from langchain_core.utils.function_calling import convert_to_openai_function
prompt = ChatPromptTemplate.from_messages([
('system', 'Você é um assistente amigável chamado Isaac'),
('user', '{input}')
])
chat = ChatOpenAI()
tools = [convert_to_openai_function(busca_wikipedia),
convert_to_openai_function(retorna_temperatura_atual)]
�→
chain = prompt | chat.bind(functions=tools)
Testando a Chain
Vamos testar nossa chain para garantir que ela está funcionando corretamente.
chain.invoke({'input': 'Olá'})
Asimov Academy
44


---
## Página 46

Agents de IA com Python e LangChain
AIMessage(content='Olá! Como posso ajudar você hoje?', response_metadata={'token_usage':
{'completion_tokens': 12, 'prompt_tokens': 148, 'total_tokens': 160}, 'model_name':
'gpt-3.5-turbo', 'system_fingerprint': None, 'finish_reason': 'stop', 'logprobs': None},
id='run-81757f8e-4e55-44e8-aac4-9f0f1d8aa09f-0')
�→
�→
�→
chain.invoke({'input': 'Qual é a temperatura de Porto Alegre?'})
AIMessage(content='', additional_kwargs={'function_call': {'arguments':
'{"latitude":-30.0346,"longitude":-51.2177}', 'name': 'retorna_temperatura_atual'}},
response_metadata={'token_usage': {'completion_tokens': 28, 'prompt_tokens': 156,
'total_tokens': 184}, 'model_name': 'gpt-3.5-turbo', 'system_fingerprint': None,
'finish_reason': 'function_call', 'logprobs': None},
id='run-962073d5-6bd1-4d75-86fc-40f9535288d8-0')
�→
�→
�→
�→
�→
chain.invoke({'input': 'Quem foi Isaac Asimov?'})
AIMessage(content='', additional_kwargs={'function_call': {'arguments': '{"query":"Isaac
Asimov"}', 'name': 'busca_wikipedia'}}, response_metadata={'token_usage':
{'completion_tokens': 20, 'prompt_tokens': 154, 'total_tokens': 174}, 'model_name':
'gpt-3.5-turbo', 'system_fingerprint': None, 'finish_reason': 'function_call', 'logprobs':
None}, id='run-1c6dd1a6-a47b-4c5d-887b-beca183fa0a9-0')
�→
�→
�→
�→
Na próxima aula, vamos ver de fato como rodar essas tools, adicionando-as em um loop de forma que
o modelo não só peça para rodar a ferramenta, mas também de fato a rode e obtenha a informação
necessária. Muito obrigado por terem ficado até aqui. Finalmente entreguei umas tools para vocês
que são úteis, né? Fazer uma busca no Wikipedia é legal, pegar a temperatura atual agora é legal, e
vocês vão ver que as ferramentas vão ficando cada vez mais legais. Espero que tenham gostado, nos
vemos no próximo capítulo.
Asimov Academy
45


---