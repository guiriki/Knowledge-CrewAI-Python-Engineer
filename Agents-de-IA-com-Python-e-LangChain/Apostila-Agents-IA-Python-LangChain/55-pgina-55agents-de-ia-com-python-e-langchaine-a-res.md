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