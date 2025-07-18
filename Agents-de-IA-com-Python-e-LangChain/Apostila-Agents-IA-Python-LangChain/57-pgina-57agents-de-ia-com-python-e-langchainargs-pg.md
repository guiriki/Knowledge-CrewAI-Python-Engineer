## Página 57

Agents de IA com Python e LangChain
Args: {'source_path': {'title': 'Source Path', 'description': 'Path of the file to move',
'type': 'string'}, 'destination_path': {'title': 'Destination Path', 'description': 'New
path for the moved file', 'type': 'string'}}
�→
�→
Name: read_file
Descrição: Read file from disk
Args: {'file_path': {'title': 'File Path', 'description': 'name of file', 'type': 'string'}}
Name: write_file
Descrição: Write file to disk
Args: {'file_path': {'title': 'File Path', 'description': 'name of file', 'type': 'string'},
'text': {'title': 'Text', 'description': 'text to write to file', 'type': 'string'},
'append': {'title': 'Append', 'description': 'Whether to append to an existing file.',
'default': False, 'type': 'boolean'}}
�→
�→
�→
Name: list_directory
Descrição: List files and directories in a specified folder
Args: {'dir_path': {'title': 'Dir Path', 'description': 'Subdirectory to list.', 'default':
'.', 'type': 'string'}}
�→
Podemos verificar que este toolkit apresenta 7 ferramentas diferentes:
• copy_file: copia arquivos
• file_delete: deleta arquivos
• file_search: busca arquivos
• move_file: move arquivos
• read_file: lê arquivos
• write_file: escreve arquivos
• list_directory: lista arquivos em uma pasta
Exemplo de uma aplicação
Podemos utilizar o toolkit de file system para criar uma aplicação que gerencia arquivos no nosso
computador. Para isso, primeiro importamos as ferramentas:
from langchain_community.agent_toolkits.file_management.toolkit import FileManagementToolkit
tool_kit = FileManagementToolkit(
root_dir='arquivos',
selected_tools=['write_file', 'read_file', 'file_search','list_directory']
)
tools = tool_kit.get_tools()
Selecionamos apenas três ferrametas:
• file_search: busca arquivos
• read_file: lê arquivos
• write_file: escreve arquivos
Asimov Academy
56


---
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