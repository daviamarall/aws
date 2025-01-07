### **Amazon EC2 (Elastic Compute Cloud)**  

- O EC2 é um dos serviços mais populares da Amazon Web Services (AWS).  
- É chamado de **Elastic Compute Cloud** e faz parte do modelo de **Infraestrutura como Serviço (IaaS)**.  
- Basicamente, o EC2 oferece:  
  - **Aluguel de máquinas virtuais** para executar seus aplicativos.  
  - **Armazenamento de dados em discos virtuais** (chamados de EBS).  
  - **Distribuição de carga de trabalho** entre várias máquinas (usando ELB).  
  - **Escalabilidade automática** com grupos que aumentam ou diminuem os recursos conforme a demanda (Auto Scaling Group - ASG).  
- Entender o EC2 é essencial para compreender como a nuvem funciona.

### Dimensionamento e opções de configuração do EC2  

• **Sistema Operacional (SO):** Linux, Windows ou Mac OS  
• **Quantidade de poder computacional e núcleos (CPU)**  
• **Quantidade de memória de acesso aleatório (RAM)**  
• **Quantidade de espaço de armazenamento:**  
  - Conectado à rede (EBS e EFS)  
  - Hardware (EC2 Instance Store)  
• **Placa de rede:** velocidade da placa, endereço IP público  
• **Regras de firewall:** grupo de segurança  
• **Script de inicialização (configuração no primeiro lançamento):** EC2 User Data

### **EC2 User Data**  
• É possível inicializar (bootstrap) nossas instâncias usando um script do **EC2 User Data**.  
• **Bootstrapping** significa executar comandos quando uma máquina é iniciada.  
• Esse script é executado **apenas uma vez**, no primeiro início da instância.  
• O **EC2 User Data** é usado para automatizar tarefas de inicialização, como:  
  - Instalar atualizações  
  - Instalar softwares  
  - Baixar arquivos comuns da internet  
  - Qualquer outra tarefa que você imaginar  
• O script do **EC2 User Data** é executado com o usuário **root**.

### Tipos de instancias. 

O Amazon EC2 oferece uma ampla seleção de tipos de instâncias otimizadas para atender a diferentes casos de uso. Os tipos de instâncias consistem em várias combinações de CPU, memória, armazenamento e capacidade de rede e oferecem flexibilidade de escolha da composição adequada de recursos para os seus aplicativos. Cada tipo de instância inclui um ou mais tamanhos de instância, permitindo a escalabilidade de seus recursos de acordo com os requisitos da workload a ser executada.

https://aws.amazon.com/pt/ec2/instance-types/


### Tipos de Instância EC2 – Uso Geral

-  Excelente para uma diversidade de cargas de trabalho, como servidores web ou repositórios de código.
-  Oferecem equilíbrio entre:

Computação
Memória
Rede


### Tipos de Instância EC2 (EC2 Instance Types) – Otimizadas para Computação (Compute Optimized). .

- Ideais para tarefas intensivas em computação que exigem processadores de alto desempenho:
  - Workloads de processamento em lote
  - Transcodificação de mídia
  - Servidores web de alto desempenho
  - Computação de alto desempenho (HPC)
  - Modelagem científica e aprendizado de máquina
  - Servidores dedicados para jogos

### **Tipos de Instância EC2 (EC2 Instance Types) – Memory Optimized**  
• Desempenho rápido para workloads que processam grandes volumes de dados na memória.  
• Casos de uso:  
  - **Bancos de dados relacionais/não relacionais de alto desempenho**  
  - **Armazenamento em cache distribuído em escala web**  
  - **Bancos de dados em memória otimizados para BI (business intelligence)**  
  - **Aplicações que realizam processamento em tempo real de grandes dados não estruturados**

**Tipos de Instância EC2 (EC2 Instance Types) – Storage Optimized**  
• Ideais para tarefas intensivas em armazenamento que exigem alto desempenho em leituras e gravações sequenciais de grandes volumes de dados no armazenamento local.  
• Casos de uso:  
  - **Sistemas de processamento de transações online (OLTP) de alta frequência**  
  - **Bancos de dados relacionais e NoSQL**  
  - **Cache para bancos de dados em memória (por exemplo, Redis)**  
  - **Aplicações de data warehouse**  
  - **Sistemas de arquivos distribuídos**

### **Introdução aos Grupos de Segurança (Security Groups)**  
• Os Security Groups são a base da segurança de rede na AWS.  
• Eles controlam como o tráfego é permitido para dentro ou fora das nossas instâncias EC2.  
![image](https://github.com/user-attachments/assets/0b1703bc-74d1-4f69-a7e8-5c3c5834d1ee)

• Os Security Groups contêm apenas regras.  
• As regras dos Security Groups podem fazer referência por IP ou por outro Security Group.  

