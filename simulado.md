# Pergunta 1 

Ao criar um bucket S3, quais regras devem ser seguidas em relação ao nome do bucket? (Selecione todas as opções corretas) Escolha as 2 respostas corretas:

A. Os nomes dos buckets devem ser exclusivos em toda a AWS.

B. Os nomes dos buckets devem ter entre 3 e 63 caracteres de comprimento.

C. Os nomes dos buckets devem conter pelo menos uma letra maiúscula.

D. Os nomes dos buckets podem ser formatados como endereços IP.

**Resposta**: AB

**Explicação**:
Embora algumas regiões permitam letras maiúsculas no nome do bucket, letras maiúsculas NÃO são obrigatórias. Além disso, um nome de bucket não pode ser formatado como um endereço IP. 

# Pergunta 2
Qual serviço da AWS você deve usar se desejar configurar um alarme de faturamento da AWS? Escolha a resposta correta

A. CloudWatch

B. CloudMonitor

C. Faturamento consolidado

D. CloudTrail

Resposta: A
Explicação:
O CloudWatch é o serviço da AWS que permite coletar métricas e criar alarmes com base nessas métricas. As métricas de faturamento podem ser rastreadas no CloudWatch, portanto, é possível criar alarmes de faturamento.

# Pergunta 3
Quais DOIS serviços/recursos são necessários para ter uma arquitetura altamente disponível e tolerante a falhas na AWS? Escolha as 2 respostas corretas:

A. Balanceador de carga elástico

B. CloudFront

C. ElastiCache

D. Auto Scaling

Resposta: AD

# Pergunta 4
Qual classe de armazenamento do S3 possui a classificação de disponibilidade mais baixa para objetos?
Escolha a resposta correta

A. Padrão

B. Redundância Reduzida

C. Acesso Infrequente

D. Todas têm a mesma classificação de disponibilidade

Resposta: C
Explicação:
O acesso infrequente tem a classificação de disponibilidade mais baixa (99,90%). Padrão e Redundância Reduzida têm uma classificação de disponibilidade de 99,99%.

# Pergunta 5

O que afetará o custo de armazenamento de objetos no S3? Escolha as 2 respostas corretas:

A. A classe de armazenamento usada para os objetos armazenados.

B. A criptografia de dados (objetos) armazenados no S3.

C. Criação e exclusão de buckets do S3

D. O tamanho total em gigabytes de todos os objetos armazenados
Resposta: AD

# Pergunta 6

Kim está gerenciando uma aplicação web executada na nuvem AWS. A aplicação está atualmente utilizando oito servidores EC2 como plataforma de computação. Hoje de manhã, dois desses servidores web travaram; no entanto, nenhum de seus clientes foi afetado. O que Kim fez corretamente nesse cenário?
Escolha a resposta correta

A. Construiu adequadamente um sistema elástico.

B. Construiu adequadamente um sistema escalável.

C. Construiu adequadamente um sistema tolerante a falhas.

D. Nenhuma das alternativas acima

Resposta: C
Explicação:
Um sistema tolerante a falhas é aquele que pode suportar uma certa quantidade de falhas e ainda permanecer operacional.

# Pergunta 7

O que descreve melhor o teste de penetração?

Escolha a resposta correta

A. Testar a capacidade de sua aplicação de penetrar em outras aplicações.

B. Testar o acesso de usuários IAM aos serviços da AWS.

C. Testar sua própria rede/aplicação em busca de vulnerabilidades.

D. Nenhuma das alternativas acima

Resposta: C

# Pergunta 8

O que descreve melhor o que é a AWS?

Escolha a resposta correta

A. A AWS é um varejista online.

B. A AWS é a nuvem.

C. A AWS é um provedor de serviços em nuvem.

D. Nenhuma das alternativas acima

Resposta: C

# Pergunta 9

