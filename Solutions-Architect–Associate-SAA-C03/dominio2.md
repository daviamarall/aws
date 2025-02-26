## Domínio 2: Design de arquiteturas resilientes
### Declaração de tarefa 2.1: Projetar arquiteturas dimensionáveis e com acoplamento fraco.

### 📌 **Criação e Gerenciamento de APIs com Amazon API Gateway**  

O **Amazon API Gateway** é um serviço totalmente gerenciado que permite criar, publicar, manter, monitorar e proteger APIs RESTful e WebSocket em escala. Ele funciona como um intermediário entre os clientes (front-end, mobile apps, IoT) e os serviços de back-end (Lambda, ECS, DynamoDB, etc.).

---

## ✅ **Principais Recursos do API Gateway**
1. **Suporte a múltiplos protocolos** → API REST, HTTP e WebSocket.  
2. **Integração com AWS Lambda** → Criação de APIs serverless.  
3. **Controle de Acesso** → Autenticação com **IAM**, **Cognito** e **JWT**.  
4. **Monitoramento** → Integração com **AWS CloudWatch** para logs e métricas.  
5. **Caching** → Redução de chamadas ao back-end para melhorar a performance.  
6. **Throttling e Rate Limiting** → Proteção contra abuso/excesso de requisições.  
7. **Suporte a múltiplos backends** → Pode se conectar a Lambda, EC2, ECS, DynamoDB, etc.  

---

## 🔹 **Exemplo 1: Criando uma API REST com API Gateway e AWS Lambda**
Vamos criar uma API RESTful simples que retorna um JSON usando **AWS API Gateway + Lambda**.  

### **1️⃣ Criar a função Lambda no AWS Lambda**
1. Acesse o **AWS Lambda** e clique em **Create Function**.
2. Escolha **Author from scratch**.
3. Defina um nome, ex: `MinhaAPIFunc`.
4. Selecione a runtime **Python 3.9** (ou outra de sua preferência).
5. No código da Lambda, insira o seguinte:

```python
import json

def lambda_handler(event, context):
    return {
        "statusCode": 200,
        "headers": {"Content-Type": "application/json"},
        "body": json.dumps({"message": "Olá, mundo!"})
    }
```
6. Salve a função.

---

### **2️⃣ Criar a API no API Gateway**
1. Acesse o **Amazon API Gateway** e clique em **Create API**.
2. Escolha **REST API** e clique em **Build**.
3. Defina um nome, ex: `MinhaAPI`.
4. Selecione **Regional** e clique em **Create API**.
5. Vá em **Actions → Create Resource**, nomeie como `hello`.
6. Com o recurso criado, clique em **Create Method**, selecione `GET` e clique na marca de check.
7. Em **Integration type**, escolha **Lambda Function** e insira o nome `MinhaAPIFunc`.
8. Clique em **Save** e **Deploy API**.

Agora, sua API pode ser acessada por um endpoint gerado pelo API Gateway.

---

## 🔹 **Exemplo 2: Criando uma API HTTP para conectar ao ALB (Application Load Balancer)**
Se sua aplicação roda em **EC2 ou ECS**, você pode criar uma **API HTTP** no API Gateway que se conecta a um **Application Load Balancer (ALB)**.

1. **Crie uma API HTTP** no API Gateway.
2. **Crie um recurso** com o caminho `/api`.
3. **Crie um método GET** e escolha **Integration Type → HTTP**.
4. **Insira o endpoint do ALB** (ex: `http://meu-load-balancer.com`).
5. **Deploy API** e agora as requisições para o API Gateway serão direcionadas para o ALB.

---

## 🔹 **Melhores Práticas no API Gateway**
✔ **Habilite Caching** → Para reduzir a carga no back-end.  
✔ **Implemente autenticação** → Use Cognito para autenticar usuários.  
✔ **Configure Rate Limiting** → Evita sobrecarga e ataques DDoS.  
✔ **Use Stages (Dev, Test, Prod)** → Para controle de versões da API.  
✔ **Integre com CloudWatch** → Para monitoramento e troubleshooting.

---

### 📌 **AWS Managed Services e Casos de Uso**  

Os serviços gerenciados da AWS ajudam a reduzir a complexidade operacional, permitindo que você foque no desenvolvimento sem se preocupar com manutenção de infraestrutura. Vamos abordar três serviços importantes:

- **AWS Transfer Family**  
- **Amazon Simple Queue Service (SQS)**  
- **AWS Secrets Manager**  

---

## 🔹 **1. AWS Transfer Family (SFTP, FTPS, FTP)**
O **AWS Transfer Family** é um serviço gerenciado para transferência segura de arquivos via **SFTP, FTPS e FTP**, permitindo a integração com **Amazon S3 ou Amazon EFS**.  

📌 **Casos de Uso:**  
✅ Transferência de arquivos entre parceiros de negócios via SFTP.  
✅ Automação de uploads e downloads de arquivos.  
✅ Substituição de servidores FTP tradicionais.  

