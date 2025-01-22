# AWS CLI

## 1. Introdução

### O que é AWS CLI?
AWS Command Line Interface (CLI) é uma ferramenta unificada para gerenciar seus serviços AWS diretamente no terminal. Com ela, você pode automatizar tarefas, criar e gerenciar recursos sem precisar usar o console web da AWS.

### Instalação e Configuração
#### Instalação
Siga os passos abaixo para instalar a AWS CLI:

**Windows:**
```bash
choco install awscli
```

**Linux/MacOS:**
```bash
curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
sudo installer -pkg AWSCLIV2.pkg -target /
```

#### Configuração
Depois de instalar, configure suas credenciais AWS:
```bash
aws configure
```
Será solicitado:
1. Access Key ID
2. Secret Access Key
3. Região padrão (exemplo: `us-east-1`)
4. Formato de saída (exemplo: `json` ou `table`)

## 2. Comandos Básicos

### Listando Recursos
Listar todos os buckets S3:
```bash
aws s3 ls
```

Listar instâncias EC2 em execução:
```bash
aws ec2 describe-instances --filters Name=instance-state-name,Values=running
```

### Criando e Deletando Recursos
Criar um bucket S3:
```bash
aws s3 mb s3://meu-bucket-exemplo
```

Deletar um bucket S3:
```bash
aws s3 rb s3://meu-bucket-exemplo --force
```

## 3. Gestão de Serviços AWS

### S3: Gerenciamento de Buckets e Objetos
Enviar um arquivo para o S3:
```bash
aws s3 cp arquivo.txt s3://meu-bucket-exemplo
```

Baixar um arquivo do S3:
```bash
aws s3 cp s3://meu-bucket-exemplo/arquivo.txt .
```

### EC2: Gerenciamento de Instâncias
Iniciar uma instância EC2:
```bash
aws ec2 start-instances --instance-ids i-1234567890abcdef0
```

Parar uma instância EC2:
```bash
aws ec2 stop-instances --instance-ids i-1234567890abcdef0
```

### IAM: Usuários, Grupos e Políticas
Criar um usuário:
```bash
aws iam create-user --user-name novo-usuario
```

Anexar uma política ao usuário:
```bash
aws iam attach-user-policy --user-name novo-usuario --policy-arn arn:aws:iam::aws:policy/AmazonS3FullAccess
```

## 4. Automatização

### Scripts Básicos com AWS CLI
Exemplo de script para listar buckets S3 e salvar em um arquivo:
```bash
#!/bin/bash
aws s3 ls > lista_buckets.txt
echo "Buckets salvos em lista_buckets.txt"
```

### Uso com Arquivos JSON/YAML
Criar um recurso EC2 usando um arquivo JSON:
```bash
aws ec2 run-instances --cli-input-json file://configuracao-ec2.json
```

Exemplo do arquivo `configuracao-ec2.json`:
```json
{
  "ImageId": "ami-0abcdef1234567890",
  "InstanceType": "t2.micro",
  "MinCount": 1,
  "MaxCount": 1
}
```

## 5. Boas Práticas

### Segurança e Credenciais
- Nunca compartilhe suas credenciais AWS.
- Use variáveis de ambiente para credenciais temporárias:
```bash
export AWS_ACCESS_KEY_ID=YOUR_ACCESS_KEY_ID
export AWS_SECRET_ACCESS_KEY=YOUR_SECRET_ACCESS_KEY
```

### Organização de Perfis
Gerencie múltiplos perfis no arquivo `~/.aws/credentials`:
```ini
[default]
aws_access_key_id=DEFAULT_ACCESS_KEY
aws_secret_access_key=DEFAULT_SECRET_KEY

[dev]
aws_access_key_id=DEV_ACCESS_KEY
aws_secret_access_key=DEV_SECRET_KEY
```
Usar um perfil específico:
```bash
aws s3 ls --profile dev
```

## 6. Exercícios Práticos

### Cenário 1: Gerenciamento de S3
1. Crie um bucket chamado `bucket-teste-cli`.
2. Envie um arquivo chamado `teste.txt` para o bucket.
3. Liste os objetos do bucket e baixe o arquivo para o diretório local.

### Cenário 2: Gestão de Instâncias EC2
1. Liste todas as instâncias EC2 em sua conta.
2. Inicie uma instância específica.
3. Pare a mesma instância.

---
### Documentação oficial 

https://docs.aws.amazon.com/pt_br/cli/latest/userguide/cli-chap-welcome.html