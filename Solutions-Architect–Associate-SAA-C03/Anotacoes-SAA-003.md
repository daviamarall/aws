
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


















