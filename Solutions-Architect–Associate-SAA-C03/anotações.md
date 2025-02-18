# **Domínio 1: Criação de arquiteturas seguras**, que representa 30% do exame SAA-C03. Esse domínio abrange os seguintes tópicos principais:

### 1.1 Projetar cargas de trabalho seguras e com alto desempenho
- Implementação de **controle de acesso** com IAM:
  - IAM Users, Groups, Roles e Policies (Least Privilege)
  - IAM Identity Center (SSO)
  - AWS STS (Session Tokens)
- Uso de **segurança em rede**:
  - Security Groups vs NACLs
  - AWS WAF e AWS Shield
  - AWS Network Firewall
- Proteção de dados com **criptografia**:
  - AWS KMS (gerenciamento de chaves)
  - AWS Secrets Manager e Parameter Store (armazenamento seguro de credenciais)
  - Criptografia em repouso (S3, RDS, EBS) e em trânsito (TLS)
- Práticas de segurança para **banco de dados e armazenamento**:
  - Amazon RDS IAM authentication
  - Controle de acesso no S3 (Bucket Policies, Block Public Access)

### 1.2 Aplicar princípios de segurança para arquiteturas baseadas em nuvem
- **Shared Responsibility Model** (Modelo de Responsabilidade Compartilhada)
- **Melhores práticas de segurança para cargas de trabalho**:
  - AWS Well-Architected Framework – Pilar de Segurança
  - Princípio do **Least Privilege** (Menor Privilégio)
  - Uso de **MFA (Multi-Factor Authentication)**
- **Gerenciamento de logs e auditoria**:
  - AWS CloudTrail (registro de atividades da conta)
  - AWS Config (compliance e mudanças na configuração)
  - Amazon CloudWatch Logs e AWS Security Hub (monitoramento e alertas)

### 1.3 Garantir proteção contra falhas e ataques cibernéticos
- Implementação de **alta disponibilidade e resiliência**:
  - Multi-AZ e Read Replicas no RDS
  - Backup e recuperação com AWS Backup
  - Disaster Recovery: Pilot Light, Warm Standby, Multi-site
- **Mitigação de DDoS e ameaças**:
  - AWS Shield Standard e Advanced
  - CloudFront para proteção contra ataques na camada de aplicação
  - AWS WAF para bloquear tráfego malicioso


Beleza! Vamos começar com **IAM (Identity and Access Management)**, que é um dos serviços mais críticos para controle de acesso na AWS.  

---

## 🔹 **IAM: Identity and Access Management**
O **AWS IAM (Identity and Access Management)** permite gerenciar quem pode acessar os recursos da AWS e o que essas entidades podem fazer. Ele é baseado nos princípios de **Least Privilege (Menor Privilégio)** e **controle granular de permissões**.

### 📌 **1. IAM Users, Groups, Roles e Policies**  

### 🔹 **IAM Users (Usuários)**
- São **identidades individuais** dentro da AWS.
- Associados a credenciais como:
  - Nome de usuário e senha (para acessar o console AWS)
  - Chaves de acesso (para uso na AWS CLI, SDKs)
- Seguem o **princípio do menor privilégio** (Least Privilege).
- Podem receber permissões diretamente ou através de **Grupos**.

### 🔹 **IAM Groups (Grupos)**
- **Conjunto de usuários** que compartilham permissões comuns.
- Exemplo:
  - Grupo `Administrators`: usuários com permissões administrativas.
  - Grupo `Developers`: usuários com acesso a serviços como Lambda e S3.
- Em vez de atribuir permissões individualmente, você atribui ao grupo e todos os usuários herdam essas permissões.

### 🔹 **IAM Roles (Funções)**
- **Identidades que não pertencem a um usuário específico**.
- Permitem que **serviços da AWS, aplicações ou usuários externos** assumam permissões temporárias.
- **Exemplos:**
  - Uma aplicação em **EC2** pode assumir um **Role** para acessar um **S3 Bucket** sem armazenar credenciais.
  - Usuários federados podem assumir um **Role** via SSO.

### 🔹 **IAM Policies (Políticas)**
- São **documentos JSON** que definem permissões.
- Podem ser anexadas a **Users, Groups e Roles**.
- Dois tipos principais:
  - **Managed Policies (Gerenciadas)** → Criadas pela AWS ou pelo usuário.
  - **Inline Policies (Embutidas)** → Definidas diretamente dentro de um usuário, grupo ou role.
