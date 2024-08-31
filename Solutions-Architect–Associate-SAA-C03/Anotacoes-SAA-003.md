
# Anotações 

## IAM 

Aqui vc pode criar usuarios, grupos e polices. 

### User

Você pode adicionar permissões ao user diretamenta, ou com base no grupo. 

### User groups

Os grupos de usuarios tem polices atreladas a ele, e ao adicionar um usuario a ao grupo o mesmo herda estas polices. 

### Polices 

São as permissões em si. 

### Password Police

- A idea aqui é criar senhas complexas com politicas de trocas 

### Multi Factor Authentication - MFA. 

A MFA aumenta a segurança porque, além das credenciais de login usuais, exige que os usuários forneçam autenticação exclusiva em um mecanismo de MFA compatível com a AWS ao acessar sites ou serviços da AWS. A AWS é compatível com os seguintes tipos de MFA: chaves de acesso e chaves de segurança, aplicações de autenticador virtual e tokens físicos de TOTP.

### Chaves de acesso e chaves de segurança
A AWS Identity and Access Management é compatível com chaves de acesso e chaves de segurança para MFA. Com base nos padrões FIDO, chaves de acesso usam criptografia de chave pública para proporcionar uma autenticação forte e resistente a phishing que é mais segura do que as senhas. A AWS é compatível com dois tipos de chaves de acesso: chaves de acesso vinculadas a dispositivo (chaves de segurança) e chaves de acesso sincronizadas.

- Chaves de segurança: dispositivos físicos, como a YubiKey, usados como segundo fator de autenticação. Uma única chave de segurança é compatível com várias contas de usuário-raiz e usuários do IAM.

- Chaves de acesso sincronizadas: usam gerenciadores de credenciais de provedores como Google, Apple, contas da Microsoft e serviços de terceiros, como 1Password, Dashlane e Bitwarden, como segundo fator.

Você pode usar autenticadores biométricos integrados, como Touch ID em Apple MacBooks, para desbloquear seu gerenciador de credenciais e fazer login na AWS. As chaves de acesso são criadas com o provedor escolhido usando sua impressão digital, rosto ou PIN do dispositivo. Você pode sincronizar chaves de acesso em seus dispositivos para facilitar o login na AWS e aprimorar a usabilidade e a capacidade de recuperação.

O IAM não oferece suporte ao registro de chave de acesso local para o Windows Hello. Para criar e usar chaves de acesso, os usuários do Windows devem usar a autenticação entre dispositivos, na qual você usa uma chave de acesso de um dispositivo, como um dispositivo móvel, ou uma chave de segurança de hardware, para entrar em outro dispositivo, como um laptop.

A FIDO Alliance conta com uma lista de todos os produtos certificados pela FIDO compatíveis com as especificações da FIDO. Para obter mais informações sobre como habilitar chaves de acesso e chaves de segurança, consulte Habilitar uma chave de acesso ou uma chave de segurança para o Usuário raiz da conta da AWS (console).


## Dicas de Exeme - Tópico EC2 
- Assinalar endereços ipv4 e ipv6 para instancias ec2
- Pode usar elastic ip adress, estatico , vai ser mantido n
- Pode criar as proprias AMIS apartir da instancias ja configuradas com software
- volumes  EBS sao persistentes, os dados não sao apagados
- Qualquer tipo de volume EBS pode usar criptografia de dados
- Vc pode criar snapshotss de volumes e armazenar em buckets s3
- Vc pode usar CloudWatch para monitorar a performance das instancias Ec2.
- Placement groups vai ajudar vc a distribuir as instancias EC2 de acordo com as necessidades.
- 
- 

