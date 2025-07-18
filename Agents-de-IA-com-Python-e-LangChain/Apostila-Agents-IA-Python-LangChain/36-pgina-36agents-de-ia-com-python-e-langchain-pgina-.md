## Página 36

Agents de IA com Python e LangChain
'autor': 'Renata Lopes',
'data': '15-05-24'},
Ecomextremafacilidadeconseguimosestruturarinformaçõescapturadasdepáginaswebcombinando
Web Scraping com modelos de linguagem.
E é isso, pessoal! Vimos como é possível extrair informações específicas de textos e páginas web
utilizando Python e LangChain. Essas técnicas são extremamente úteis para transformar dados não
estruturados em informações organizadas e utilizáveis.
Desafio
Após este conteúdo sobre extração de informações utilizando LLMs, quero propor um desafio para
vocês! É um exercício simples e bem pedagógico, mas a ideia é reforçar o aprendizado de vocês e
mostrar como as LLMs podem ser utilizadas até nas atividades mais simples do cotidiano.
Vamos aplicar o que aprendemos e extrair dados da seguinte receita que encontrei na internet. Após a
extração, vamos criar uma lista de compras. Pensem que este poderia ser muito facilmente o primeiro
passo para um agente que faz compras automaticamente ao fornecermos uma receita para ele. A
receita que temos é a seguinte:
Receita de Bolo de Cenoura
Massa 1. Em um liquidificador, adicione a cenoura, os ovos e o óleo, depois misture. 2. Acrescente o
açúcar e bata novamente por 5 minutos. 3. Em uma tigela ou na batedeira, adicione a farinha de trigo
e depois misture novamente. 4. Acrescente o fermento e misture lentamente com uma colher. 5. Asse
em um forno preaquecido a 180° C por aproximadamente 40 minutos. Cobertura 6. Despeje em uma
tigela a manteiga, o chocolate em pó, o açúcar e o leite, depois misture. 7. Leve a mistura ao fogo e
continue misturando até obter uma consistência cremosa, depois despeje a calda por cima do bolo.
O que você precisa fazer?
A partir da receita acima, você deve extrair as seguintes informações:
• Utensílios de Cozinha: Liste todos os utensílios que são mencionados na receita (por exemplo,
liquidificador, tigela, batedeira).
• Ingredientes: Liste todos os ingredientes necessários para preparar o bolo (por exemplo, ce-
noura, ovos, óleo, açúcar, farinha de trigo, fermento, manteiga, chocolate em pó, leite).
• Salvar em CSV: Após extrair as informações, salve os dados de ingredientes em um arquivo CSV
e os utensílios em outro.
Asimov Academy
35


---
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