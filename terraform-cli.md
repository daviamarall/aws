# Terraform

O Terraform é uma ferramenta de infraestrutura como código (IaC) que permite provisionar, configurar e gerenciar recursos de infraestrutura em vários provedores de nuvem de forma declarativa.

## Comandos do Terraform

Aqui estão alguns comandos básicos do Terraform que ajudam na criação e gerenciamento de recursos:

### `terraform init`

O comando `terraform init` é usado para inicializar um diretório do Terraform. Ele baixa e configura os plugins necessários especificados no arquivo de configuração do Terraform, como provedores e módulos.

Exemplo de uso:
´terraform init´

### `terraform plan`

O comando `terraform plan` é usado para criar um plano de execução do Terraform. Ele analisa os arquivos de configuração do Terraform e mostra as ações que seriam executadas se você aplicasse as alterações.

Exemplo de uso:
´terraform plan´

### `terraform apply`

O comando `terraform apply` é usado para aplicar as alterações definidas nos arquivos de configuração do Terraform. Ele provisiona ou modifica a infraestrutura de acordo com as especificações fornecidas.

Exemplo de uso:
´terraform apply´

### `terraform destroy`

O comando `terraform destroy` é usado para destruir os recursos provisionados pela configuração do Terraform. Ele remove todos os recursos gerenciados pelo Terraform no ambiente de destino.

Exemplo de uso:
´terraform destroy´

### `terraform validate`

O comando `terraform validate` é usado para validar a sintaxe dos arquivos de configuração do Terraform. Ele verifica se os arquivos estão corretamente escritos e se não há erros.

Exemplo de uso:
´terraform validate´

### `terraform state`

O comando `terraform state` é usado para visualizar e gerenciar o estado da infraestrutura gerenciada pelo Terraform. Ele permite visualizar, alterar ou remover recursos individuais do estado.

Exemplo de uso (para listar os recursos no estado):
´terraform state´



Estão listados alguns dos comandos básicos do Terraform. Existem muitos outros comandos e recursos disponíveis para explorar na [documentação oficial do Terraform](https://www.terraform.io/docs/index.html).