📌 **Exemplo prático:**  
1. Criar um **servidor SFTP gerenciado**.  
2. Configurar um bucket S3 como destino dos arquivos.  
3. Adicionar usuários com permissões específicas para acesso ao SFTP.  
4. Automatizar a transferência com AWS Lambda ou AWS DataSync.  

---

## 🔹 **2. Amazon SQS (Simple Queue Service)**
O **Amazon SQS** é um serviço de **fila de mensagens** que desacopla componentes de aplicações distribuídas, garantindo que mensagens sejam processadas de forma **assíncrona**.  

📌 **Casos de Uso:**  
✅ Processamento de pedidos em sistemas de e-commerce.  
✅ Fila de tarefas para execução assíncrona (ex: transcodificação de vídeos).  
✅ Comunicação entre microsserviços sem dependências diretas.  

📌 **Exemplo prático:**  
1. Criar uma fila no SQS.  
2. Um serviço envia mensagens para a fila (Producer).  
3. Outro serviço consome essas mensagens (Consumer).  

🔹 **Exemplo de envio de mensagem para uma fila SQS via AWS SDK (Python/Boto3):**  

```python
import boto3

sqs = boto3.client('sqs')
queue_url = 'https://sqs.us-east-1.amazonaws.com/123456789012/minha-fila'

response = sqs.send_message(
    QueueUrl=queue_url,
    MessageBody='Processar pedido #123'
)

print("Mensagem enviada com ID:", response['MessageId'])
```

🔹 **Exemplo de leitura de mensagens do SQS:**  

```python
response = sqs.receive_message(QueueUrl=queue_url, MaxNumberOfMessages=1)

for message in response.get('Messages', []):
    print("Recebida:", message['Body'])
    sqs.delete_message(QueueUrl=queue_url, ReceiptHandle=message['ReceiptHandle'])
```

---

## 🔹 **3. AWS Secrets Manager (Armazenamento Seguro de Credenciais)**
O **AWS Secrets Manager** gerencia credenciais de forma segura, permitindo rotação automática de chaves de banco de dados, credenciais de API e outros segredos.

📌 **Casos de Uso:**  
✅ Armazenamento seguro de credenciais de banco de dados.  
✅ Gestão de tokens de API sem precisar armazená-los no código-fonte.  
✅ Rotação automática de senhas para aumentar a segurança.  

📌 **Exemplo prático:**  
1. Criar um segredo no AWS Secrets Manager.  
2. Configurar permissões IAM para que um serviço acesse o segredo.  
3. Recuperar o segredo dinamicamente no código da aplicação.  

🔹 **Exemplo de recuperação de um segredo no Python com Boto3:**  

```python
import boto3
import json

client = boto3.client('secretsmanager')

response = client.get_secret_value(SecretId='meu-segredo')

secrets = json.loads(response['SecretString'])
print("Usuário:", secrets['username'])
print("Senha:", secrets['password'])
```

---

## 🎯 **Resumo**
✔ **AWS Transfer Family** → Transferência segura de arquivos (SFTP, FTPS, FTP).  
✔ **Amazon SQS** → Processamento assíncrono e desacoplamento de sistemas.  
✔ **AWS Secrets Manager** → Armazenamento seguro e rotação de credenciais.  

---

### 📌 **Estratégias de Armazenamento em Cache**  

O armazenamento em cache melhora o desempenho das aplicações, reduzindo a latência e aliviando a carga sobre bancos de dados e servidores de origem. A AWS fornece diversas soluções para caching:

🔹 **Amazon ElastiCache (Redis e Memcached)**  
🔹 **AWS CloudFront (CDN – Cache na borda)**  
🔹 **DynamoDB Accelerator (DAX)**  

---

## 🔹 **1. Amazon ElastiCache (Redis e Memcached)**
O **Amazon ElastiCache** fornece armazenamento em cache gerenciado para melhorar a escalabilidade de aplicações. Suporta **Redis** e **Memcached**.

📌 **Casos de Uso:**  
✅ Cache de consultas de banco de dados para reduzir leituras repetitivas.  
✅ Sessões de usuário armazenadas em memória para aplicações web.  
✅ Fila de mensagens em tempo real com Redis Pub/Sub.  

📌 **Exemplo prático:**  

### **🔹 Usando Redis como cache de banco de dados**
1. Criar uma instância **ElastiCache Redis**.  
2. Configurar a aplicação para armazenar e buscar dados no cache antes de consultar o banco.  

**Exemplo de uso do Redis com Python:**  

```python
import redis

redis_client = redis.StrictRedis(host='meu-cluster.cache.amazonaws.com', port=6379, decode_responses=True)

# Salvando um valor no cache
redis_client.set('chave_usuario_123', 'Davi Amaral', ex=3600)  # Expira em 1 hora

# Buscando do cache
usuario = redis_client.get('chave_usuario_123')
print(usuario)  # Retorna 'Davi Amaral'
```