Stephen está tendo problemas para rastrear o quanto de capacidade de computação sua aplicação está usando. Idealmente, ele deseja rastrear e receber alarmes quando a utilização da CPU ultrapassar 70%. O que Stephen deve fazer para conseguir isso?
Escolha a resposta correta

A. Configurar um tópico SNS com um limite de alarme definido para disparar quando a utilização da CPU for superior a 70%.

B. Configurar um alarme CloudWatch com um limite de alarme definido para disparar quando a utilização da CPU for superior a 70%.

C. Configurar um alarme CloudWatch com um limite de alarme definido para disparar quando a utilização da CPU for superior ou igual a 70%.

D. Nenhuma das alternativas acima

Resposta: B

Explicação:
A resposta é configurar um alarme CloudWatch com um limite de alarme definido para disparar quando a utilização da CPU for superior a 70%. Isso exibirá o alarme no estado "alarme" quando a utilização da CPU for superior a 70%. Esta pergunta foi formulada de forma muito específica com as palavras "ultrapassar 70%", o que desqualifica a resposta que afirmou "superior ou igual a 70%". O exame AWS terá perguntas muito complicadas como esta.

# Pergunta 10

Qual é a classificação de disponibilidade e durabilidade da classe de armazenamento S3 Standard?

Escolha a resposta correta

A. Durabilidade de 99,999999999% e disponibilidade de 99,99%

B. Disponibilidade de 99,999999999% e durabilidade de 99,90%

C. Disponibilidade de 99,999999999% e durabilidade de 99,99%

D. Durabilidade de 99,999999999% e disponibilidade de 99,00%

Resposta: A

Explicação:
A classe de armazenamento S3 Standard possui uma classificação de durabilidade de 99,999999999% (11 noves) e uma disponibilidade de 99,99%.

# Pergunta 11
Se um objeto estiver armazenado na classe de armazenamento S3 Standard e você desejar movê-lo para o Glacier, o quevocê deve fazer para migrá-lo corretamente?

Escolha a resposta correta

A. Excluir o objeto e fazer o upload novamente, selecionando o Glacier como classe de armazenamento.

B. Criar uma política de ciclo de vida que o migre após um mínimo de 30 dias.

C. Alterar a classe de armazenamento diretamente no objeto.

D. Nenhuma das alternativas acima

Resposta: B
Explicação:
Qualquer objeto carregado no S3 deve primeiro ser colocado em uma das classes de armazenamento: Padrão, Redundância Reduzida ou Acesso Infrequente. Uma vez no S3, a única maneira de mover o objeto para o Glacier é por meio de uma política de ciclo de vida.

# Pergunta 14
Quais são os benefícios principais do AWS Relational Database Service (RDS)? (Selecione todas as opções corretas) Escolha as 3 respostas corretas:

A. Capacidade redimensionável

B. Atualizações e backups automatizados

C. Eficiência de custos

D. Nenhuma das alternativas acima

Resposta: ABC

# Pergunta 19

Thomas está gerenciando os direitos de acesso e credenciais de todos os funcionários que têm acesso à conta AWS de sua empresa. Esta manhã, ele foi notificado de que algumas dessas contas podem ter sido comprometidas e agora ele precisa alterar a política de senha e gerar uma nova senha para todos os usuários. Qual serviço da AWS Thomas precisa usar para realizar isso?
Escolha a resposta correta

A. Política e Gerenciamento de Acesso

B. Elastic Cloud Compute

C. Gerenciamento de Acesso

D. Nenhuma das alternativas acima

Resposta: D
Explicação:
O Gerenciamento de Identidade e Acesso (IAM) é o serviço da AWS onde as políticas de senha e as credenciais do usuário são gerenciadas. (Política e Gerenciamento de Acesso como serviço não existem).

# Pergunta 20

Quais são os principais benefícios de usar o Lambda? (Selecione todas as opções corretas) Escolha as 2 respostas corretas:

A. Pagar apenas pelo tempo de computação que você consome.

