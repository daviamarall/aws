**NEW QUESTION 1**
Quais são os principais benefícios das instâncias EC2 sob demanda? (Selecione todas as opções que se aplicam) Escolha as 2 respostas corretas:

A. São a opção de compra mais barata.

B. São a opção de compra mais flexível.

C. Requerem de 1 a 2 dias para configuração e instalação.

D. Criar, iniciar, parar e encerrar a qualquer momento.

Resposta: BD

Explicação:
As instâncias EC2 sob demanda são amplamente utilizadas devido à sua flexibilidade. Você pode criar, iniciar, parar e encerrar a qualquer momento (sem taxas de inicialização ou encerramento).
No entanto, devido a essa flexibilidade, elas são a opção de compra mais cara.

**NEW QUESTION 2**

Qual serviço da AWS você deve usar se desejar configurar um alarme de faturamento da AWS? Escolha a resposta correta.

A. CloudWatch

B. CloudMonitor

C. Faturamento consolidado


D. CloudTrail

Resposta: A
Explicação:
O CloudWatch é o serviço da AWS que permite coletar métricas e criar alarmes com base nessas métricas. As métricas de faturamento podem ser rastreadas no CloudWatch, portanto, é possível criar alarmes de faturamento.

**NEW QUESTION 3**

Quanta dados você pode armazenar no S3?

Escolha a resposta correta.

A. A capacidade de armazenamento é virtualmente ilimitada.

B. Você pode armazenar até 1 petabyte de dados.

C. Cada conta recebe 50 gigabytes de capacidade de armazenamento e não pode usar mais.

D. Você pode armazenar até 1 petabyte de dados, depois disso é necessário pagar uma taxa adicional.
Resposta: A
Explicação:
Embora teoricamente exista um limite de capacidade, como usuário do S3, não há limite para a quantidade de dados que você pode armazenar no S3.

**NEW QUESTION 4**

A alta administração de sua empresa está ficando muito nervosa em relação à gestão de governança, conformidade e auditoria de riscos na AWS. Que serviço você deve habilitar e informar à alta administração?
Escolha a resposta correta.

A. CloudAudit

B. CloudTrail

C. CloudCompliance


D. CloudWatch

Resposta: B

Explicação:
O AWS CloudTrail é projetado para registrar todas as ações realizadas em sua conta da AWS. Isso fornece um ótimo recurso para governança, conformidade e auditoria de riscos.

**NEW QUESTION 5**

O que significa S3? Escolha a resposta correta.

A. Simple Storage Service (Serviço de Armazenamento Simples)

B. Simplified Storage Service (Serviço de Armazenamento Simplificado)

C. Simple Store Service (Serviço de Armazenamento Simples)

D. Service for Simple Storage (Serviço para Armazenamento Simples)

Resposta: A

**NEW QUESTION 6**

Qual classe de armazenamento da AWS deve ser usada para armazenamento de longo prazo e arquivamento?

Escolha a resposta correta.

A. Glacier

B. Long-Term

C. Padrão

D. Acesso Infrequente

Resposta: A

Explicação:
O Glacier deve ser usado (e é especificamente projetado) para armazenamento de longo prazo e arquivamento.

**NEW QUESTION 7**

Qual é o serviço de computação sem servidor da AWS?

Escolha a resposta correta.

A. S3

B. Lambda

C. EC2

D. Nenhum dos anteriores

Resposta: B

Explicação:
A AWS tem dois principais serviços de computação, o EC2 (baseado em servidor) e o Lambda (sem servidor).

**NEW QUESTION 8**

Qual é a classificação de disponibilidade e durabilidade da classe de armazenamento Padrão do S3?

Escolha a resposta correta.

A. Durabilidade de 99,999999999% e disponibilidade de 99,99%

B. Disponibilidade de 99,999999999% e durabilidade de 99,90%

C. Disponibilidade de 99,999999999% e durabilidade de 99,99%

D. Durabilidade de 99,999999999% e disponibilidade de 99,00%

Resposta: A

Explicação:

A classe de armazenamento Padrão do S3 tem uma classificação de durabilidade de 99,999999999% (referida como 11 noves) e uma disponibilidade de 99,99%.