- Exemplo de **Policy JSON** que permite acesso somente leitura ao S3:
  ```json
  {
    "Version": "2012-10-17",
    "Statement": [
      {
        "Effect": "Allow",
        "Action": "s3:ListBucket",
        "Resource": "arn:aws:s3:::meu-bucket"
      }
    ]
  }
  ```

---

## 🔹 **IAM Identity Center (SSO)**
- Gerencia **Single Sign-On (SSO)** para **várias contas AWS** e aplicações SaaS.
- Permite usar **Microsoft Active Directory**, **Okta**, **Google Workspace**, etc., para autenticação.
- Benefícios:
  - **Login único** para múltiplas contas AWS.
  - **Atribuição de permissões centralizada**.
  - **Integração com MFA** para mais segurança.

---

## 🔹 **AWS STS (Security Token Service)**
- Fornece **credenciais temporárias** para acessar a AWS.
- Essas credenciais:
  - Expiram automaticamente (por padrão, em 1 hora).
  - Não precisam ser armazenadas permanentemente.
- Usado para:
  - **Cross-account access** (acesso entre contas AWS).
  - **Usuários federados** (SSO e Active Directory).
  - **Aplicações que precisam de credenciais temporárias**.

### 🔹 **Exemplo de Uso do STS**
1. Um usuário assume um **IAM Role**.
2. O STS gera **credenciais temporárias**.
3. A aplicação usa essas credenciais para acessar um recurso AWS.

Exemplo de chamada à AWS CLI para assumir um role via STS:
```sh
aws sts assume-role --role-arn "arn:aws:iam::123456789012:role/MeuRole" --role-session-name "MinhaSessao"
```

---

## 🔥 **Resumo**
| Componente | Descrição |
|------------|------------|
| **IAM Users** | Usuários individuais com permissões específicas. |
| **IAM Groups** | Conjunto de usuários que compartilham permissões. |
| **IAM Roles** | Identidades que permitem assumir permissões temporárias. |
| **IAM Policies** | Definem permissões em JSON. |
| **IAM Identity Center (SSO)** | Gerencia login único para várias contas. |
| **AWS STS** | Gera credenciais temporárias para acessos seguros. |

---

Com certeza! Vamos criar exemplos práticos para cada parte do primeiro conteúdo sobre **IAM Users, Groups, Roles, Policies, IAM Identity Center e AWS STS**.

---

# ✅ **1. Configuração de IAM Users, Groups, Roles e Policies**

### **1️⃣ Criando um usuário IAM via AWS CLI**
```sh
aws iam create-user --user-name DevUser
```
Isso cria um usuário chamado **DevUser**.

### **2️⃣ Criando um grupo e adicionando permissões**
```sh
aws iam create-group --group-name Developers
```
Agora, adicionamos uma política gerenciada de **acesso ao S3** ao grupo:
```sh
aws iam attach-group-policy --group-name Developers --policy-arn arn:aws:iam::aws:policy/AmazonS3FullAccess
```

Adicionamos o usuário ao grupo:
```sh
aws iam add-user-to-group --user-name DevUser --group-name Developers
```
✅ **Agora o usuário DevUser tem acesso ao S3 porque pertence ao grupo Developers!**

---

# ✅ **2. Criando uma Role para EC2 acessar o S3**
Vamos criar uma **IAM Role** que permite uma instância **EC2 acessar um bucket S3**.

### **1️⃣ Criando uma política JSON personalizada**
Criamos um arquivo chamado `s3-access-policy.json`:
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "s3:*",
            "Resource": "arn:aws:s3:::meu-bucket/*"
        }
    ]
}
```
Agora criamos a política na AWS:
```sh
aws iam create-policy --policy-name S3AccessPolicy --policy-document file://s3-access-policy.json
```
Isso retorna um ARN parecido com:
```
"Arn": "arn:aws:iam::123456789012:policy/S3AccessPolicy"
```

### **2️⃣ Criando a Role para EC2**
Criamos uma Role chamada `EC2S3AccessRole`:
```sh
aws iam create-role --role-name EC2S3AccessRole --assume-role-policy-document file://trust-policy.json
```
O arquivo `trust-policy.json` define que **somente instâncias EC2 podem assumir a Role**:
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": {
                "Service": "ec2.amazonaws.com"
            },
            "Action": "sts:AssumeRole"
        }
    ]
}
```

