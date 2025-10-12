## 🧩 O que é o EC2 Instance Store

O **Instance Store** é um **armazenamento em disco físico** que fica **diretamente acoplado ao host físico** onde a instância EC2 está sendo executada.

Em outras palavras:
➡️ é um **disco local (não EBS)**, com **baixa latência e altíssimo desempenho**, mas **volátil** — ou seja, **os dados são perdidos quando a instância é parada, encerrada ou movida para outro host**.

---

## ⚙️ Características principais

| Característica            | Descrição                                                                               |
| ------------------------- | --------------------------------------------------------------------------------------- |
| **Tipo de armazenamento** | Local (diretamente no host físico)                                                      |
| **Desempenho**            | Muito alto — ideal para cache, buffers, dados temporários                               |
| **Persistência**          | Não persistente — os dados são perdidos ao parar ou encerrar a instância                |
| **Custo**                 | Incluso no preço da instância (sem custo adicional por GB como o EBS)                   |
| **Tamanho**               | Varia conforme o tipo de instância (por exemplo, `i3`, `d2`, `m5d` têm volumes grandes) |
| **Latência**              | Extremamente baixa, pois não depende da rede                                            |
| **Backup necessário?**    | Sim, se precisar preservar dados                                                        |

---

## 📦 Exemplo de uso

O Instance Store é indicado quando você **precisa de alto desempenho, mas não de persistência**.
Exemplos práticos:

* Armazenar **arquivos temporários** ou **cache** de aplicação.
* Uso em **bancos de dados NoSQL** de alta performance que replicam dados em rede (como Cassandra).
* **Processamento de dados** (ETL, big data, analytics) onde os dados são lidos, processados e descartados.
* **Armazenamento efêmero** em containers ou clusters (por exemplo, em Kubernetes com pods de curta duração).

---

## 🧠 Comparação com o EBS (Elastic Block Store)

| Aspecto                | **Instance Store**                 | **EBS**                                         |
| ---------------------- | ---------------------------------- | ----------------------------------------------- |
| **Localização**        | Disco físico local                 | Rede (armazenamento em rede da AWS)             |
| **Persistência**       | Não persiste após stop/terminate   | Persiste                                        |
| **Desempenho**         | Muito alto (latência baixa)        | Alto, mas depende do tipo (gp3, io2, etc.)      |
| **Custo**              | Incluso na instância               | Cobrado separadamente por GB e IOPS             |
| **Backup (Snapshots)** | Não suporta                        | Suporta snapshots no S3                         |
| **Usos comuns**        | Cache, temp files, data processing | Bancos de dados, logs, armazenamento permanente |

---

## ⚠️ Cuidados

* **Parou ou encerrou a instância → dados se perdem.**
* **Não é possível redimensionar** o volume Instance Store.
* **Snapshots não são suportados.**
* **Apenas alguns tipos de instância** oferecem volumes Instance Store (por exemplo: `i3`, `i4i`, `m5d`, `c6gd`, etc.).

---

## 💡 Dica prática

Se quiser usar Instance Store **e ainda manter persistência**, uma prática comum é:

> Utilizar o Instance Store como cache + replicar periodicamente dados críticos para o EBS ou S3.
