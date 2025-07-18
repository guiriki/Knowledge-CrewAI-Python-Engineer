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
## Página 12

Deploy para CrewAI
• Adicione também a variável model, por exemplo, “gpt4omini”.
Dica: Configure as variáveis‑chave como padrão, para facilitar o processo em deploys fu‑
turos.
2. Confirmando a Configuração:
• Verifique se todas as variáveis necessárias foram adicionadas corretamente.
• Uma vez configuradas, clique em Deploy para iniciar o processo.
Realizando o Deploy
1. Iniciando o Deploy:
• Após configurar as variáveis, clique no botão Deploy.
• O processo de deploy iniciará e aparecerá um status indicando que ele está in progress.
• O tempo para a conclusão do deploy pode variar: na primeira execução, o processo pode
demorar até 10 minutos ou um pouco mais.
2. Monitoramento e Logs:
• Durante o deploy, o painel do CreaEnterprise exibirá logs e mensagens de status.
• Caso ocorra algum erro (por exemplo, instabilidade do servidor ou deployment error), há a
opção de redeploy para reiniciar o processo sem que seja necessário modificar qualquer
arquivo local ou no repositório.
3. Finalização do Deploy:
• Quando o deploy for concluído com sucesso, o status deverá indicar algo como “CREWAI
IS ONLINE” (ou similar).
• Mesmo que inicialmente tenha ocorrido algum erro, ao efetuar um redeploy, o sistema
normalmente completa o processo sem grandes modificações.
Considerações Finais e Próximos Passos
• Revisão do Processo:
Você aprendeu como conectar o repositório do GitHub ao CrewAI Enterprise, configurar as var‑
iáveis de ambiente necessárias e realizar o deploy da sua crew.
Asimov Academy
11


---