Agora anexamos a política de acesso ao S3 à Role:
```sh
aws iam attach-role-policy --role-name EC2S3AccessRole --policy-arn arn:aws:iam::123456789012:policy/S3AccessPolicy
```

### **3️⃣ Associando a Role a uma instância EC2**
```sh
aws ec2 associate-iam-instance-profile --instance-id i-1234567890abcdef0 --iam-instance-profile Name=EC2S3AccessRole
```
✅ Agora, qualquer aplicação rodando na EC2 pode acessar o bucket S3 sem precisar de credenciais fixas!

---

# ✅ **3. AWS STS (Security Token Service)**
O **STS** permite assumir um Role temporariamente sem armazenar credenciais permanentes.

### **1️⃣ Criando um Role para acesso temporário**
Criamos uma política para o Role:
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "s3:ListBucket",
            "Resource": "arn:aws:s3:::meu-bucket"
        }
    ]
}
```
Criamos a Role com:
```sh
aws iam create-role --role-name TemporaryS3AccessRole --assume-role-policy-document file://trust-policy.json
```
Anexamos a política ao Role:
```sh
aws iam attach-role-policy --role-name TemporaryS3AccessRole --policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

### **2️⃣ Assumindo a Role com STS**
```sh
aws sts assume-role --role-arn "arn:aws:iam::123456789012:role/TemporaryS3AccessRole" --role-session-name "TemporarySession"
```
Isso retorna credenciais temporárias:
```json
{
    "Credentials": {
        "AccessKeyId": "ASIA...",
        "SecretAccessKey": "abcd...",
        "SessionToken": "FQoGZXIvYXdz...",
        "Expiration": "2025-02-18T12:00:00Z"
    }
}
```
Agora podemos configurar essas credenciais temporárias no ambiente para acessar o S3.

---

# 🚀 **Conclusão**
✅ Criamos um **usuário IAM e grupo** com acesso ao S3.  
✅ Criamos uma **Role** para EC2 acessar o S3 sem credenciais fixas.  
✅ Utilizamos **AWS STS** para acessar um recurso de forma temporária.

Ótimo! Agora vamos falar sobre **segurança de rede na AWS**, abordando **Security Groups, NACLs, AWS WAF, AWS Shield e AWS Network Firewall**.  

---

# 🔹 **2. Uso de Segurança em Rede na AWS**

A AWS fornece várias camadas de segurança para proteger sua infraestrutura de rede. Vamos entender os principais serviços e quando usar cada um.

---

## ✅ **1. Security Groups vs NACLs**  

### 🔹 **Security Groups (SG)**
- **Funcionam a nível de instância** (por exemplo, EC2, RDS, Lambda com VPC).
- **São stateful** (respostas a tráfegos permitidos são automaticamente permitidas).
- **Regras só permitem tráfego** (não bloqueiam, apenas liberam portas e IPs específicos).
- **Atribuídos a instâncias individuais**.
- **Avaliados em conjunto** → Se uma regra permitir, o tráfego é aceito.

📌 **Exemplo: Criando um Security Group para EC2**
```sh
aws ec2 create-security-group --group-name MeuSG --description "Security Group para Web Server"
```
Adicionando regras para permitir tráfego HTTP e SSH:
```sh
aws ec2 authorize-security-group-ingress --group-name MeuSG --protocol tcp --port 80 --cidr 0.0.0.0/0
aws ec2 authorize-security-group-ingress --group-name MeuSG --protocol tcp --port 22 --cidr 192.168.1.0/24
```
✅ Permite HTTP de qualquer IP e SSH apenas da rede interna.

---

### 🔹 **Network ACLs (NACLs)**
- **Funcionam a nível de Subnet (VPC)**.
- **São stateless** (requisições e respostas precisam de regras separadas).
- **Podem permitir ou bloquear tráfego**.
- **São aplicadas em ordem numérica (rule number)**.
- **Avaliação sequencial** → Assim que uma regra bate, ele para de verificar as outras.