B. Uma ampla variedade de sistemas operacionais para escolher.

C. Selecionar e gerenciar ativamente o tipo e a capacidade da instância.

D. Executar código sem provisionar servidores.

Resposta: AD
Explicação:
O Lambda, sendo a plataforma de computação sem servidor da AWS, significa que não há servidores, tipos de instância ou capacidade para selecionar. Isso é gerenciado para você. Com o Lambda, você paga apenas pelo tempo em que seu código está sendo executado.

# Pergunta 21

David está gerenciando uma aplicação web executada em dezenas de servidores EC2. Ele está preocupado que, se algo der errado com um dos servidores, ele não saberá a tempo. Que solução você pode oferecer para ajudá-lo a se manter atualizado sobre o status de seus servidores?
Escolha a resposta correta

A. Configurar cada instância EC2 com um script personalizado para enviar um e-mail para David quando ocorrerem problemas.

B. Configurar notificações RDS com base em alarmes métricos EC2 do CloudWatch.

C. Habilitar o CloudTrail para registrar e relatar problemas que ocorrem com as instâncias EC2.

D. Configurar notificações SNS com base em alarmes métricos EC2 do CloudWatch.

Resposta: D
Explicação:

O CloudWatch é usado para rastrear métricas em todas as instâncias EC2. Alarmes métricos podem ser configurados para acionar mensagens SNS se algo der errado.

# Pergunta 22

Qual recurso da AWS age como um regulador de distribuição de tráfego, garantindo que cada instância EC2 em um sistema receba a mesma quantidade de tráfego?
Escolha a resposta correta

A. Zona de disponibilidade

B. ELB (Balanceador de Carga Elástico)

C. NACL (Lista de Controle de Acesso à Rede)

D. Auto Scaling

Resposta: B

Explicação:
Um Balanceador de Carga Elástico (ELB) é responsável por distribuir uniformemente o tráfego da web recebido entre todas as instâncias EC2 associadas a ele. Isso ajuda a evitar que um servidor fique sobrecarregado de tráfego, enquanto outro permanece subutilizado.

# Pergunta 23

Mike está configurando a infraestrutura para uma aplicação web que requer três instâncias EC2 para lidar com a demanda esperada. No entanto, ao testar a aplicação, Mike percebe que todo o tráfego está sendo roteado para apenas uma das instâncias. Que recurso da AWS ele deve adicionar à aplicação para distribuir o tráfego uniformemente entre todas as três instâncias?
Escolha a resposta correta

A. Balanceador de Carga Elástico (ELB)

B. Auto Scaling

C. Route 53

D. CloudFront

Resposta: A

Explicação:
Um Balanceador de Carga Elástico (ELB) é projetado para distribuir uniformemente o tráfego da web recebido entre todos os servidores associados a ele.

# Pergunta 24

Karen está criando um site que deverá ter um mínimo de 1000 usuários continuamente ao longo de 24 horas. Durante 8 horas por dia, espera-se que o tráfego seja de aproximadamente 1800 usuários. Quais opções de compra de instâncias EC2 ela deve usar para lidar com todo o tráfego e ser mais econômica?

Escolha a resposta correta

A. Karen deve depender exclusivamente de instâncias spot, pois essa será a opção mais barata.

B. Karen deve comprar instâncias reservadas com capacidade suficiente para lidar com todos os 1800 usuários e talvez comprar um pouco mais de capacidade apenas para garantia.

C. Karen deve comprar instâncias reservadas com capacidade suficiente para cobrir a base de 1000 usuários e, em seguida, contar com instâncias sob demanda para o período de 8 horas de tráfego aumentado todos os dias.

D. Karen deve comprar instâncias reservadas com capacidade suficiente para cobrir a base de 1000 usuários e, em seguida, contar com instâncias spot para o período de 8 horas de tráfego aumentado todos os dias.

Resposta: C