**NEW QUESTION 9**

As classes de armazenamento do S3 são classificadas por quais duas categorias de métricas? (Selecione duas opções) Escolha as 2 respostas corretas:

A. Objetividade

B. Durabilidade

C. Disponibilidade

D. Tolerância a falhas

Resposta: BC

Explicação:

Cada classe de armazenamento do S3 é classificada com base em sua disponibilidade e durabilidade.



**NEW QUESTION 10**

Se um objeto estiver armazenado na classe de armazenamento Padrão do S3 e você quiser movê-lo para o Glacier, o que você deve fazer para migrá-lo corretamente?

Escolha a resposta correta.

A. Excluir o objeto e carregá-lo novamente, selecionando o Glacier como classe de armazenamento.

B. Criar uma política de ciclo de vida que o migre após um mínimo de 30 dias.

C. Alterar diretamente a classe de armazenamento no objeto.

D. Nenhuma das opções anteriores

Resposta: B

Explicação:

Qualquer objeto carregado no S3 deve primeiro ser colocado em uma das classes de armazenamento Padrão, Redundância Reduzida ou Acesso Infrequente. Depois de estar no S3, a única maneira de mover o objeto para o Glacier é através de uma política de ciclo de vida.



**NEW QUESTION 11**

Qual serviço da AWS possui mitigação integrada contra DDoS (Negação de Serviço Distribuída)?

Escolha a resposta correta.

A. CloudFront

B. CloudTrail

C. CloudWatch

D. EC2

Resposta: A

Explicação:

Com o CloudFront, você armazena em cache o conteúdo nos locais de borda, o que protege sua infraestrutura de aplicativos subjacente contra ataques DDoS.



**NEW QUESTION 12**

Quais são os principais benefícios de usar o Lambda? (Selecione todas as opções que se aplicam) Escolha as 2 respostas corretas:

A. Pagar apenas pelo tempo de computação que você consome.

B. Grande variedade de sistemas operacionais para escolher.

C. Selecionar e gerenciar ativamente o tipo de instância e a capacidade.

D. Executar código sem provisionamento de servidor.

Resposta: AD

Explicação:

O Lambda, sendo a plataforma de computação sem servidor da AWS, significa que não existem servidores, tipos de instância ou capacidade para selecionar. Tudo isso é gerenciado para você. Com o Lambda, você paga apenas pelo tempo em que seu código está realmente sendo executado.



**NEW QUESTION 15**

Se você tem um conjunto de arquivos acessados com frequência que são usados diariamente, em qual classe de armazenamento do S3 você deve armazená-los?

Escolha a resposta correta.

A. Acesso Infrequente

B. Redundância Reduzida

C. Padrão

D. Acesso Rápido

Resposta: C

Explicação:

A classe de armazenamento Padrão deve ser usada para arquivos que você acessa diariamente ou com muita frequência.



**NEW QUESTION 16**

O que afetará o preço que você paga por uma instância EC2? (Selecione todas as opções que se aplicam) Escolha as 3 respostas corretas:

A. Tipo de instância.

B. Classe de armazenamento selecionada.

C. Por quanto tempo você usa a instância.

D. Amazon Machine Image (AMI).

Resposta: ACD

Explicação:

A precificação das instâncias EC2 varia dependendo de muitas variáveis. 1) O tipo de opção de compra 2) AMI selecionada 3) Tipo de instância selecionada 4) Região 5) Dados de entrada/saída 6) Capacidade de armazenamento



**NEW QUESTION 19**

O que você deve fazer se acreditar que sua conta da AWS foi comprometida? (Selecione todas as opções que se aplicam) Escolha as 4 respostas corretas:

A. Excluir quaisquer recursos em sua conta que você não tenha criado.

B. Responder a quaisquer notificações que você tenha recebido da AWS por meio do AWS Support Center.

C. Alterar todas as senhas dos usuários IAM.

D. Excluir ou girar todas as chaves de acesso programáticas (API).

Resposta: ABCD

Explicação:

Todas essas respostas são ações que você deve tomar se acreditar que sua conta foi comprometida.



**NEW QUESTION 21**

