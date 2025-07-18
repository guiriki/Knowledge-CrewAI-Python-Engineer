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
## Página 45

Criando Multi Agent Systems com CrewAI
│
└── __init__.py
└── config/
├── agents.yaml
└── tasks.yaml
Temos alguns arquivos principais que precisamos entender para utilizar as Crews nesta estrutura:
Arquivo
Finalidade
agents.yaml
Define seus agentes de IA e seus papéis
tasks.yaml
Configura tarefas e fluxos de trabalho dos agentes
.env
Armazena chaves de API e variáveis de ambiente
main.py
Ponto de entrada do projeto e fluxo de execução
crew.py
Orquestração e coordenação da equipe
tools/
Diretório para ferramentas personalizadas de agentes
Arquivo .env
Vamos começar analisando o arquivo .env.
Você pode perceber que aqui é definido o modelo que o nosso sistema utilizará. Como definimos no
início o gpt-4o-mini, o comando create já preenche o arquivo com o modelo que solicitei.
Neste arquivo, também adicionamos a chave de API do provedor. No final, teremos um arquivo
como:
MODEL=gpt-4o-mini
OPENAI_API_KEY=MINHA_CHAVE_DE_API
No caso da OpenAI, o nome para fornecer a key é OPENAI_API_KEY. Este nome varia conforme o
provedor!
Asimov Academy
44


---