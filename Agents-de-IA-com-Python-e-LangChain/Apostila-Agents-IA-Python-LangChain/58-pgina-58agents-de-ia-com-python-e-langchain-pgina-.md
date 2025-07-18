## Página 58

Agents de IA com Python e LangChain
• list_directory: lista arquivos em uma pasta
Quando passamos o parâmetro root_dir=‘arquivos’, estamos dizendo às ferramentas que elas somente
terão acesso aos arquivos dentro da pasta arquivos.
Agora recriamos nossa função de roteamento, como visto no capítulo anterior:
from langchain_core.agents import AgentFinish
def roteamento(resultado):
if isinstance(resultado, AgentFinish):
return resultado.return_values['output']
else:
return tool_run[resultado.tool].run(resultado.tool_input)
E criamos nossa chain:
from langchain.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
from langchain_core.utils.function_calling import convert_to_openai_function
from langchain.agents.output_parsers import OpenAIFunctionsAgentOutputParser
tools_json = [convert_to_openai_function(tool) for tool in tools]
tool_run = {tool.name: tool for tool in tools}
prompt = ChatPromptTemplate.from_messages([
('system', 'Você é um assistente amigável chamado Isaac capaz de gerenciar arquivos'),
('user', '{input}')
])
chat = ChatOpenAI()
chain = (prompt
| chat.bind(functions=tools_json)
| OpenAIFunctionsAgentOutputParser()
| roteamento)
E agora já podemos utilizar nosso gerenciador de arquivos:
chain.invoke({'input': 'O que você é capaz de fazer?'})
'Olá! Eu sou um assistente amigável chamado Isaac e sou capaz de gerenciar arquivos. Posso
escrever texto em arquivos, ler o conteúdo de arquivos, pesquisar arquivos com base em
padrões de regex e listar arquivos e diretórios em uma pasta específica. Se precisar de
ajuda com alguma dessas tarefas, fique à vontade para me pedir! Como posso ajudar você
hoje?'
�→
�→
�→
�→
chain.invoke({'input': 'Crie um arquivo txt chamado notas com o seguinte conteúdo "Isso foi
feito por uma LLM"'})
�→
'File written successfully to notas.txt.'
chain.invoke({'input': 'Leia o arquivo notas.txt'})
'Isso foi feito por uma LLM'
Asimov Academy
57


---
## Página 59

Agents de IA com Python e LangChain
E assim fizemos um modelo capaz de escrever arquivos e lê-los em nosso pc. Incrível, não?
Espero que tenham gostado e que essas ferramentas ajudem vocês em seus projetos!
Asimov Academy
58


---