Qual é o propósito do serviço Route 53 da AWS? (Selecione todas as opções que se aplicam) Escolha as 2 respostas corretas:

A. Armazenamento de conteúdo.

B. Gerenciamento de banco de dados.

C. Registro de domínio.

D. Serviço de Sistema de Nomes de Domínio (DNS) da AWS.

Resposta: CD

Explicação:

O Route 53 é o serviço de gerenciamento de domínio e DNS da AWS. Você pode usá-lo para registrar novos nomes de domínio e gerenciar conjuntos de registros DNS.



**NEW QUESTION 22**

David está gerenciando um aplicativo da web executado em dezenas de servidores EC2. Ele está preocupado que, se algo der errado com um dos servidores, ele não será informado de maneira oportuna. Que solução você pode oferecer para ajudá-lo a se manter atualizado sobre o status de seus servidores?

Escolha a resposta correta.

A. Configure cada instância EC2 com um script personalizado para enviar um e-mail para David quando ocorrerem problemas.

B. Configure notificações RDS com base em alarmes de métricas EC2 do CloudWatch.

C. Ative o CloudTrail para registrar e relatar quaisquer problemas que ocorram com as instâncias EC2.

D. Configure notificações SNS com base em alarmes de métricas EC2 do CloudWatch.

Resposta: D

Explicação:

O CloudWatch é usado para rastrear métricas em todas as instâncias EC2. Os alarmes de métricas podem ser configurados para acionar mensagens SNS se algo der errado.



**NEW QUESTION 23**

Qual termo descreve melhor o conceito de escalabilidade?

Escolha a resposta correta.

A. A capacidade de um sistema resistir a uma determinada quantidade de falhas e ainda permanecer funcional.

B. A capacidade de um sistema crescer em tamanho, capacidade e/ou escopo.

C. A capacidade de um sistema crescer e diminuir com base na demanda.

D. A capacidade de um sistema ser acessível quando você tenta acessá-lo.

Resposta: B

Explicação:

Escalabilidade refere-se ao conceito de um sistema poder escalar facilmente (e de maneira econômica). Para aplicativos da web, isso significa a capacidade de adicionar facilmente capacidade de servidor quando a demanda exige.



**NEW QUESTION 26**

Qual é a relação entre a infraestrutura global da AWS e o conceito de alta disponibilidade?

Escolha a resposta correta.

A. A AWS está localizada centralmente em um único local e está sujeita a interrupções generalizadas se algo acontecer nesse único local.

B. As regiões e Zonas de Disponibilidade da AWS permitem a criação de arquitetura redundante em partes isoladas do mundo.

C. Cada região da AWS lida com diferentes serviços da AWS, e você deve usar todas as regiões para usar totalmente a AWS.

D. Nenhuma das opções acima

Resposta: B

Explicação:

Como usuário da AWS, você pode criar a infraestrutura de seu aplicativo e duplicá-la. Ao colocar infraestrutura duplicada em várias regiões, a alta disponibilidade é criada, porque se uma região falhar, você terá um backup (em outra região) para usar.



**NEW QUESTION 30**

Se você tem uma grande coleção de objetos reproduzíveis, em qual classe de armazenamento do S3 você deve armazená-los se o custo for sua prioridade?

Escolha a resposta correta.

A. Glacier

B. Padrão

C. Redundância Reduzida

D. Nenhuma das opções acima

Resposta: C

Explicação:

A classe de armazenamento Redundância Reduzida tem a menor durabilidade de todas as classes de armazenamento. Isso significa que os objetos armazenados nesta classe têm a maior probabilidade de serem perdidos. Portanto, você deve armazenar objetos nesta classe apenas se puder reproduzi-los facilmente. Em troca da durabilidade mais 
baixa, o custo é menor do que na classe de armazenamento Padrão.



**NEW QUESTION 32**

O que é o Marketplace de AMIs da EC2?

Escolha a resposta correta.

A. Onde você seleciona o tipo de armazenamento de uma instância EC2.

B. Uma coleção de AMIs da EC2 pagas que geralmente vêm com software empresarial licenciado.

C. Onde você armazena AMIs que você cria.

D. Onde você seleciona a capacidade de computação de uma instância EC2.

Resposta: B