📌 **Exemplo: Criando uma NACL para uma Subnet**
```sh
aws ec2 create-network-acl --vpc-id vpc-12345678
```
Adicionando regras para permitir HTTP e SSH:
```sh
aws ec2 create-network-acl-entry --network-acl-id acl-12345678 --rule-number 100 --protocol tcp --port-range From=80,To=80 --egress --cidr-block 0.0.0.0/0 --rule-action allow
aws ec2 create-network-acl-entry --network-acl-id acl-12345678 --rule-number 110 --protocol tcp --port-range From=22,To=22 --egress --cidr-block 192.168.1.0/24 --rule-action allow
```
✅ Permite HTTP globalmente e SSH apenas da rede interna.

📌 **Resumo: Security Group vs NACLs**
| Característica | Security Group | NACL |
|--------------|---------------|------|
| **Nível** | Instância (EC2, RDS) | Subnet (VPC) |
| **Stateful?** | Sim | Não |
| **Permite/Bloqueia?** | Apenas permite | Permite e bloqueia |
| **Ordem de Avaliação** | Avalia todas as regras | Avalia em sequência (numérica) |

---

## ✅ **2. AWS WAF e AWS Shield**
### 🔹 **AWS WAF (Web Application Firewall)**
- **Protege aplicações web** contra **ataques comuns** (SQL Injection, XSS, DDoS na camada de aplicação).
- Usado com **ALB (Application Load Balancer), API Gateway, CloudFront e App Runner**.
- Define **WebACLs** com regras personalizadas.

📌 **Exemplo: Criando uma WebACL para bloquear SQL Injection**
```sh
aws wafv2 create-web-acl --name "MinhaWebACL" --scope "REGIONAL" --default-action Allow --rules '[
    {
        "Name": "BlockSQLInjection",
        "Priority": 1,
        "Statement": {
            "SqliMatchStatement": {
                "FieldToMatch": {
                    "AllQueryArguments": {}
                },
                "TextTransformations": [
                    {
                        "Priority": 0,
                        "Type": "URL_DECODE"
                    }
                ]
            }
        },
        "Action": {
            "Block": {}
        }
    }
]'
```
✅ Isso bloqueia **SQL Injection** na requisição.

---

### 🔹 **AWS Shield**
- Proteção contra **ataques DDoS**.
- Dois níveis:
  - **AWS Shield Standard** (grátis) → Proteção automática contra ataques comuns.
  - **AWS Shield Advanced** (pago) → Monitoramento 24/7, mitigação avançada e suporte AWS.

✅ **AWS Shield Standard** já protege **CloudFront, Route 53 e ALB** sem custo extra!

📌 **Resumo: AWS WAF vs AWS Shield**
| Serviço | Protege contra | Aplicado em |
|---------|--------------|-------------|
| **AWS WAF** | SQL Injection, XSS, Bots, etc. | ALB, API Gateway, CloudFront |
| **AWS Shield** | DDoS | CloudFront, ALB, Route 53 |

---

## ✅ **3. AWS Network Firewall**
- Firewall **gerenciado** dentro da **VPC**.
- Regras mais avançadas que NACLs e Security Groups.
- Baseado no **Suricata** (poderoso sistema de detecção de intrusão).
- Protege **tráfego Leste-Oeste (entre VPCs) e Norte-Sul (de/para internet)**.

📌 **Exemplo: Criando um AWS Network Firewall**
1️⃣ Criamos um firewall policy com regras personalizadas:
```sh
aws network-firewall create-firewall-policy --firewall-policy-name MeuFirewallPolicy --firewall-policy '{
    "StatelessRuleGroupReferences": [],
    "StatefulRuleGroupReferences": [],
    "StatefulDefaultActions": ["aws:drop_strict"]
}'
```
2️⃣ Criamos um firewall e associamos à VPC:
```sh
aws network-firewall create-firewall --firewall-name MeuFirewall --firewall-policy-arn arn:aws:network-firewall:us-east-1:123456789012:firewall-policy/MeuFirewallPolicy --vpc-id vpc-12345678
```
✅ O **AWS Network Firewall** protege redes corporativas e tráfego entre serviços!

---

