## Página 81

Agents de IA com Python e LangChain
Invoking: `sql_db_query` with `{'query': 'SELECT Artist.Name, COUNT(Album.AlbumId) AS
Number_of_Albums FROM Artist JOIN Album ON Artist.ArtistId = Album.ArtistId GROUP BY
Artist.ArtistId ORDER BY Number_of_Albums DESC LIMIT 1'}`
�→
�→
[('Iron Maiden', 21)]O artista que possui mais álbuns é "Iron Maiden", com um total de 21
álbuns.
�→
> Finished chain.
{'input': 'Qual artista possui mais albuns?',
'output': 'O artista que possui mais álbuns é "Iron Maiden", com um total de 21 álbuns.'}
Podemos ver que o agente é capaz de realizar queries complexas a base de dados, e tudo de forma
muito simples!
Neste capítulo, aprendemos a criar agents utilizando Toolkits para analisar DataFrames e bases de
dados SQL. Vimos como esses Toolkits podem simplificar e automatizar tarefas complexas de análise
de dados. Esperamos que vocês tenham gostado e que essas ferramentas sejam úteis no dia a dia de
vocês.
Asimov Academy
80


---
## Página 82

Agents de IA com Python e LangChain
15. Finalizando o curso
E assim encerramos o nosso curso. Muito obrigado, meus amigos, por terem ficado até aqui. Parabéns
a vocês pela determinação em percorrer essa jornada, que eu sei que não foi fácil. Mas vocês sabem
que quanto mais difícil a jornada, mais recompensador é chegar ao final. Então, parabéns!
Gostaria de pedir um favor a vocês: deixem nos comentários da aula, o que vocês acharam que faltou
no curso, o que gostariam de ver em termos de aplicações, como vocês estão pensando em utilizar os
seus agentes, quais dúvidas têm em geral sobre agentes e como utilizá-los. Isso nos ajudará a melhorar
nosso curso, desenvolver mais aulas e criar projetos conforme as necessidades de vocês.
Queremos que cada vez mais vocês deem feedback, retornem para nós o que estão pensando e como
estão utilizando as IAs, para que possamos customizar bem o nosso conteúdo conforme as suas
necessidades. Então, fica aqui esse pedido para vocês.
Para consolidar bem o que aprendemos, fica sempre aquela dica: apliquem, tentem, exercitem, porque
senão vocês vão acabar esquecendo tudo. Claro, vocês sempre podem recorrer novamente ao nosso
curso e aos nossos materiais para reaprender, mas o melhor mesmo para consolidar é aplicar e
tentar criar agentes para as suas aplicações. Assim, tenho certeza de que tudo o que fizemos será
consolidado.
Muito obrigado novamente e nos vemos nos nossos próximos cursos e projetos aqui na Asimov. Grande
abraço!
Asimov Academy
81