🔹 **Benefícios:**  
✔ **Redis**: Suporte a estruturas de dados avançadas (listas, conjuntos ordenados, pub/sub).  
✔ **Memcached**: Melhor para **cache simples** e alta taxa de leitura.  

---

## 🔹 **2. AWS CloudFront (CDN – Cache na Borda)**
O **AWS CloudFront** é um serviço de **Content Delivery Network (CDN)** que armazena conteúdo em servidores distribuídos globalmente para melhorar a entrega e reduzir latência.  

📌 **Casos de Uso:**  
✅ Aceleração de sites, servindo imagens e vídeos mais rápido.  
✅ Cache de APIs REST para reduzir carga no backend.  
✅ Proteção contra ataques DDoS (AWS Shield integrado).  

📌 **Exemplo prático:**  

### **🔹 Cacheando objetos do S3**
1. Criar um **bucket no S3** e armazenar imagens estáticas.  
2. Criar uma distribuição CloudFront apontando para o S3.  
3. Configurar regras de cache para definir tempo de expiração.  

🔹 **Exemplo de URL antes e depois do CloudFront:**  
❌ **Antes:** `https://meu-bucket.s3.amazonaws.com/logo.png`  
✅ **Depois:** `https://d111111abcdef8.cloudfront.net/logo.png` (Cache na borda)  

---

## 🔹 **3. DynamoDB Accelerator (DAX)**
O **DynamoDB Accelerator (DAX)** é um cache de leitura otimizado para **Amazon DynamoDB**, reduzindo a latência para **microsegundos**.

📌 **Casos de Uso:**  
✅ Aplicações que exigem resposta rápida (exemplo: e-commerce).  
✅ Melhorar a performance de **workloads read-heavy**.  

📌 **Exemplo prático:**  
1. Criar um **cluster DAX** na AWS.  
2. Modificar o código da aplicação para usar DAX em vez do DynamoDB diretamente.  

🔹 **Exemplo de leitura usando DAX:**  

```python
import boto3

dax = boto3.client('dax')

response = dax.get_item(
    TableName='Pedidos',
    Key={'pedido_id': {'S': '1234'}}
)

print(response['Item'])
```

---

## 🎯 **Resumo**
✔ **ElastiCache (Redis e Memcached)** → Cache para bancos de dados e sessões.  
✔ **CloudFront** → CDN para entrega rápida de conteúdo.  
✔ **DAX para DynamoDB** → Cache de leitura de banco NoSQL.  

---

### **📌 Princípios de Design para Microsserviços**
Os microsserviços são um estilo arquitetônico onde uma aplicação é dividida em **pequenos serviços independentes**, que se comunicam entre si.  

🔹 **Principais características:**  
✅ **Desacoplamento**: Cada serviço tem uma responsabilidade clara.  
✅ **Escalabilidade**: Componentes podem escalar de forma independente.  
✅ **Resiliência**: Falha em um serviço não derruba a aplicação inteira.  
✅ **Desenvolvimento ágil**: Equipes podem trabalhar em serviços separados.  

---

## 🔹 **1. Stateless vs. Stateful**
A principal diferença está na **persistência de estado**.

🔹 **Stateless (Sem estado)**  
✔ O serviço não mantém informações da sessão entre requisições.  
✔ Facilita a escalabilidade horizontal (exemplo: AWS Lambda).  
✔ Exemplo: APIs REST, processamento em lote.  

🔹 **Stateful (Com estado)**  
✔ O serviço armazena informações de sessão entre requisições.  
✔ Normalmente requer persistência de dados (exemplo: Banco de dados).  
✔ Exemplo: Carrinho de compras, sessões de usuário.  

📌 **Exemplo de microsserviço stateless com AWS Lambda:**  

```python
import json

def lambda_handler(event, context):
    return {
        'statusCode': 200,
        'body': json.dumps("Olá, Mundo!")
    }
```

---

## 🔹 **2. Arquiteturas Orientadas a Eventos**
Arquiteturas orientadas a eventos utilizam **mensageria** e **publicação/assinatura** para comunicação assíncrona entre serviços.

🔹 **Serviços AWS para eventos:**  
✅ **Amazon SQS** → Fila de mensagens para desacoplamento.  
✅ **Amazon SNS** → Notificações push (publicação/assinatura).  
✅ **Amazon EventBridge** → Roteamento de eventos entre serviços AWS.  

📌 **Exemplo de arquitetura orientada a eventos:**  
1. **Usuário faz upload de uma imagem no S3**.  
2. **O S3 gera um evento para o Amazon EventBridge**.  
3. **O EventBridge aciona uma função Lambda para processar a imagem**.  
4. **Lambda salva os metadados no DynamoDB**.  

🔹 **Exemplo prático com SQS:**  

