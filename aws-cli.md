
```markdown
# Comandos CLI da AWS

## AWS CLI Instalação e Configuração

### Instalar a AWS CLI
```bash
# No Linux ou macOS
$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
$ unzip awscliv2.zip
$ sudo ./aws/install

# No Windows (usando o PowerShell)
PS > .\awscliv2.exe

# Verificar a instalação
$ aws --version
```

### Configurar Credenciais
```bash
$ aws configure
```

## Comandos Básicos

### Listar Regiões
```bash
$ aws ec2 describe-regions
```

### Listar Instâncias EC2
```bash
$ aws ec2 describe-instances
```

### Criar um Buckets S3
```bash
$ aws s3 mb s3://meu-bucket-unico
```

### Remover Bucket S3
aws s3 rb s3://seu-bucket --force

### Enviar um Arquivo para um Bucket S3
```bash
$ aws s3 cp meu-arquivo.txt s3://meu-bucket-unico/
```

### Criar uma Instância EC2
```bash
$ aws ec2 run-instances --image-id ami-12345678 --instance-type t2.micro --key-name meu-par-de-chaves
```

### Desligar uma Instância EC2
```bash
$ aws ec2 stop-instances --instance-ids i-1234567890abcdef0
```

### Listar Grupos de Segurança
```bash
$ aws ec2 describe-security-groups
```

### Criar uma Tabela DynamoDB
```bash
$ aws dynamodb create-table --table-name MinhaTabela --attribute-definitions AttributeName=ID,AttributeType=N --key-schema AttributeName=ID,KeyType=HASH --provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5
```

## Exemplos Avançados

### Criar um Cluster Redshift
```bash
$ aws redshift create-cluster --node-type dc2.large --cluster-type single-node --cluster-identifier meu-cluster-redshift --master-username meu-usuario --master-user-password minha-senha
```

### Criar uma Função Lambda
```bash
$ aws lambda create-function --function-name minha-funcao-lambda --runtime nodejs14.x --role arn:aws:iam::123456789012:role/minha-funcao-execucao --handler index.handler --code S3Bucket=meu-bucket, S3Key=minha-funcao.zip
```

### Criar uma Pilha CloudFormation
```bash
$ aws cloudformation create-stack --stack-name minha-pilha --template-body file://template.yaml --parameters ParameterKey=KeyName,ParameterValue=meu-par-de-chaves
```

### Listar Buckets S3 com Formato JSON
```bash
$ aws s3api list-buckets --output json
```

Lembre-se de substituir os valores reais, como nomes de buckets, IDs de instâncias, etc., pelos seus próprios valores ao executar esses comandos na sua própria conta AWS.
```

Este arquivo Markdown único contém todos os exemplos anteriores de comandos CLI da AWS. Você pode copiar e colar este código em um arquivo Markdown (.md) e renderizá-lo em qualquer visualizador de Markdown para uma exibição mais legível. Certifique-se de ter a AWS CLI instalada e configurada em seu ambiente para usar esses comandos.