**NEW QUESTION 37**

Jacky está criando um site usando a infraestrutura da AWS. Ela tem uma ótima ideia para um nome de domínio, mas precisa verificar se ele está disponível e, se estiver, registrá-lo. Que serviço da AWS permitirá que ela faça isso?

Escolha a resposta correta.

A. CloudFront

B. DomainServices

C. CloudWatch

D. Route 53

Resposta: D

Explicação:

O Route 53 é o serviço de gerenciamento de domínio e DNS da AWS. (DomainServices não existe).



**NEW QUESTION 42**

No S3, como é chamado um arquivo que você faz upload?

Escolha a resposta correta.

A. Arquivo estático.

B. Bucket.

C. Pasta.

D. Objeto.

Resposta: D

Explicação:

Os arquivos armazenados no S3 são chamados de objetos.



**NEW QUESTION 45**

Qual serviço de banco de dados da AWS é usado para armazenamento de dados de petabytes?

Escolha a resposta correta.

A. RDS

B. Elasticache

C. Redshift

D. DynamoDB

Resposta: C

Explicação:

O Redshift é um data warehouse totalmente gerenciado que é perfeito para armazenar petabytes de dados.



**NEW QUESTION 49**

Qual é a principal diferença entre os serviços de banco de dados RDS e DynamoDB da AWS?

Escolha a resposta correta.

A. O RDS oferece opções de banco de dados NoSQL, e o DynamoDB oferece opções de banco de dados SQL.

B. O RDS oferece apenas uma opção de banco de dados SQL, e o DynamoDB oferece muitas opções de banco de dados NoSQL.

C. O RDS oferece opções de banco de dados SQL, e o DynamoDB oferece apenas uma opção de banco de dados NoSQL.

D. Nenhuma das opções acima

Resposta: C

Explicação:

O RDS é um serviço de banco de dados SQL (que oferece várias opções de mecanismo de banco de dados), enquanto o DynamoDB é uma opção de banco de dados NoSQL que oferece apenas um mecanismo NoSQL.



**NEW QUESTION 54**

Se você deseja monitorar o uso médio de CPU de suas instâncias EC2, qual serviço da AWS você deve usar?

Escolha a resposta correta.

A. CloudMonitor

B. CloudTrail

C. CloudWatch

D. Nenhum dos acima

Resposta: C

Explicação:

O CloudWatch é usado para coletar, visualizar e rastrear métricas de recursos (como instâncias EC2) em sua conta da AWS.



**NEW QUESTION 59**

Se você deseja que notificações por SMS ou e-mail sejam enviadas para vários membros de seu departamento com atualizações de status sobre recursos em sua conta da AWS, que serviço você deve escolher?

Escolha a resposta correta.

A. STS

B. RDS

C. GetSMS

D. SNS

Resposta: D

Explicação:

O Simple Notification Service (SNS) é o que publica mensagens para endpoints SMS e/ou e-mail.



**NEW QUESTION 63**

Qual serviço da AWS usa uma combinação de editores e assinantes?

Escolha a resposta correta.

A. SNS

B. RDS

C. EC2

D. Lambda

Resposta: A

Explicação:

No SNS, existem dois tipos de clientes: editores e assinantes. Os editores enviam a mensagem, e os assinantes recebem a mensagem.



**NEW QUESTION 68**

Qual termo melhor descreve o modelo de preços da AWS?

Escolha a resposta correta.

A. Pague tudo antecipadamente.

B. Pague conforme o uso.

C. Pague tudo no final.

D. Nenhuma das opções acima

Resposta: B

Explicação:

A AWS opera com um modelo de pagamento conforme o uso. Sem custos antecipados ou taxas de término.



**NEW QUESTION 73**

Quais categorias são analisadas pelo programa AWS Trusted Advisor? (Selecione todas as opções que se aplicam) Escolha as 2 respostas corretas:

A. Tolerância a falhas

B. Escalabilidade

C. Otimização de custos

D. Nenhuma das opções acima

Resposta: AC

Explicação:

O programa AWS Trusted Advisor analisará sua conta com verificações nas seguintes categorias: Otimização de custos, Desempenho, Segurança e Tolerância a falhas.

