7
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

### IAM – Política de Senhas
- Senhas fortes = maior segurança para sua conta
- Na AWS, você pode configurar uma política de senhas:
  - Definir um comprimento mínimo para a senha
  - Exigir tipos específicos de caracteres:
    - incluindo letras maiúsculas
    - letras minúsculas
    - números
    - caracteres não alfanuméricos
  - Permitir que todos os usuários IAM mudem suas próprias senhas
  - Exigir que os usuários mudem suas senhas após algum tempo (expiração da senha)
  - Prevenir a reutilização de senhas

### Autenticação Multifator - MFA
- Usuários têm acesso à sua conta e podem possivelmente alterar configurações ou deletar recursos na sua conta AWS
- Você quer proteger suas Contas Root e usuários IAM
- MFA = senha que você conhece + dispositivo de segurança que você possui
  ![image](https://github.com/user-attachments/assets/79fb60c4-59a8-4f2b-a41a-b439837fe879)
- Principal benefício do MFA: se uma senha for roubada ou hackeada, a conta não será comprometida

### Dispositivos de MFA 
![image](https://github.com/user-attachments/assets/1af33412-655a-4737-a5ec-194d4582cb5b)
![image](https://github.com/user-attachments/assets/c91013a1-9191-4798-adcc-4a4fe51daa35)

### Como os usuários podem acessar a AWS?

- Para acessar a AWS, você tem três opções:
  - Console de Gerenciamento da AWS (protegido por senha + MFA)
  - Interface de Linha de Comando da AWS (CLI): protegida por chaves de acesso
  - Kit de Desenvolvimento de Software da AWS (SDK) - para código: protegido por chaves de acesso
- As chaves de acesso são geradas através do Console da AWS
- Os usuários gerenciam suas próprias chaves de acesso
- As chaves de acesso são secretas, assim como uma senha. Não as compartilhe
- ID da Chave de Acesso ~= nome de usuário
- Chave de Acesso Secreta ~= senha

#### Exemplo Acess Keys

- Access key ID: AKIASK4E37PV4983d6C
- Secret Access Key: AZPN3zojWozWCndIjhB0Unh8239a1bzbzO5fqqkZq

### O que é o AWS CLI?

- Uma ferramenta que permite interagir com os serviços da AWS usando comandos no seu terminal de linha de comando
- Acesso direto às APIs públicas dos serviços da AWS
- Você pode desenvolver scripts para gerenciar seus recursos
- É open-source: https://github.com/aws/aws-cli
- Alternativa ao uso do Console de Gerenciamento da AWS
![image](https://github.com/user-attachments/assets/83e19206-e7c3-4f4f-8ce2-7cd5aff2646b)

### O que é o AWS SDK?
- Kit de Desenvolvimento de Software da AWS (AWS SDK)
- APIs específicas para cada linguagem (conjunto de bibliotecas)
- Permite acessar e gerenciar os serviços da AWS programaticamente
- Integrado dentro da sua aplicação
- Suporta:
  - SDKs (JavaScript, Python, PHP, .NET, Ruby, Java, Go, Node.js, C++)
  - SDKs móveis (Android, iOS, ...)
  - SDKs para dispositivos IoT (Embedded C, Arduino, ...)
- Exemplo: o AWS CLI é construído sobre o AWS SDK para Python


### AWS CloudShell
É um serviço da AWS que fornece um ambiente de shell baseado em navegador para gerenciar recursos da AWS diretamente do console. Ele é pré-configurado com as ferramentas mais usadas para administração e automação de recursos na AWS, como o AWS CLI, SDKs, ferramentas de gerenciamento, e utilitários comuns de Unix/Linux.

### Principais características:
1. **Ambiente pronto para uso**: Não é necessário instalar ou configurar ferramentas localmente.
2. **Baseado em navegador**: Acesso fácil pelo console da AWS, sem dependência de um terminal local.
3. **Armazenamento persistente**: Inclui 1 GB de armazenamento persistente por região para scripts, arquivos e dados.
4. **Segurança integrada**: O ambiente usa suas credenciais e permissões IAM para interagir de forma segura com os recursos.
5. **Ferramentas pré-instaladas**: Como Git, Python, Node.js, e muito mais, além do AWS CLI.

### Casos de uso:
- **Automação de tarefas**: Executar comandos no AWS CLI para criar, modificar ou excluir recursos.
- **Desenvolvimento e teste**: Escrever e testar scripts em Python, Bash, etc.
- **Acesso remoto seguro**: Trabalhar com seus recursos de qualquer dispositivo com acesso à internet.

**Vantagem principal**: Reduz o tempo e esforço necessário para configurar e gerenciar um ambiente CLI para interagir com a AWS.

### Funções IAM para Serviços 
• Alguns serviços da AWS precisarão realizar ações em seu nome.  
• Para isso, atribuímos permissões aos serviços da AWS com **IAM Roles** (Funções IAM).  
• Funções comuns:  
   - **Funções para Instâncias EC2**  
   - **Funções para Funções Lambda**  
   - **Funções para o CloudFormation**  
![image](https://github.com/user-attachments/assets/34cf479a-8da7-4be9-b522-0369b9846613)

###  Ferramentas de Segurança IAM 

- **IAM Credentials Report** (nível da conta):  
  - Um relatório que lista todos os usuários da sua conta e o status de suas diversas credenciais.  

- **IAM Access Advisor** (nível do usuário):  
  - O IAM Access Advisor exibe as permissões de serviço concedidas a um usuário e quando esses serviços foram acessados pela última vez.  
  - Você pode usar essas informações para revisar suas políticas.  