```python
import boto3

sqs = boto3.client('sqs')

queue_url = 'https://sqs.us-east-1.amazonaws.com/123456789012/minha-fila'

# Enviar mensagem
sqs.send_message(QueueUrl=queue_url, MessageBody='Novo pedido recebido')

# Ler mensagem
messages = sqs.receive_message(QueueUrl=queue_url)
print(messages)
```

---

## 🔹 **3. Escalabilidade Horizontal vs. Vertical**
🔹 **Escalabilidade Horizontal** (mais recomendada na AWS)  
✅ Adiciona **mais instâncias** para dividir a carga.  
✅ Melhor para microsserviços stateless.  
✅ Exemplo: Auto Scaling Groups no EC2, ECS Fargate.  

🔹 **Escalabilidade Vertical**  
✅ Aumenta os recursos da **mesma instância** (CPU, memória).  
✅ Boa opção para bancos de dados monolíticos.  
✅ Exemplo: Redimensionar uma instância do RDS.  

📌 **Exemplo de escalabilidade horizontal com Auto Scaling no EC2:**  
1. Criar um **Launch Template** para instâncias EC2.  
2. Configurar um **Auto Scaling Group** com regras de escalonamento.  
3. Definir um **Application Load Balancer** para distribuir requisições.  

---

## 🎯 **Resumo**
✔ **Microsserviços** são desacoplados e independentes.  
✔ **Stateless** facilita a escalabilidade, **stateful** armazena estado.  
✔ **Arquiteturas orientadas a eventos** usam **SNS, SQS e EventBridge**.  
✔ **Escalabilidade horizontal** adiciona instâncias, **vertical** aumenta recursos.  





---

### **📌 Conceitos de Balanceamento de Carga (Load Balancing)**
O balanceamento de carga é essencial para distribuir tráfego entre múltiplas instâncias, garantindo **alta disponibilidade, escalabilidade e resiliência**.

---

## 🔹 **1. Tipos de Load Balancer na AWS**
A AWS oferece diferentes tipos de Load Balancer dentro do serviço **Elastic Load Balancing (ELB)**:

| Tipo | Uso Principal | Características |
|------|--------------|----------------|
| **Application Load Balancer (ALB)** | Tráfego HTTP/HTTPS | Balanceia por camada 7 (Aplicação), suporta regras baseadas em conteúdo. |
| **Network Load Balancer (NLB)** | Tráfego TCP/UDP | Balanceia por camada 4 (Rede), baixa latência e alta performance. |
| **Classic Load Balancer (CLB)** | Legado | Suporta HTTP, HTTPS, TCP, mas substituído por ALB/NLB. |
| **Gateway Load Balancer (GWLB)** | Firewall e segurança | Redireciona tráfego para appliances de segurança (firewalls de terceiros). |

---

## 🔹 **2. Como Funciona o Application Load Balancer (ALB)?**
O **ALB** opera na camada de aplicação (**OSI Layer 7**) e pode distribuir tráfego baseado em **caminhos de URL, headers, métodos HTTP e hostnames**.

### 🔥 **Principais Recursos do ALB:**
✅ **Regras de roteamento baseadas em caminho (Path-Based Routing)** → `/login` vai para um serviço e `/checkout` para outro.  
✅ **Regras de roteamento baseadas em host (Host-Based Routing)** → `api.dominio.com` e `app.dominio.com` podem apontar para diferentes serviços.  
✅ **Suporte a WebSockets**.  
✅ **Compatível com contêineres** no **ECS** usando target groups dinâmicos.  

