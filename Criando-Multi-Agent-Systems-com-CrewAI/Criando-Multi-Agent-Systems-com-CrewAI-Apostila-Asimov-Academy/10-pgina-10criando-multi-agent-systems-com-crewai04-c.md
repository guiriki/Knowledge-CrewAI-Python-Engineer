## Página 10

Criando Multi Agent Systems com CrewAI
04. Criação de Agents, Tasks e Crews no CrewAI
A primeira aplicação de IA que eu criei aqui para a empresa foi um criador de posts de blog. Automa‑
tizamos o nosso processo de criação de artigos e, com isso, em menos de 6 meses, geramos mais de
600 posts. O site que recebia 100 acessos orgânicos passou a ter 2 mil.
Crescimento do número de páginas orgânicas
Aumento no número de Cliks
A partir desse case, percebemos que precisávamos desenvolver uma trilha de IA aqui na Asimov. O
poderdessasLLMs(LargeLanguageModels)combinadasàprogramaçãoémuitoimpactante; oganho
de produtividade que tivemos foi incrível e sentimos a necessidade de compartilhar essa experiência
com nossos alunos.
Em homenagem a esta pequena história, decidi criar uma Crew de desenvolvimento de posts de blog
como um primeiro exemplo para vocês.
Asimov Academy
9


---
## Página 11

Criando Multi Agent Systems com CrewAI
Na aula de hoje, nós finalmente iremos para o código. Aprenderemos como criar Agents, Tasks e uma
Crew que os combine, em seu estado mais simples. Apesar de começarmos de forma elementar, a
aplicação já será muito interessante e prática.
Overview da aplicação
Nesta aula, vamos desenvolver uma Crew que consiste em quatro agents, cada um com tasks especí‑
ficas que serão responsáveis por executar. Teremos os seguintes agents:
• Desenvolvedor de Ideias: responsável por gerar ideias criativas.
• Planejador de Conteúdo: encarregado de planejar o conteúdo.
• Escritor do Post: responsável pela redação do post.
• Revisor do Post: que revisa o texto finalizado.
Asimov Academy
10


---