# 🚀 **Resumo Geral**
| Serviço | Finalidade |
|---------|------------|
| **Security Groups** | Controle de tráfego a nível de instância (EC2, RDS). Stateful. |
| **NACLs** | Controle de tráfego a nível de subnet (VPC). Stateless. |
| **AWS WAF** | Protege contra ataques na camada de aplicação (SQL Injection, XSS, Bots). |
| **AWS Shield** | Protege contra DDoS (Shield Standard é gratuito, Advanced é pago). |
| **AWS Network Firewall** | Firewall gerenciado para tráfego interno da VPC. |

---

Isso cobre toda a parte de **segurança de rede** na AWS! 🔥  


Agora vamos falar sobre **Proteção de Dados com Criptografia** na AWS! 🔐💡  

---

# 🔹 **3. Proteção de Dados com Criptografia**  

A criptografia é essencial para garantir a segurança dos dados em repouso e em trânsito na AWS. Vamos cobrir os principais serviços e técnicas:

- **AWS KMS**: Gerenciamento de chaves de criptografia.  
- **AWS Secrets Manager & Parameter Store**: Armazenamento seguro de credenciais e segredos.  
- **Criptografia em repouso e em trânsito**: Proteção de dados armazenados e transmitidos.  

---

## ✅ **1. AWS KMS (Gerenciamento de Chaves de Criptografia)**  

O **AWS Key Management Service (KMS)** permite criar e gerenciar **chaves de criptografia** para proteger dados em diversos serviços da AWS.

📌 **Principais Características do KMS**:
- Gera e gerencia **Customer Managed Keys (CMK)**.
- Integração com **S3, EBS, RDS, Lambda, DynamoDB e outros serviços**.
- Usa **Hardware Security Modules (HSMs)** para segurança.
- **Auditoria via AWS CloudTrail**.

📌 **Exemplo: Criando uma chave KMS**
```sh
aws kms create-key --description "Minha Chave KMS"
```
📌 **Criptografando e descriptografando um dado**:
```sh
echo "Meu dado secreto" | aws kms encrypt --key-id "alias/minha-chave" --plaintext fileb://- --output text --query CiphertextBlob > data_encrypted.txt

aws kms decrypt --ciphertext-blob fileb://data_encrypted.txt --output text --query Plaintext | base64 --decode
```
✅ Isso protege dados sensíveis usando uma **chave gerenciada pelo usuário (CMK)**.

---

## ✅ **2. AWS Secrets Manager e Parameter Store**  

A AWS oferece **dois serviços** para armazenar **credenciais e segredos** com segurança:

### 🔹 **AWS Secrets Manager**
- Armazena e gerencia **credenciais de banco de dados, API Keys, tokens, etc.**
- **Rotação automática de credenciais** (exemplo: trocas periódicas de senhas do RDS).
- Integrado ao **AWS KMS** para criptografia.

📌 **Exemplo: Criando um segredo no Secrets Manager**
```sh
aws secretsmanager create-secret --name MeuBancoSenha --secret-string '{"username":"admin","password":"supersecreto"}'
```
📌 **Recuperando um segredo**
```sh
aws secretsmanager get-secret-value --secret-id MeuBancoSenha --query SecretString --output text
```
✅ Isso protege credenciais sensíveis sem precisar armazená-las em código.

---

### 🔹 **AWS Systems Manager Parameter Store**
- Armazena **valores simples ou hierárquicos** (exemplo: `/prod/db/password`).
- Opção de criptografia com **AWS KMS**.
- **Gratuito para parâmetros padrão** (até 4 KB), enquanto **parâmetros avançados** têm custo.

📌 **Exemplo: Criando um parâmetro no Parameter Store**
```sh
aws ssm put-parameter --name "/prod/db/password" --value "supersecreto" --type SecureString --key-id "alias/minha-chave"
```
📌 **Recuperando um parâmetro seguro**
```sh
aws ssm get-parameter --name "/prod/db/password" --with-decryption
```
✅ **Diferença entre Secrets Manager e Parameter Store**:

| Característica | Secrets Manager | Parameter Store |
|---------------|----------------|----------------|
| **Usado para** | Credenciais de banco, API Keys, tokens | Configurações, senhas simples |
| **Rotação automática** | Sim | Não |
| **Integração com KMS** | Sim | Sim |
| **Custo** | Pago | Gratuito para parâmetros simples |

---