Explicação:
As instâncias reservadas devem ser usadas para lidar com o tráfego básico esperado para o site. As instâncias reservadas (em termos de 1/3 de ano) podem ser adquiridas com um desconto significativo em relação às instâncias sob demanda. Qualquer tráfego variável acima da base deve ser tratado com instâncias sob demanda (pois podem ser adicionadas/removidas a qualquer momento, com base na demanda atual). Instâncias spot não devem ser usadas nesse cenário.

# Pergunta 33

Quais são as DUAS principais camadas de segurança (firewalls) usadas dentro de um VPC? Escolha as 2 respostas corretas:

A. NetProtect

B. Lista de Controle de Acesso à Rede (NACL)

C. Grupo de Segurança (Security Group)

D. Listas de Segurança

Resposta: BC

Explicação:
As Listas de Controle de Acesso à Rede (NACL) atuam como um firewall no nível do sub-rede, e os Grupos de Segurança atuam como um firewall no nível da instância.

# Pergunta 37
Qual é o principal benefício do CloudFront?

Escolha a resposta correta

A. Gerenciamento de DNS

B. Armazenamento ilimitado

C. Capacidade de computação sem servidor

D. Proteção integrada contra DDoS

Resposta: D

Explicação:
O CloudFront permite que você armazene conteúdo em locais de borda. Quando uma solicitação é feita para esse conteúdo, a solicitação é enviada para um local de borda (não para o hardware de sua aplicação), portanto, os locais de borda absorverão qualquer ataque DDoS e protegerão seu hardware subjacente.

# Pergunta 39

Um Local de Borda é um centro de dados especializado da AWS que funciona em conjunto com qual serviço da AWS?
Escolha a resposta correta

A. Route 53

B. CloudWatch

C. Lambda

D. CloudFront

Resposta: D

Explicação:
O CloudFront é composto por uma rede de Locais de Borda (onde o conteúdo é armazenado em cache).

# Pergunta 42

O que é o Marketplace de AMI da AWS?

Escolha a resposta correta

A. Onde você seleciona o tipo de armazenamento de uma instância EC2.

B. Uma coleção de AMIs (Amazon Machine Images) pagas que geralmente são fornecidas com software empresarial licenciado.

C. Onde você armazena AMIs que cria.

D. Onde você seleciona a capacidade de computação de uma instância EC2.

Resposta: B

# Pergunta 45

Jacky está criando um site usando a infraestrutura da AWS. Ela tem uma ótima ideia para um nome de domínio, mas precisa verificar se ele está disponível e, se estiver, registrá-lo. Qual serviço da AWS permitirá que ela faça isso?
Escolha a resposta correta

A. CloudFront

B. DomainServices

C. CloudWatch

D. Route 53

Resposta: D

Explicação:
O Route 53 é o serviço da AWS para gerenciamento de domínios e DNS. (DomainServices não existe).

# Pergunta 46

Kunal está logado na conta AWS de sua empresa. Ele tenta acessar o EC2, mas está recebendo um erro. Qual é a razão mais provável pela qual ele não consegue acessar o EC2?
Escolha a resposta correta

A. Não há uma política de acesso IAM anexada ao seu usuário IAM.

B. Ele não faz parte de um Grupo IAM.

C. Ele não tem autenticação de vários fatores (MFA) ativada.

D. Não há uma política de acesso IAM anexada à sua função IAM.

Resposta: A
Explicação:
Quando um usuário IAM é criado, esse usuário NÃO tem acesso a nenhum serviço da AWS. Para ganhar acesso a um servidor AWS, um usuário IAM deve ter permissão concedida a ele. Isso é feito anexando uma política de acesso IAM ao usuário IAM (ou por meio de um grupo anexado). No entanto, apenas fazer parte de um grupo não concede acesso. Uma política adequada deve ser anexada a esse grupo.

# Pergunta 50

No S3, como é chamado o arquivo que você faz o upload?
Escolha a resposta correta

