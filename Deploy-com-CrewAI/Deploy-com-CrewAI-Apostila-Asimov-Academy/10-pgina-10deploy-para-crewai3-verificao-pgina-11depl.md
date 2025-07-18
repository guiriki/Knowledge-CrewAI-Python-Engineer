## Página 10

Deploy para CrewAI
3. Verificação:
Certifique‑se de que o remote foi adicionado corretamente e que a branch principal (geral‑
mente, main) está configurada para sincronização com o repositório GitHub.
Realizando o Push para o GitHub
• Com o remote configurado, clique em “Push” para enviar todas as alterações do repositório
local para o GitHub.
• Verifique, na interface web do GitHub, se os arquivos apareceram corretamente e se os arquivos
sensíveis (como .env) foram devidamente ignorados.
Conclusão e Próximos Passos
• Revisão:
Aqui, você aprendeu a transformar a pasta do projeto local em um repositório Git, configurar
o .gitignore para garantir que arquivos sensíveis ou desnecessários sejam ignorados e sin‑
cronizar o repositório com o GitHub.
• Próximas Etapas:
A seguir, veremos como realizar o deploy do seu projeto utilizando o CrewAI Enterprise, que fará
a conexão e a execução do deploy a partir do repositório do GitHub.
Asimov Academy
9


---
## Página 11

Deploy para CrewAI
04. Fazendo deploy de uma crew
Nesta aula, vamos realizar o deploy da nossa crew utilizando o CrewEnterprise (a plataforma de de‑
ploy para crews). O processo é intuitivo e, embora possa levar alguns minutos, é bastante simples.
Nosso objetivo é conectar o repositório hospedado no GitHub (onde já publicamos nosso projeto)
à plataforma CreaEnterprise, configurar as variáveis de ambiente necessárias e lançar o deploy da
nossa API.
Acessando o CrewAi Enterprise
1. Entrando na Plataforma:
• Acesse o CrewAI Enterprise
• Faça o login na plataforma.
• Se você ainda não configurou o GitHub dentro do CrewAI Enterprise, siga as instruções
passo a passo que o próprio site oferece. Essa configuração permitirá que o serviço acesse
os repositórios de sua conta.
2. Conectando o Repositório:
• Após configurar o GitHub, aparecerá a opção Deploy your crews from GitHub.
• Selecione o repositório referente ao projeto que criamos anteriormente (no exemplo,
“crew for Deploy”).
• A plataforma reconhecerá automaticamente a branch principal (geralmente, a branch
main).
Configurando Variáveis de Ambiente
Embora o arquivo .env com as variáveis não seja enviado para o repositório (por segurança), é funda‑
mental que o deploy receba esses dados. O CreaEnterprise oferece uma interface para configurar as
environment variables manualmente.
1. Adicionando as Variáveis:
• Localize a seção de Env_Var_Keys.
• Adicione a sua OpenAI API key; esse valor deve ser copiado do seu arquivo .env local.
Asimov Academy
10


---