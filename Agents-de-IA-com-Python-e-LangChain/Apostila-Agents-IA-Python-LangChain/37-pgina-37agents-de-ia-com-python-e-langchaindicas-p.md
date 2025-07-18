## Página 37

Agents de IA com Python e LangChain
Dicas para a Extração
• Utilize a estrutura que aprendemos na aula para criar as classes de dados com Pydantic, se
necessário.
• Pense em como você pode estruturar seu código para que a extração seja eficiente e organizada.
• Lembre-se de que a categorização e a estruturação de dados são fundamentais para facilitar a
análise e utilização posterior do seu agente.
Asimov Academy
36


---
## Página 38

Agents de IA com Python e LangChain
07. Criação de Tools com LangChain
Olá, pessoal! Bem-vindos a mais um capítulo da nossa apostila. Hoje, vamos nos aprofundar em um
dos aspectos mais essenciais para a construção de agentes inteligentes: as Tools (ferramentas). As
ferramentas são o que realmente diferenciam um Agent, permitindo que ele interaja com o mundo de
maneira mais eficiente e eficaz. Nosso objetivo agora será:
• Entender o que são Tools e sua importância para os Agents.
• Aprender a criar Tools utilizando o decorador @tool.
• Explorar a criação de Tools com a metaclasse StructuredTool.
• Compreender como descrever argumentos de forma clara e precisa.
• Ver exemplos práticos de como chamar e utilizar essas Tools.
O que são tools?
As tools (ferramentas) são componentes essenciais no ecossistema do LangChain, permitindo que
agentes, cadeias ou modelos de linguagem (LLMs) interajam com o mundo externo. Elas funcionam
como interfaces que possibilitam a execução de ações específicas, facilitando a integração de fun-
cionalidades externas nas aplicações de IA.
Como as Tools se Relacionam com Modelos de Linguagem
As tools são especialmente poderosas quando combinadas com as capacidades de tool calling dos
modelos de linguagem. Isso significa que, ao invés de apenas gerar texto, os LLMs podem agora
chamar funções externas para realizar ações específicas, como buscar informações, processar dados
ou interagir com APIs.
Por exemplo, ao criar uma tool que retorna a temperatura atual de uma localidade, o modelo de
linguagem pode ser instruído a chamar essa função quando um usuário faz uma pergunta sobre o
clima. Isso não só enriquece a interação, mas também permite que o modelo forneça respostas mais
precisas e contextuais.
Criando Tools com o Decorador @tool
Vamos começar criando uma ferramenta utilizando o decorador @tool. O decorador @tool modifica
uma função, permitindo que ela seja usada como uma ferramenta pelo LangChain.
from langchain.agents import tool
Asimov Academy
37


---