A. Arquivo estático

B. Bucket

C. Pasta

D. Objeto

Resposta: D

Explicação:
Os arquivos armazenados no S3 são chamados de objetos.

# Pergunta 55

Donna precisa provisionar um servidor Linux para executar uma aplicação web. Qual serviço da AWS ela deve usar para criar o servidor Linux?
Escolha a resposta correta

A. VPC (Virtual Private Cloud)

B. Lambda

C. IAM (Identity and Access Management)

D. EC2 (Elastic Cloud Compute)

Resposta: D

Explicação:
O Elastic Cloud Compute (EC2) da AWS é uma plataforma de computação baseada em servidores. Você pode usá-lo para provisionar e usar servidores com base em Linux e Windows.

# Pergunta 57

Qual é o nome do mecanismo de banco de dados SQL da RDS da AWS?

Escolha a resposta correta

A. Lightsail

B. SNS (Simple Notification Service)

C. MySQL

D. Aurora

Resposta: D

Explicação:
A AWS criou seu próprio mecanismo de banco de dados SQL personalizado, chamado Aurora.

# Pergunta 59

Qual é o serviço de banco de dados relacional da AWS?

Escolha a resposta correta

A. Redshift

B. DynamoDB

C. ElastiCache

D. RDS (Relational Database Service)

Resposta: D

Explicação:
O RDS oferece opções de banco de dados SQL, também conhecidas como bancos de dados relacionais.

# Pergunta 63

Se você deseja aprender sobre as melhores práticas arquiteturais ou de segurança da AWS, onde encontrará esse tipo de informação?

Escolha a resposta correta

A. AWS Yellow Pages

B. Seção de Informações da AWS Console

C. White Papers da AWS

D. Documentação de Serviço da AWS

Resposta: C

# Pergunta 64

O que você DEVE fazer antes de realizar qualquer teste de penetração em sua conta?

Escolha a resposta correta

A. Os testes de penetração não são permitidos.

B. Entre em contato com a AWS e informe-os primeiro.

C. Nada, você está livre para fazer testes de penetração quando quiser.

D. Nenhuma das alternativas acima

Resposta: B

Explicação:
Antes de realizar qualquer teste de penetração em sua conta AWS, é importante entrar em contato com a AWS e obter autorização.

# Pergunta 65

Qual é o mecanismo de busca global altamente escalável da AWS?

Escolha a resposta correta

A. CloudWatch

B. CloudFront

C. CloudSearch

D. Elasticsearch

Resposta: D

Explicação:
Elasticsearch é um mecanismo de busca altamente escalável disponível na AWS.

# Pergunta 66

O que o Amazon CloudWatch oferece aos desenvolvedores da AWS?

Escolha a resposta correta

A. Uma maneira de criar servidores virtuais na nuvem.

B. Uma plataforma de análise de big data.

C. Uma maneira de monitorar recursos e aplicativos, coletar e rastrear métricas e definir alarmes.

D. Nenhuma das alternativas acima

Resposta: C
Explicação:
O Amazon CloudWatch é um serviço de monitoramento que permite monitorar recursos e aplicativos, coletar e rastrear métricas e definir alarmes.

# Pergunta 67

O que é uma zona de disponibilidade da AWS?

Escolha a resposta correta

A. Uma área geográfica na qual a AWS opera um ou mais data centers.

B. Uma instância EC2 com capacidade computacional adicional.

C. Um local onde o CloudWatch armazena métricas.

D. Nenhuma das alternativas acima

Resposta: A

Explicação:
Uma zona de disponibilidade é uma área geográfica na qual a AWS opera um ou mais data centers.

# Pergunta 68

Quando você deve usar uma instância EC2 com uma única instância?

Escolha a resposta correta

A. Quando você precisa de alta disponibilidade e tolerância a falhas.

B. Quando você está testando o ambiente AWS pela primeira vez.

