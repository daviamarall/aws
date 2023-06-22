# Configuração inicial da AWS CLI
aws configure

# EC2 - Amazon Elastic Compute Cloud
aws ec2 describe-instances

# S3 - Amazon Simple Storage Service
aws s3 ls
aws s3 cp <arquivo_origem> <destino>
aws s3 sync <diretório_origem> <destino>

# Lambda - AWS Lambda
aws lambda create-function
aws lambda invoke --function-name <nome_função> --payload '<payload>' <arquivo_saida>

# RDS - Amazon Relational Database Service
aws rds describe-db-instances
aws rds create-db-instance

# DynamoDB - Amazon DynamoDB
aws dynamodb create-table
aws dynamodb put-item --table-name <nome_tabela> --item '<item_json>'

# CloudFormation - AWS CloudFormation
aws cloudformation create-stack --stack-name <nome_pilha> --template-body file://<caminho_arquivo_template>
aws cloudformation describe-stacks

# ECS - Amazon Elastic Container Service
aws ecs run-task --cluster <nome_cluster> --task-definition <nome_definição_tarefa>

# EKS - Amazon Elastic Kubernetes Service
aws eks create-cluster --name <nome_cluster>