## ✅ **3. Criptografia em Repouso e em Trânsito**  

A AWS protege dados **armazenados (em repouso)** e **enviados entre serviços (em trânsito)**.

---

### 🔹 **Criptografia em repouso (S3, RDS, EBS)**
📌 **Amazon S3**
- **Criptografia no lado do servidor (SSE)**:
  - **SSE-S3** → AWS gerencia as chaves.
  - **SSE-KMS** → Usa chaves gerenciadas no AWS KMS.
  - **SSE-C** → Você fornece suas próprias chaves.
- **Criptografia no lado do cliente** → Aplicação criptografa antes de enviar.

📌 **Exemplo: Ativando criptografia ao enviar um arquivo para S3**
```sh
aws s3 cp meu-arquivo.txt s3://meu-bucket/ --sse aws:kms --sse-kms-key-id alias/minha-chave
```

📌 **Amazon RDS**
- Ativa-se no **momento da criação do banco**.
- Suporta criptografia para **Aurora, MySQL, PostgreSQL, SQL Server, MariaDB e Oracle**.

📌 **Exemplo: Criando um RDS criptografado**
```sh
aws rds create-db-instance --db-instance-identifier meu-db --engine mysql --master-username admin --master-user-password senha123 --storage-encrypted
```

📌 **Amazon EBS**
- **Volumes criptografados** protegem **EC2 e Snapshots**.
- **KMS gerencia as chaves**.

📌 **Exemplo: Criando um volume EBS criptografado**
```sh
aws ec2 create-volume --size 10 --region us-east-1 --availability-zone us-east-1a --encrypted --kms-key-id alias/minha-chave
```

✅ **Resumo: Criptografia em repouso**
| Serviço | Tipo de Criptografia |
|---------|----------------------|
| **S3** | SSE-S3, SSE-KMS, SSE-C, Criptografia do Cliente |
| **RDS** | Criptografia KMS (habilitada na criação) |
| **EBS** | Volumes e Snapshots criptografados com KMS |

---

### 🔹 **Criptografia em trânsito (TLS)**
A AWS **usa TLS/SSL** para proteger a comunicação entre serviços e usuários.

📌 **Como garantir comunicação segura:**
1️⃣ **Habilitar HTTPS no S3**
```sh
aws s3api put-bucket-policy --bucket meu-bucket --policy '{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "EnforceTLS",
            "Effect": "Deny",
            "Principal": "*",
            "Action": "s3:*",
            "Resource": ["arn:aws:s3:::meu-bucket/*"],
            "Condition": {
                "Bool": {
                    "aws:SecureTransport": "false"
                }
            }
        }
    ]
}'
```
✅ **Isso impede acessos não seguros** (sem HTTPS).

2️⃣ **Ativar HTTPS no Load Balancer (ALB)**:
```sh
aws elbv2 create-listener --load-balancer-arn arn:aws:elasticloadbalancing:us-east-1:123456789012:loadbalancer/app/meu-alb --protocol HTTPS --port 443 --certificates CertificateArn=arn:aws:acm:us-east-1:123456789012:certificate/abcd-1234
```
✅ **Isso garante que o tráfego passe por TLS**.

---

# 🚀 **Resumo Final**
| Recurso | Finalidade |
|---------|------------|
| **AWS KMS** | Gerencia chaves para criptografia de dados. |
| **AWS Secrets Manager** | Armazena credenciais e permite rotação automática. |
| **AWS Parameter Store** | Armazena parâmetros e segredos com criptografia. |
| **Criptografia em repouso** | Protege dados armazenados no **S3, RDS, EBS**. |
| **Criptografia em trânsito** | Usa **TLS/SSL** para proteger comunicações. |

---

Isso cobre **criptografia e proteção de dados na AWS**! 🔥  

Bora para mais um tópico essencial para a **SAA-C03**! 🚀  

---

# 🔹 **4. Práticas de Segurança para Banco de Dados e Armazenamento**  

A segurança de **bancos de dados e armazenamento** na AWS envolve **controle de acesso, autenticação e políticas** para proteger os dados.

- **Amazon RDS IAM Authentication** → Gerenciamento de acesso seguro ao banco.  
- **Controle de acesso no S3** → Uso de **Bucket Policies** e **Block Public Access** para restringir permissões.  

