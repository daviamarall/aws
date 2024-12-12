
# Anotações 

## IAM 

### IAM: Users & Groups (IAM = Gerenciamento de Identidade e Acesso, serviço global)
- A conta root é criada por padrão, não deve ser usada ou compartilhada
- Usuários são pessoas dentro da sua organização e podem ser agrupados
- Grupos contêm apenas usuários, não outros grupos
- Usuários não precisam pertencer a um grupo, e um usuário pode pertencer a vários grupos

![image](https://github.com/user-attachments/assets/9499c449-6f41-42a5-8235-f8635aa1941b)

### IAM: Permissões
- Usuários ou Grupos podem receber documentos JSON chamados policies
- Essas policies definem as permissões dos usuários
- Na AWS, você aplica o princípio do menor privilégio: não dê mais permissões do que um usuário precisa

#### Exemplo: 
![image](https://github.com/user-attachments/assets/df035e36-c638-4b8e-a623-69b6ec9975c8)

### Heranças de Politicas IAM
#### Exemplo:
![image](https://github.com/user-attachments/assets/4b59cc47-8d20-4a09-af03-e07e76ff60b4)

### Estrutura de Políticas IAM
- Consiste em:
  - Versão: versão da linguagem da política, sempre incluir "2012-10-17"
  - Id: um identificador para a política (opcional)
  - Declaração: uma ou mais declarações individuais (obrigatório)

- As declarações consistem em:
  - Sid: um identificador para a declaração (opcional)
  - Efeito: se a declaração permite ou nega acesso (Permitir, Negar)
  - Principal: conta/usuário/papel ao qual esta política se aplica
  - Ação: lista de ações que esta política permite ou nega
  - Recurso: lista de recursos aos quais as ações se aplicam
  - Condição: condições para quando esta política está em vigor (opcional)
#### Exemplo: 
![image](https://github.com/user-attachments/assets/f89a3867-6132-45df-8928-2b4e048c65fb)
























## Dicas de Exeme - Tópico EC2 

- Assinalar endereços ipv4 e ipv6 para instancias ec2
- Pode usar elastic ip adress, estatico , vai ser mantido n
- Pode criar as proprias AMIS apartir da instancias ja configuradas com software
- volumes  EBS sao persistentes, os dados não sao apagados
- Qualquer tipo de volume EBS pode usar criptografia de dados
- Vc pode criar snapshotss de volumes e armazenar em buckets s3
- Vc pode usar CloudWatch para monitorar a performance das instancias Ec2.
- Placement groups vai ajudar vc a distribuir as instancias EC2 de acordo com as necessidades.

## S3 - Simple Storage Services

- Leia atentamente todas as alternativas maiss de uam vez
- Conheça as opções de segurança.
- Controles no nivel de objeto e do bucket
- Classes de armazenamento,
- Casos de uso das classes de armazenamento
- Criptografia S3



![image](https://github.com/user-attachments/assets/c8f2f887-8b3a-4b98-8bde-c7857236760f)
![image](https://github.com/user-attachments/assets/579b80f5-cabe-4eb8-b2c9-c062ee9d37f4)
![image](https://github.com/user-attachments/assets/befa2b8e-93b2-4e37-9fa8-18b50c4a4647)
![image](https://github.com/user-attachments/assets/c9c1939c-d063-4400-9d9f-04e1a37619bc)
![image](https://github.com/user-attachments/assets/416ea1f2-4560-49ba-a8d5-e1644f3bb854)

-  
![image](https://github.com/user-attachments/assets/ec736019-2346-40ce-80ec-238ba28c0238)

![image](https://github.com/user-attachments/assets/e124a1df-864c-4cf0-8462-50e582ff0e0d)
![image](https://github.com/user-attachments/assets/13c8e757-b05b-4f8c-b0f2-f0ccf74fd7f0)


![image](https://github.com/user-attachments/assets/bdae7832-9523-4526-9ef5-787842d23622)



