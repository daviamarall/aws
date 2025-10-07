

## 🧩 O que é o EBS?

O **Amazon Elastic Block Store (EBS)** fornece **volumes de armazenamento em bloco** persistentes que podem ser anexados às **instâncias EC2**.
Pense nele como o **HD (ou SSD)** da sua máquina virtual na nuvem.

---

## ⚙️ Como funciona

* Cada volume **EBS é como um disco** independente que pode ser:

  * **Anexado** a uma instância EC2.
  * **Desanexado** e **reatribuído** a outra instância.
* O armazenamento é **persistente**, ou seja, os dados **não são perdidos** se a instância EC2 for parada ou reiniciada.
* É possível **tirar snapshots** (cópias de segurança incrementais) para o **Amazon S3**, facilitando o backup e a recuperação.

---

## 💾 Tipos de Volumes EBS

Existem vários tipos otimizados para diferentes necessidades:

| Tipo de volume     | Descrição                                | Ideal para                                                          |
| ------------------ | ---------------------------------------- | ------------------------------------------------------------------- |
| **gp3/gp2 (SSD)**  | Equilíbrio entre custo e desempenho      | Uso geral, sistemas de arquivos, bancos de dados leves              |
| **io2/io1 (SSD)**  | Alta performance e IOPS garantido        | Bancos de dados críticos e aplicações sensíveis à latência          |
| **st1 (HDD)**      | Desempenho sequencial alto e custo baixo | Grandes volumes de dados acessados sequencialmente (logs, big data) |
| **sc1 (HDD Cold)** | Baixo custo e baixa performance          | Dados raramente acessados (arquivamento)                            |

---

## 🔒 Recursos e Benefícios

* **Persistência de dados:** independente da vida da instância EC2.
* **Snapshots incrementais:** backups eficientes e rápidos.
* **Criptografia nativa:** com integração ao **AWS KMS** (chaves gerenciadas).
* **Alta disponibilidade:** replicação automática dentro da **zona de disponibilidade (AZ)**.
* **Elasticidade:** ajuste de capacidade e desempenho **sem downtime** (em volumes gp3/io2).
* **Desempenho consistente:** adequado até para workloads de banco de dados críticos.

---

## 💰 Cobrança

Você paga por:

* **Capacidade provisionada (GB/mês)**
* **IOPS provisionado (em volumes io1/io2)**
* **Snapshots armazenados no S3**
* **Transferência de dados entre AZs (se houver)**

https://aws.amazon.com/pt/ebs/pricing/

---

## 🧠 Exemplos de uso

* Volume raiz de uma instância EC2 (SO e arquivos).
* Armazenamento para bancos de dados (RDS, MongoDB, Oracle, etc.).
* Ambientes de desenvolvimento e teste.
* Processamento de dados que requer alta taxa de leitura/gravação.

---

## 🚀 Dica prática

Se você precisa:

* **Performance estável e boa relação custo-benefício** → use **gp3**
* **Performance extrema e previsível** → use **io2**
* **Baixo custo para dados grandes e sequenciais** → use **st1**

---

Fontes: 

https://docs.aws.amazon.com/pt_br/ebs/latest/userguide/ebs-ug.pdf