C. Quando você tem uma carga de trabalho simples que não precisa de redundância.

D. Nenhuma das alternativas acima

Resposta: C

Explicação:
Você deve usar uma instância EC2 com uma única instância quando tem uma carga de trabalho simples que não precisa de alta disponibilidade e tolerância a falhas. Para alta disponibilidade, é comum usar instâncias EC2 em grupos de Auto Scaling.

# Pergunta 69

Qual é o principal benefício do Amazon S3?

Escolha a resposta correta

A. Capacidade de computação sem servidor.

B. Armazenamento de dados altamente escalável e durável.

C. Um banco de dados relacional totalmente gerenciado.

D. Proteção contra ataques DDoS.

Resposta: B

Explicação:
O principal benefício do Amazon S3 é o armazenamento de dados altamente escalável e durável.

# NOVA PERGUNTA 70

O que VOCÊ DEVE fazer antes de realizar qualquer teste de penetração em sua conta?
Escolha a Resposta Correta

A. Testes de penetração agora são permitidos.

B. Entre em contato com a AWS e informe-os primeiro.

C. Nada, você está livre para fazer testes de penetração quando quiser.

D. Nenhuma das alternativas acima

Resposta: B
Explicação:
Você deve entrar em contato com a AWS antes de realizar qualquer teste de penetração em sua conta. Se você não notificar a AWS primeiro, eles podem desativar sua conta.

# NOVA PERGUNTA 71

Quais dos seguintes são Planos de Suporte AWS? (Selecione todas as respostas corretas) Escolha as 3 Respostas Corretas:

A. Enterprise

B. Expert

C. Basic

D. Business

Resposta: ACD

Explicação:
A AWS possui quatro níveis de planos de suporte: Basic (Básico), Developer (Desenvolvedor), Business (Negócios) e Enterprise (Empresarial).

# NOVA PERGUNTA 75

Qual é o principal benefício da faturação consolidada?

Escolha a Resposta Correta

A. Resposta mais rápida do suporte técnico da AWS.

B. Obter um desconto por volume para uso em todas as suas contas da AWS.

C. Acesso a um nível de plano de suporte superior.

D. Nenhuma das alternativas acima

Resposta: B

Explicação:
A faturação consolidada permite que você visualize, gerencie e pague faturas de várias contas da AWS em uma única interface de usuário. Descontos por volume podem ser obtidos combinando o uso de todas as contas que você possui.

# NOVA PERGUNTA 79

O que descreve melhor a diferença entre o Calculador de TCO e o Cost Explorer?

Escolha a Resposta Correta

A. O Calculador de TCO ajuda a analisar as cobranças atuais de uso da AWS; o Cost Explorer ajuda a estimar a economia de custos de usar a AWS.

B. O Calculador de TCO ajuda a estimar a economia de custos de usar a AWS; o Cost Explorer ajuda a analisar as cobranças atuais de uso da AWS.

C. O Cost Explorer ajuda a calcular o custo de uso do EC2 por hora; o Calculador de TCO é uma lista de preços para cada serviço da AWS.

D. O Cost Explorer é uma lista de preços para cada serviço da AWS; o Calculador de TCO ajuda a calcular o custo de uso do EC2 por hora.

Resposta: B

Explicação:

O Calculador de TCO é uma ferramenta gratuita fornecida pela AWS que permite estimar a economia de custos de usar a AWS em comparação com o uso de um centro de dados local. O Cost Explorer é uma ferramenta gratuita que permite visualizar as cobranças de custo (ajuda a analisar onde você está gastando dinheiro).

# NOVA PERGUNTA 81

O que significa TCO?

Escolha a Resposta Correta

A. Contagem de Custo de Propriedade

B. Propriedade Contínua Total

C. O Custo de Propriedade

D. Nenhuma das alternativas acima
Resposta: D

Explicação:
TCO significa Total Cost of Ownership (Custo Total de Propriedade).
