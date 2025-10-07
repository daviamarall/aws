## 🧩 O que é uma AMI (Amazon Machine Image)

Uma **AMI** é uma **imagem pré-configurada de máquina virtual** usada para **criar instâncias EC2 (Elastic Compute Cloud)** na AWS.
Ela contém tudo o que o sistema precisa para iniciar e funcionar, incluindo:

1. **Sistema operacional** (Linux, Windows, etc.)
2. **Aplicações e bibliotecas** pré-instaladas
3. **Configurações do sistema**
4. **Permissões de acesso** e **configurações de inicialização**

Em resumo: a AMI é o “modelo” da sua instância EC2.

---

## ⚙️ Componentes de uma AMI

Cada AMI é composta por:

* **Uma ou mais snapshots do EBS** → armazenam o conteúdo do disco.
* **Informações de inicialização** → como o sistema deve ser configurado ao iniciar.
* **Permissões de acesso** → define quem pode usar essa imagem.
* **Block device mapping** → define quais volumes (discos) serão montados na instância.

---

## 🚀 Tipos de AMI

A AWS oferece **três tipos principais** de AMIs:

1. **AMIs públicas**

   * Disponíveis para todos os usuários da AWS.
   * Exemplo: AMIs oficiais da Amazon Linux, Ubuntu, Windows Server.

2. **AMIs privadas**

   * Criadas e visíveis apenas na sua conta.
   * Usadas para padronizar ambientes internos (por exemplo, com suas aplicações já instaladas).

3. **AMIs de Marketplace**

   * Fornecidas por terceiros (empresas/parceiros).
   * Podem incluir softwares pagos (como Red Hat, Fortinet, etc.).

---

## 🧠 Exemplo prático

### 1️⃣ Criar uma instância usando uma AMI padrão

Você pode escolher, por exemplo:

* **Amazon Linux 2 AMI**
* **Ubuntu Server 22.04 LTS**
* **Microsoft Windows Server 2022**

A partir dela, cria uma EC2 já funcional.

---

### 2️⃣ Criar uma AMI personalizada

Imagine que você:

* Instalou o Apache e o PHP em uma instância EC2
* Configurou tudo exatamente como precisa

Você pode **criar uma AMI personalizada** dessa instância.
Assim, no futuro, ao lançar novas EC2s, tudo já virá configurado igual — economizando tempo e garantindo padronização.

---

## 🔁 Atualizações e versionamento

É comum manter **versões de AMIs**, como:

* `ami-webserver-v1`
* `ami-webserver-v2` (com patch de segurança atualizado)

Isso ajuda a manter controle e rastreabilidade sobre o ambiente.

---

## 🔒 Permissões e compartilhamento

Você pode:

* **Compartilhar AMIs** com outras contas da AWS.
* Torná-las **públicas** (visíveis a qualquer um).
* Ou **privadas**, restritas à sua conta.

---

## 💰 Custo

* Criar e armazenar uma AMI **não tem custo direto**.
* O que é cobrado é o **armazenamento do snapshot EBS** associado a ela.
