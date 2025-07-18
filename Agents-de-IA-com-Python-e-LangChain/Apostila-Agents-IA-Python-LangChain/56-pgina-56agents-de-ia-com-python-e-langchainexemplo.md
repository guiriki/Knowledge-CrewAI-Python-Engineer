## Página 56

Agents de IA com Python e LangChain
Exemplo de uso
tool_stack.run({'query': 'LangChain Agents'})
E a resposta será:
'Question: While using groq for my project im getting this error\ndef
claim_agent(user_question):\n
memory =
ConversationBufferWindowMemory(ai_prefix=&quot;Insurance <span
class="highlight">Agent</span>&quot;, k=20)\n
prompt_template = PromptTemplate(\n
input_variables=[&#39;history&#39;, &#39;input&#39;], &hellip;
&quot;D:\\Project_tests.venv\\Lib\\site-packages\\<span
class="highlight">langchain</span>\\chains\\base.py&quot;, line 163, in invoke\nraise
e\nFile
�→
�→
�→
�→
�→
�→
�→
...
File System
Por último, vamos explorar o toolkit de gerenciamento de arquivos, que permite criar, deletar, mover e
listar arquivos.
from langchain_community.agent_toolkits.file_management import FileManagementToolkit
toolkit = FileManagementToolkit(root_dir='arquivos')
tools = toolkit.get_tools()
for tool in tools:
print('Name:', tool.name)
print('Descrição:', tool.description)
print('Args:', tool.args)
print()
Name: copy_file
Descrição: Create a copy of a file in a specified location
Args: {'source_path': {'title': 'Source Path', 'description': 'Path of the file to copy',
'type': 'string'}, 'destination_path': {'title': 'Destination Path', 'description': 'Path
to save the copied file', 'type': 'string'}}
�→
�→
Name: file_delete
Descrição: Delete a file
Args: {'file_path': {'title': 'File Path', 'description': 'Path of the file to delete',
'type': 'string'}}
�→
Name: file_search
Descrição: Recursively search for files in a subdirectory that match the regex pattern
Args: {'dir_path': {'title': 'Dir Path', 'description': 'Subdirectory to search in.',
'default': '.', 'type': 'string'}, 'pattern': {'title': 'Pattern', 'description': 'Unix
shell regex, where * matches everything.', 'type': 'string'}}
�→
�→
Name: move_file
Descrição: Move or rename a file from one location to another
Asimov Academy
55


---
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