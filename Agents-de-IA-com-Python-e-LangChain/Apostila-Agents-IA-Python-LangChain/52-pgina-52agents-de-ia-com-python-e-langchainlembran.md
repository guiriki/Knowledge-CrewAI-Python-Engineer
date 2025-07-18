## Página 52

Agents de IA com Python e LangChain
Lembrando que este código funciona para emails do Gmail. Você precisa criar uma senha de app no
Gmail e adicionar ao código.
Asimov Academy
51


---
## Página 53

Agents de IA com Python e LangChain
10. Explorando Tools Padrão da Biblioteca LangChain
Olá, pessoal! Agora vamos explorar algumas das ferramentas padrão que a biblioteca LangChain
oferece. Até aqui entendemos o que são funções externas e tool e como criá-las, mas ignoramos algo
muito relevante: o LangChain já possui inúmeras tools criadas pela própria comunidade que podemos
acessar e oferecer aos nossos agentes.
Antes de começar o seu processo de criação de tools, sempre sugiro a dar uma pesquisada na docu-
mentação do LangChain e verificar se alguém já não criou uma tool para a mesma finalidade, só então
comece a criar uma tool própria!
Nesta aula, vamos, portante:
• Conhecer as ferramentas padrão do LangChain.
• Aprender a utilizar essas ferramentas padrões.
• Entender as diferentes formas de importar uma tool no LangChain.
• Explorar exemplos práticos de uso das tools.
Explorando Tools Padrão
A biblioteca LangChain já possui diversas ferramentas padrão construídas que podemos utilizar. Elas
podem ser verificadas neste link. Vamos mostrar como utilizar algumas.
ArXiv
Esta ferramenta utiliza a biblioteca do arXiv para retornar resumos de artigos científicos de um deter-
minado tema solicitado. Temos três formas em geral para chamar uma tool, da mais baixo a mais alto
nível:
1. Criando a tool utilizando o Wrapper: No LangChain foram criados diferentes wrappers para
APIs e bibliotecas externas que facilitam a utilização das mesmas e permitem uma rápida criação
de uma nova tool. Ela é mais customizável, pois podemos modificar as descrições e argumentos
da tool às nossas necessidades, além de podermos modificar facilmente os parâmetros do
wrapper.
2. Instanciando a tool já criada: Em geral, uma tool pronta já está criada dentro da biblioteca e
podemos acessá-la diretamente.
3. Utilizando o load_tools:
O LangChain possui uma ferramenta especial chamada
load_tools que permite o carregamento de diversas ferramentas ao mesmo tempo.
Vamos explorar os três métodos agora:
Asimov Academy
52


---