---

## ✅ **1. Amazon RDS IAM Authentication**  

O **Amazon RDS IAM Authentication** permite que usuários se conectem ao banco de dados **sem precisar de senhas**, usando **credenciais temporárias gerenciadas pelo IAM**.

📌 **Benefícios do IAM Authentication no RDS**:
- **Elimina a necessidade de armazenar senhas** no código.
- Usa **credenciais temporárias** (STS) para conexões seguras.
- Funciona com **MySQL e PostgreSQL** no RDS e Aurora.

### 🛠 **Passo a Passo: Configurar IAM Authentication no RDS**  

🔹 **1. Criar uma Role IAM para acesso ao RDS**  
```sh
aws iam create-role --role-name RDSIAMRole --assume-role-policy-document '{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Principal": {
      "Service": "rds.amazonaws.com"
    },
    "Action": "sts:AssumeRole"
  }
}'
```
  
🔹 **2. Criar uma Policy para permitir acesso ao banco**  
```sh
aws iam create-policy --policy-name RDSPolicy --policy-document '{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "rds-db:connect",
    "Resource": "arn:aws:rds-db:us-east-1:123456789012:dbuser:my-db/iam_user"
  }
}'
```

🔹 **3. Associar a Policy ao usuário**  
```sh
aws iam attach-user-policy --user-name meu-usuario --policy-arn arn:aws:iam::123456789012:policy/RDSPolicy
```

🔹 **4. Obter Token Temporário de Conexão**  
```sh
aws rds generate-db-auth-token --hostname mydb.cluster-xyz.us-east-1.rds.amazonaws.com --port 3306 --region us-east-1 --username iam_user
```
✅ **Isso gera um token temporário para conexão ao banco!**  

🔹 **5. Conectar ao RDS com IAM Authentication**  
```sh
mysql --host=mydb.cluster-xyz.us-east-1.rds.amazonaws.com --user=iam_user --password=TOKEN_AQUI --ssl-ca=ca.pem
```
✅ **Agora, o usuário acessa o banco sem senha fixa, apenas com o token gerado pelo AWS STS.**  

---

## ✅ **2. Controle de Acesso no S3**  

O **Amazon S3** oferece várias maneiras de **proteger o acesso aos dados**, como **Bucket Policies** e **Block Public Access**.

### 🔹 **Bucket Policies** (Políticas de Acesso no S3)  
As **Bucket Policies** definem quem pode acessar um bucket e quais ações são permitidas.

📌 **Exemplo: Bloquear acesso público ao bucket, exceto para um IP específico**  
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "DenyPublicAccess",
      "Effect": "Deny",
      "Principal": "*",
      "Action": "s3:*",
      "Resource": ["arn:aws:s3:::meu-bucket/*"],
      "Condition": {
        "Bool": {"aws:SecureTransport": "false"}
      }
    },
    {
      "Sid": "AllowSpecificIP",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": ["arn:aws:s3:::meu-bucket/*"],
      "Condition": {
        "IpAddress": {"aws:SourceIp": "192.168.1.100/32"}
      }
    }
  ]
}
```
✅ **Isso impede acessos não seguros e só permite downloads de um IP específico.**  

---

### 🔹 **Block Public Access (BPA) no S3**  
A AWS oferece um controle global para impedir acessos públicos acidentais no S3.

📌 **Habilitar o Block Public Access via CLI**  
```sh
aws s3api put-public-access-block --bucket meu-bucket --public-access-block-configuration '{
  "BlockPublicAcls": true,
  "IgnorePublicAcls": true,
  "BlockPublicPolicy": true,
  "RestrictPublicBuckets": true
}'
```
✅ **Isso garante que o bucket nunca será acessível publicamente!**  

---

# 🚀 **Resumo Final**  

| 🔹 Recurso | ✅ Finalidade |
|------------|-------------|
| **Amazon RDS IAM Authentication** | Conectar ao banco **sem senha fixa**, usando credenciais temporárias. |
| **Bucket Policies** | Controla **quem pode acessar os dados no S3** e o que podem fazer. |
| **Block Public Access (BPA)** | Bloqueia **acesso público não intencional** ao bucket. |

---

🔥 **Isso cobre práticas de segurança para bancos de dados e armazenamento na AWS!**  
