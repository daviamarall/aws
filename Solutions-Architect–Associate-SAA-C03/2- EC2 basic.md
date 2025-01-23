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

## Security Groups

### Visão Geral
Os grupos de segurança atuam como um "firewall" para instâncias EC2. Eles regulam:

- Acesso às Portas
- Faixas de IP autorizadas - IPv4 e IPv6
- Controle de rede de entrada (de outros para a instância)
- Controle de rede de saída (da instância para outros)

![alt text](image.png)

### Diagrama 
![alt text](image-1.png)

## Pontos Importantes
- Podem ser anexados a várias instâncias
- Estão vinculados a uma combinação de região/VPC
- Operam "fora" da instância EC2 – se o tráfego for bloqueado, a instância EC2 não o verá
- É recomendável manter um grupo de segurança separado para acesso SSH
- Se sua aplicação não estiver acessível (timeout), o problema está no grupo de segurança
- Se sua aplicação apresentar o erro "connection refused", então é um problema na aplicação ou ela não foi iniciada
- Todo o tráfego de entrada é bloqueado por padrão
- Todo o tráfego de saída é autorizado por padrão

## Referenciando Outros Grupos de Segurança
Os grupos de segurança podem ser configurados para referenciar outros grupos de segurança dentro da mesma VPC. Isso permite criar regras de tráfego que permitem ou negam acesso entre recursos associados a diferentes grupos de segurança.

### Diagrama

A seguir, um exemplo simplificado de como funciona a referência entre grupos de segurança:

![alt text](image-2.png)

## Ports

- 22 = SSH (Secure Shell) - acesso a uma instância Linux
- 21 = FTP (File Transfer Protocol) - upload de arquivos para um compartilhamento de arquivos
- 22 = SFTP (Secure File Transfer Protocol) - upload de arquivos usando SSH
- 80 = HTTP - acesso a sites não seguros
- 443 = HTTPS - acesso a sites seguros
- 3389 = RDP (Remote Desktop Protocol) - acesso a uma instância Windows

## Opções de Compra de Instâncias EC2

- **On-Demand Instances** – cargas de trabalho curtas, preço previsível, pagamento por segundo
- **Reserved (1 e 3 anos)**  
  - **Reserved Instances** – cargas de trabalho longas  
  - **Convertible Reserved Instances** – cargas de trabalho longas com instâncias flexíveis
- **Savings Plans (1 e 3 anos)** – compromisso com uma quantidade de uso, para cargas de trabalho longas
- **Spot Instances** – cargas de trabalho curtas, econômicas, com possibilidade de perda de instâncias (menos confiáveis)
- **Dedicated Hosts** – reserva de um servidor físico inteiro, controle total sobre o posicionamento das instâncias
- **Dedicated Instances** – nenhum outro cliente compartilhará seu hardware
- **Capacity Reservations** – reserva de capacidade em uma Zona de Disponibilidade específica por qualquer duração
