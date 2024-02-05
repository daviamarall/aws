# AWS Certified Solutions Architect – Associate (SAA-C03)

## Descrição do curso

* **Domínio 1**: Criação de arquiteturas seguras (30% do conteúdo pontuado)
* **Domínio 2**: Criação de arquiteturas resilientes (26% do conteúdo pontuado)
* **Domínio 3**: Criação de arquiteturas de alto desempenho (24% do conteúdo pontuado)
* **Domínio 4**: Criação de arquiteturas com custo otimizado (20% do conteúdo pontuado)


### IAM: Users e Groups 

- **IAM** = Identity and Access Management, Global service. Identidade e gerenciamento de acesso.
- **Root account** created by default, shouldn't be used or shared. Não deve ser usada ou compartilhada.
- **Users** são pessoas dentro da sua organização e podem ser agrupadas.
- **Groups** contêm apenas usuários, não outros grupos.
- **Users** não precisam pertencer a um grupo, e um usuário pode pertencer a vários grupos.
![image](https://github.com/daviamarall/aws/assets/40430859/1f3f3e48-dc1e-4ac3-a7a6-465e309604c2)

### IAM: Permissions 

- Users or Groups podem ser designados por documentos JSON chamados políticas.
- Estas políticas definem as permissões dos usuários.
- Na AWS, você aplica o princípio do menor privilégio: não conceda mais permissões do que um usuário precisa.
