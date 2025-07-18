## Página 54

Criando Multi Agent Systems com CrewAI
Conclusão
Quando falamos de observabilidade, estamos tocando em algo super importante para quem quer
criar aplicações inteligentes com o CrewAI. Ter essa capacidade de observar e entender o que está
acontecendo com seus agentes é fundamental para garantir que tudo esteja rodando direitinho. O
AgentOps é uma ótima opção com suas ferramentas de rastreamento, replay e análise, ele se torna
um aliado indispensável para quem deseja desenvolver sistemas que realmente funcionem bem.
Nas próximas aulas, vamos entender juntos como você pode usar essas habilidades de observabil‑
idade em projetos práticos. Vamos aprender a melhorar a performance dos seus agentes e, conse‑
quentemente, a experiência de quem interage com eles.
Asimov Academy
53


---
## Página 55

Criando Multi Agent Systems com CrewAI
11. Tools de CrewAI
Vocês devem se lembrar das duas principais características de um agente: raciocinar e agir através de
ferramentas.
Até agora, mostramos como criar um sistema multiagentes, adicionando passos e momentos para
que ele reflita, o que por si só já aumenta muito a capacidade de uma aplicação. Mas ainda não
falamos nada do segundo elemento fundamental: as ações!
Como um modelo age?
Os modelos necessitam de um meio para conseguir agir. Lembrando que eles são modelos de lin‑
guagem; portanto, recebem texto como input e devolvem texto como output. Os modelos, por si só,
não têm a habilidade de executar uma ação que não seja gerar texto. Mas como então fornecemos a
eles uma maior capacidade de ação, como acessar um banco de dados ou enviar um e‑mail ou men‑
sagem no celular? É aí que entra o conceito de desenvolvimento de ferramentas, mais conhecidas
pelo termo em inglês: tools!
O que são as tools?
As tools são funções construídas através da programação que são descritas e fornecidas aos modelos
delinguagem. Comofalamosanteriormente, omodeloporsisónãoconsegueexecutarumatool,mas
eleécapazdeentenderqueexisteumatooldentrodosistemaqueelepodesolicitarquesejaacionada
quando necessário. A tool roda dentro do sistema que está chamando o modelo de linguagem. No
nosso caso, seria o nosso próprio computador.
O modelo entende que existe uma tool através da descrição que criamos dela. Ele percebe sua utili‑
dade através da descrição que é enviada junto ao prompt, e, ao ver a necessidade de buscar uma in‑
formação externa ou atuar de alguma forma, ele se utiliza das tools previamente criadas para isso.
Os dois principais tipos de tools
Eu gosto de separar as tools em duas categorias: tools de busca de informação e tools de atuação.
Tools de captura de informação
Uma das grandes limitações dos modelos de linguagem é que sua informação é limitada aos dados
de treinamento. Toda nova informação que surja após o treinamento do modelo de linguagem não
Asimov Academy
54


---