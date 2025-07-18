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
## Página 56

Criando Multi Agent Systems com CrewAI
está disponível dentro de sua inteligência. É como se os modelos vivessem sempre há um ano atrás
do dia de hoje, ignorando completamente a informação nova que ocorreu neste último ano. Por isso,
quando tentamos gerar código para bibliotecas novas, como a própria CrewAI, os códigos estão sem‑
pre desatualizados, pois o modelo ignora toda evolução da biblioteca no último ano.
Paracontornaressalimitação, podemoscriarferramentasdebuscadeinformações. Algunsexemplos
incluem:
• Ferramentas de web crawl para buscar na internet informações recentes.
• Ferramentas de acesso a bancos de dados, oferecendo ao modelo acesso a informações em
diversos tipos de banco de dados, como SQL, Postgres, MongoDB, etc.
• Ferramentas de leitura de arquivos de texto, arquivos PDF, CSV, etc.
• Ferramentas de acesso a informações de APIs diversas, como APIs de clima, trânsito, tráfego
aéreo, etc.
Tools de atuação
Agora estamos falando de dar mais autonomia aos modelos. Queremos que nossos modelos possam
gerar soluções além da geração de texto — queremos que eles interajam, atuem e modifiquem seu
entorno. É aqui que entram as tools de atuação, capazes de mudar o estado de aplicações e sistemas
fora do escopo da aplicação. São ferramentas que atuam no mundo real.
Alguns exemplos incluem:
• Ferramentas para enviar um e‑mail, uma mensagem SMS, ou uma mensagem no WhatsApp ou
Telegram.
• Ferramentas para adicionar ou deletar dados de diversos bancos de dados, como SQL, Postgres,
MongoDB, etc.
• Ferramentas para criar e deletar arquivos em um computador.
• Ferramentas para criação de imagens, áudio, etc.
Como usar tools?
Para usar as Tools no CrewAI, você precisa começar instalando o pacote de ferramentas adicionais.
Basta rodar o seguinte comando no seu terminal:
pip install 'crewai[tools]'
Aqui está um exemplo de como você pode usar algumas Tools no seu código:
import os
from crewai import Agent, Task, Crew
Asimov Academy
55


---