📌 **Exemplo de Roteamento Baseado em Caminho:**
```
- Tráfego para `/api/*` → ECS Service 1
- Tráfego para `/auth/*` → ECS Service 2
- Tráfego para `/static/*` → Amazon S3
```

---

## 🔹 **3. Exemplo Prático: Criando um Load Balancer via AWS CLI**
Para criar um **Application Load Balancer** e associar a um Target Group, usamos a AWS CLI:

### **1️⃣ Criar um Target Group**
```sh
aws elbv2 create-target-group \
    --name meu-target-group \
    --protocol HTTP \
    --port 80 \
    --vpc-id vpc-123456
```

### **2️⃣ Criar um Application Load Balancer**
```sh
aws elbv2 create-load-balancer \
    --name meu-load-balancer \
    --subnets subnet-12345 subnet-67890 \
    --security-groups sg-12345 \
    --scheme internet-facing \
    --type application
```

### **3️⃣ Criar uma Regra de Roteamento**
```sh
aws elbv2 create-listener \
    --load-balancer-arn arn:aws:elasticloadbalancing:us-east-1:123456789012:loadbalancer/app/meu-load-balancer/abc123 \
    --protocol HTTP \
    --port 80 \
    --default-actions Type=forward,TargetGroupArn=arn:aws:elasticloadbalancing:us-east-1:123456789012:targetgroup/meu-target-group/xyz789
```

---

## 🔹 **4. Conceito de Auto Scaling e Load Balancer**
O **Auto Scaling Group (ASG)** permite adicionar/remover instâncias automaticamente conforme a demanda.  
O Load Balancer **monitora e distribui** as requisições entre as instâncias.

📌 **Fluxo típico:**
1. **Tráfego aumenta** → ASG adiciona novas instâncias.
2. **Tráfego diminui** → ASG remove instâncias.
3. O **Load Balancer** distribui tráfego entre as instâncias saudáveis.

---

## 🎯 **Resumo**
✔ O **ALB** opera na camada 7 e permite roteamento baseado em conteúdo.  
✔ O **NLB** opera na camada 4 e tem baixa latência.  
✔ O **Auto Scaling Group** trabalha em conjunto com o Load Balancer para garantir escalabilidade.  
✔ Podemos configurar Load Balancers via **AWS CLI, Console ou Terraform**.  

---

### **📌 Arquiteturas Multicamadas (Multi-Tier Architectures)**
As arquiteturas multicamadas são amplamente usadas para **isolar componentes**, melhorar **segurança**, aumentar **escalabilidade** e garantir **alta disponibilidade**.

---

## 🔹 **1. O que é uma Arquitetura Multicamadas?**
Uma arquitetura **multi-tier** separa os componentes de uma aplicação em **diferentes camadas**, geralmente:  

✅ **Camada de Apresentação (Frontend)** → Interface gráfica, como React, Angular ou um site estático hospedado no Amazon S3 com CloudFront.  
✅ **Camada de Aplicação (Backend)** → Processamento de lógica de negócio, normalmente usando EC2, AWS Lambda ou ECS.  
✅ **Camada de Banco de Dados (Data Layer)** → Armazena dados em RDS (relacional), DynamoDB (NoSQL) ou Amazon S3.  

💡 **Benefícios da Arquitetura Multi-Tier:**  
✔ **Segurança** → Camadas isoladas, evitando exposição direta do banco de dados.  
✔ **Escalabilidade** → Cada camada pode escalar de forma independente.  
✔ **Alta Disponibilidade** → Se uma camada falha, o restante do sistema pode continuar funcionando.  

---

## 🔹 **2. Exemplo de Arquitetura Multicamadas na AWS**
📌 **Cenário:** Um site de e-commerce com backend e banco de dados.

🔹 **Camada de Apresentação (Frontend)**  
- Um site estático hospedado no **Amazon S3** e entregue via **CloudFront**.  
- Os clientes acessam `https://www.ecommerce.com`.

🔹 **Camada de Aplicação (Backend)**  
- Servidores EC2 rodando Node.js/Python/Java conectados ao banco.  
- O tráfego passa por um **Application Load Balancer (ALB)** antes de chegar nos servidores.  
- Lambda pode ser usado para partes serverless, como checkout.

🔹 **Camada de Banco de Dados (Data Layer)**  
- **Amazon RDS (MySQL/PostgreSQL)** para dados transacionais.  
- **Amazon DynamoDB** para sessões de usuário ou carrinho de compras.  
- **Amazon S3** para armazenar imagens de produtos.

---

## 🔹 **3. Implementação na AWS**
📌 **Criando uma arquitetura multicamadas com EC2, RDS e Load Balancer usando AWS CLI.**  

### **1️⃣ Criar um Load Balancer para a Camada de Aplicação**
```sh
aws elbv2 create-load-balancer \
    --name ecommerce-alb \
    --subnets subnet-1 subnet-2 \
    --security-groups sg-12345 \
    --scheme internet-facing \
    --type application
```

### **2️⃣ Criar um Auto Scaling Group para a Aplicação**
```sh
aws autoscaling create-auto-scaling-group \
    --auto-scaling-group-name ecommerce-app \
    --launch-template LaunchTemplateId=lt-123456 \
    --min-size 2 \
    --max-size 10 \
    --desired-capacity 2 \
    --vpc-zone-identifier subnet-1,subnet-2
```

### **3️⃣ Criar um Banco de Dados RDS**
```sh
aws rds create-db-instance \
    --db-instance-identifier ecommerce-db \
    --db-instance-class db.t3.micro \
    --engine mysql \
    --allocated-storage 20 \
    --master-username admin \
    --master-user-password StrongPassword123 \
    --vpc-security-group-ids sg-67890
```

---

## 🎯 **Resumo**
✔ Arquiteturas **multicamadas** isolam diferentes partes de um sistema.  
✔ O **Frontend** pode ser hospedado no S3 + CloudFront.  
✔ O **Backend** pode rodar em EC2, ECS ou Lambda com um **Load Balancer**.  
✔ O **Banco de Dados** pode ser RDS, DynamoDB ou S3, dependendo do caso de uso.  
✔ A AWS oferece serviços como **Auto Scaling, Load Balancers e Security Groups** para garantir escalabilidade e segurança.  

----

## **📌 Como Migrar Aplicações para Contêineres?**
Migrar uma aplicação tradicional (monolítica ou baseada em VMs) para **contêineres** melhora a **escalabilidade, portabilidade e eficiência**. A AWS oferece várias soluções para rodar contêineres, como **ECS, EKS e Fargate**.  

---

## **🔹 1. Etapas da Migração**
### 🔍 **Passo 1: Analisar a Aplicação**
Antes de migrar, identifique:  
✅ **Dependências** → Banco de dados, serviços externos, APIs.  
✅ **Estado da aplicação** → É **stateless** (sem persistência) ou **stateful** (precisa armazenar dados)?  
✅ **Ambiente de execução** → Atualmente roda em VMs (EC2), Bare Metal ou outro ambiente?  

💡 **Exemplo:**  
- Uma API REST rodando em **Node.js** com banco de dados **PostgreSQL**.
- Atualmente está em um **EC2**, mas queremos mover para **contêineres**.

---

### 🚀 **Passo 2: Containerizar a Aplicação**
Agora, criamos um **Dockerfile** para empacotar a aplicação.

📌 **Exemplo: Dockerfile para uma API Node.js**
```dockerfile
# Usando imagem oficial do Node.js
FROM node:18-alpine

# Definindo diretório de trabalho
WORKDIR /app

# Copiando arquivos da aplicação
COPY package.json package-lock.json ./
RUN npm install

# Copiando código-fonte
COPY . .

# Expondo porta
EXPOSE 3000

# Comando de inicialização
CMD ["node", "server.js"]
```

💡 **Testando o contêiner localmente:**
```sh
docker build -t minha-api .
docker run -p 3000:3000 minha-api
```

---

### 🔄 **Passo 3: Escolher um Serviço AWS para Rodar os Contêineres**
A AWS oferece **três principais opções** para rodar contêineres:  

1️⃣ **Amazon ECS (Elastic Container Service)** → Gerenciado pela AWS, mais fácil de configurar.  
2️⃣ **Amazon EKS (Elastic Kubernetes Service)** → Kubernetes gerenciado, ideal para ambientes multi-cloud.  
3️⃣ **AWS Fargate** → Sem necessidade de gerenciar servidores (serverless para contêineres).  

🔹 **Comparação rápida**:
| Serviço | Gerenciamento | Uso Principal |
|---------|--------------|--------------|
| **ECS** | Simples, AWS cuida da infraestrutura | Aplicações leves e fáceis de escalar |
| **EKS** | Kubernetes gerenciado | Quando precisa de Kubernetes (EKS = Kubernetes as a Service) |
| **Fargate** | Totalmente serverless | Quando não quer gerenciar servidores |

---

### 🏗 **Passo 4: Deploy na AWS**
#### 📌 **Opção 1: Deploy no Amazon ECS com Fargate**
Com o Fargate, não precisamos gerenciar servidores.

1️⃣ **Criar um repositório no Amazon Elastic Container Registry (ECR)**:
```sh
aws ecr create-repository --repository-name minha-api
```

2️⃣ **Autenticar no ECR e enviar a imagem Docker**:
```sh
aws ecr get-login-password | docker login --username AWS --password-stdin <ID_DA_CONTA>.dkr.ecr.us-east-1.amazonaws.com

docker tag minha-api <ID_DA_CONTA>.dkr.ecr.us-east-1.amazonaws.com/minha-api
docker push <ID_DA_CONTA>.dkr.ecr.us-east-1.amazonaws.com/minha-api
```

3️⃣ **Criar um cluster ECS com Fargate**:
```sh
aws ecs create-cluster --cluster-name minha-api-cluster
```

4️⃣ **Criar uma task definition para rodar o contêiner**:
```json
{
  "family": "minha-api-task",
  "containerDefinitions": [
    {
      "name": "minha-api",
      "image": "<ID_DA_CONTA>.dkr.ecr.us-east-1.amazonaws.com/minha-api",
      "memory": 512,
      "cpu": 256,
      "essential": true
    }
  ],
  "requiresCompatibilities": ["FARGATE"],
  "networkMode": "awsvpc",
  "cpu": "256",
  "memory": "512",
  "executionRoleArn": "arn:aws:iam::XXXXXXXXXX:role/ecsTaskExecutionRole"
}
```

5️⃣ **Executar a tarefa no ECS**:
```sh
aws ecs run-task --cluster minha-api-cluster --task-definition minha-api-task
```

🔹 Agora, sua API está rodando em **Fargate + ECS**! 🚀  

---

## **🎯 Resumo**
✔ **Containerizar a aplicação** com Docker.  
✔ **Escolher um serviço AWS** → ECS, EKS ou Fargate.  
✔ **Fazer deploy** com ECR + ECS.  
✔ **Gerenciar escalabilidade e segurança** com AWS Load Balancer e IAM Roles.  

---

## **📌 Conceitos de Enfileiramento e Sistema de Mensagens (Pub/Sub) na AWS**

### 🔹 O que é um Sistema de Mensagens?  
Um **sistema de mensagens** permite que diferentes partes de uma aplicação **comuniquem-se de forma assíncrona**, melhorando **escalabilidade, desacoplamento e resiliência**. Na AWS, existem duas abordagens principais:

1️⃣ **Fila de Mensagens (Enfileiramento - Point-to-Point)** → Exemplo: **Amazon SQS**  
2️⃣ **Publicação/Assinatura (Pub/Sub - Broadcast)** → Exemplo: **Amazon SNS**  

---

## **📌 1. Enfileiramento com Amazon SQS (Simple Queue Service)**
O **Amazon SQS** é um serviço de **fila de mensagens gerenciado**. Ele permite que aplicações enviem, armazenem e consumam mensagens de forma confiável.

📌 **Cenário:**  
Imagine que você tem um **sistema de pedidos** em um e-commerce. Quando um cliente faz um pedido, a API do e-commerce coloca a solicitação em uma fila, e um sistema de processamento de pedidos consome essas mensagens **assíncronamente**.

### 🏗 **Fluxo de Funcionamento do SQS**
1️⃣ **Produtor** → Envia uma mensagem para a fila.  
2️⃣ **SQS** → Armazena a mensagem até que seja processada.  
3️⃣ **Consumidor** → Lê a mensagem e a processa.  
4️⃣ **Mensagem é removida** da fila após o processamento.  

### 🔧 **Exemplo prático de SQS**
Criando uma **fila SQS** na AWS CLI:
```sh
aws sqs create-queue --queue-name minha-fila
```

Enviando uma **mensagem para a fila**:
```sh
aws sqs send-message --queue-url https://sqs.us-east-1.amazonaws.com/1234567890/minha-fila \
--message-body "Pedido #12345 - Cliente João"
```

Recebendo mensagens da fila:
```sh
aws sqs receive-message --queue-url https://sqs.us-east-1.amazonaws.com/1234567890/minha-fila
```

---

## **📌 2. Publicação/Assinatura com Amazon SNS (Simple Notification Service)**
O **Amazon SNS** permite um modelo **publicador/assinante (Pub/Sub)**, onde uma mensagem enviada para um **tópico** pode ser distribuída para vários assinantes ao mesmo tempo.

📌 **Cenário:**  
- Um sistema de monitoramento detecta um problema no banco de dados.  
- Ele publica uma mensagem no **Amazon SNS**.  
- O SNS envia essa mensagem para **vários assinantes**:  
  🔹 **Email** do administrador.  
  🔹 **SMS** para um celular de alerta.  
  🔹 **Lambda Function** para acionar um processo automático.  

### 🏗 **Fluxo de Funcionamento do SNS**
1️⃣ **Publicador** → Envia uma mensagem para o **tópico SNS**.  
2️⃣ **SNS** → Distribui a mensagem para todos os **assinantes** do tópico.  

### 🔧 **Exemplo prático de SNS**
Criando um **tópico SNS**:
```sh
aws sns create-topic --name alerta-sistema
```

Criando uma **assinatura (ex: email)**:
```sh
aws sns subscribe --topic-arn arn:aws:sns:us-east-1:1234567890:alerta-sistema \
--protocol email --notification-endpoint meuemail@exemplo.com
```

Publicando uma mensagem para o tópico:
```sh
aws sns publish --topic-arn arn:aws:sns:us-east-1:1234567890:alerta-sistema \
--message "Alerta! O banco de dados está sobrecarregado!"
```

📌 **Os assinantes do tópico (emails, SMS, Lambda, SQS) receberão a mensagem automaticamente!** 🚀  

---

## **📌 3. Quando Usar SQS vs SNS?**
| Característica | Amazon SQS (Fila) | Amazon SNS (Pub/Sub) |
|--------------|-----------------|------------------|
| **Padrão** | Point-to-Point | Broadcast |
| **Entrega** | Uma mensagem para um único consumidor | Uma mensagem para vários consumidores |
| **Uso Ideal** | Processamento assíncrono, desacoplamento de serviços | Notificações, eventos, integração com múltiplos sistemas |

💡 **Exemplo de Uso Combinado**  
Podemos combinar **SNS + SQS** para distribuir mensagens de um **único publicador** para **múltiplas filas de processamento**!

1️⃣ **O SNS publica um evento de novo pedido.**  
2️⃣ **Duas filas SQS recebem a mensagem:**  
   🔹 Fila A → Processa pagamento.  
   🔹 Fila B → Atualiza o estoque.  

📌 **Esse design melhora escalabilidade e desacoplamento!** 🚀  

---

## **🎯 Resumo**
✔ **Amazon SQS** → Sistema de **fila de mensagens**, point-to-point, usado para processamentos assíncronos.  
✔ **Amazon SNS** → Sistema **Pub/Sub**, onde uma mensagem é enviada para múltiplos assinantes ao mesmo tempo.  
✔ **SQS + SNS** → Juntos, criam arquiteturas escaláveis e resilientes!  

---

## **📌 Tecnologias e Padrões Sem Servidor (Serverless) na AWS**  

A **arquitetura serverless (sem servidor)** permite executar código **sem gerenciar servidores**. A AWS cuida automaticamente do provisionamento, escalabilidade e manutenção da infraestrutura.  

Os principais serviços **serverless** na AWS são:  
✔ **AWS Lambda** → Executa código sem necessidade de servidores.  
✔ **AWS Fargate** → Permite rodar containers sem gerenciar servidores.  

---

## **1️⃣ AWS Lambda – Funções Serverless**  

📌 **O que é?**  
O **AWS Lambda** permite rodar **funções** em resposta a eventos sem precisar gerenciar servidores.  

📌 **Casos de Uso:**  
✅ Processamento de eventos de **S3, DynamoDB, API Gateway, CloudWatch**  
✅ Automação de tarefas **(ex: backup, notificações, análise de logs)**  
✅ Integração com outros serviços **AWS (ex: AWS Step Functions)**  

### 🏗 **Como Funciona o AWS Lambda?**  
1️⃣ **Trigger (Evento)** → Exemplo: Upload de um arquivo no **S3**.  
2️⃣ **Execução da Função Lambda** → Exemplo: Processamento do arquivo.  
3️⃣ **Saída** → Exemplo: Salvar dados processados no **DynamoDB**.  

### 🔧 **Exemplo prático com AWS Lambda**
Criando uma **função Lambda** na AWS CLI:
```sh
aws lambda create-function --function-name ProcessarPedido \
--runtime python3.8 --role arn:aws:iam::1234567890:role/meu-role \
--handler lambda_function.lambda_handler \
--zip-file fileb://meuarquivo.zip
```
Invocando a função manualmente:
```sh
aws lambda invoke --function-name ProcessarPedido output.json
```

💡 **Vantagens do AWS Lambda**  
✅ **Escala automática** → AWS escala de acordo com a demanda.  
✅ **Modelo de pagamento por uso** → Cobra apenas pelo tempo de execução.  
✅ **Sem necessidade de gerenciar servidores.**  

---

## **2️⃣ AWS Fargate – Containers Sem Servidor**  

📌 **O que é?**  
O **AWS Fargate** permite rodar **containers Docker** sem precisar gerenciar instâncias EC2.  

📌 **Casos de Uso:**  
✅ Execução de **containers em ECS ou EKS** sem provisionar infraestrutura.  
✅ Aplicações **event-driven**, como **processamento de jobs**.  
✅ Workloads de **curta duração**, como análise de dados e CI/CD.  

### 🏗 **Como Funciona o AWS Fargate?**  
1️⃣ **Cria-se uma Task Definition no ECS/EKS**  
2️⃣ **O Fargate gerencia a execução do container**  
3️⃣ **O container escala automaticamente conforme a demanda**  

### 🔧 **Exemplo prático com AWS Fargate**
Criando um cluster ECS para rodar containers no Fargate:
```sh
aws ecs create-cluster --cluster-name meu-cluster
```
Criando uma definição de tarefa para um container:
```sh
aws ecs register-task-definition \
    --family minha-tarefa \
    --network-mode awsvpc \
    --requires-compatibilities FARGATE \
    --cpu "256" --memory "512" \
    --container-definitions '[{"name":"meu-container","image":"nginx","essential":true}]'
```
Rodando um container no Fargate:
```sh
aws ecs run-task --cluster meu-cluster --task-definition minha-tarefa
```

💡 **Vantagens do AWS Fargate**  
✅ **Gerencia a infraestrutura automaticamente**  
✅ **Escala sob demanda**  
✅ **Sem necessidade de gerenciar instâncias EC2**  

---

## **📊 AWS Lambda vs AWS Fargate – Quando Usar Cada Um?**
| Característica | AWS Lambda | AWS Fargate |
|--------------|------------|------------|
| **Execução** | Código serverless (funções) | Containers sem servidor |
| **Duração da Execução** | Máximo de 15 minutos | Execução contínua |
| **Casos de Uso** | Eventos, ETL, APIs, automação | Microsserviços, aplicações containerizadas |
| **Provisionamento** | Zero servidores, escalabilidade automática | Containers gerenciados |

📌 **Lambda é melhor para código simples e event-driven, enquanto Fargate é ideal para workloads mais complexos e stateful.**  

---

## **🎯 Resumo**
✔ **AWS Lambda** → Executa código sem servidores, ideal para eventos e funções rápidas.  
✔ **AWS Fargate** → Roda containers sem EC2, ideal para microsserviços e workloads maiores.  
✔ **Ambos são serverless**, eliminando a necessidade de gerenciar infraestrutura!  

---
