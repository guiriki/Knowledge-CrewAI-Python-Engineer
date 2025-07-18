## Página 43

Criando Multi Agent Systems com CrewAI
09. Projeto ‑ Refinando a crew para criar crews
Bem‑vindos de volta, pessoal! Finalizamos agora os elementos básicos de CrewAI e já vamos começar
a pensar na criação de estruturas para produção. Pois nosso objetivo é criar soluções que realmente
serão utilizadas; então, quando quisermos oferecê‑las ao mundo, elas precisam estar prontas!
Para facilitar este processo, a CrewAI criou recentemente uma nova estrutura de construção de uma
Crew, baseada em arquivos YAML. De início, isso pode assustar um pouco, pois há uma complexidade
maior na forma como os arquivos são organizados. Porém, eles são mais limpos, modularizados e
facilitam a manutenção do projeto.
Iniciando um projeto
ComoCrewAIinstaladonoseuambiente, vocêganhaacessoaalgunscomandoscriadosnabiblioteca.
Vamos utilizar o comando create para iniciar um novo projeto. Para isso, abra um terminal e digite:
crewai create crew projeto_teste
No exemplo, demos o nome do projeto como projeto_teste, mas você pode modificar para um
nome que faça sentido para a sua aplicação.
Primeiro, será solicitado que você selecione o provedor de modelos que será utilizado no seu projeto,
e você perceberá que temos diversas opções no caso do CrewAI:
Asimov Academy
42


---
## Página 44

Criando Multi Agent Systems com CrewAI
Eu digitei “1” para selecionar a OpenAI, e depois vamos para a seleção do modelo da OpenAI que será
utilizado:
Selecionei o gpt-4o-mini para este projeto!
Por último, será solicitado que você forneça uma API KEY do provedor que você selecionou:
Em geral, eu deixo vazio e forneço a API key manualmente após a estrutura ser criada.
E pronto! A estrutura do projeto estará criada dentro da pasta com o nome do projeto que você
forneceu; no nosso caso, projeto_teste.
Analisando a estrutura do projeto
A estrutura criada será a seguinte:
projeto_teste/
├── .gitignore
├── pyproject.toml
├── README.md
├── .env
└── src/
└── projeto_teste/
├── __init__.py
├── main.py
├── crew.py
├── tools/
│
├── custom_tool.py
Asimov Academy
43


---