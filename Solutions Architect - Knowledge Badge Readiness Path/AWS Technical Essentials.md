# O que é a AWS?

## On-premises e computação em nuvem

Antes da nuvem, empresas e organizações hospedavam e mantinham hardware, como equipamentos de computação, armazenamento e rede em seus próprios datacenters. Muitas vezes, eles alocavam departamentos de infraestrutura inteiros para cuidar de seus datacenters, o que resultou em operações dispendiosas que impossibilitaram algumas workloads e experimentações.

À medida que o uso da Internet se tornou mais difundido, a demanda por equipamentos de computação, armazenamento e rede aumentou. Para algumas empresas e organizações, o custo de manter uma grande presença física era insustentável. Para resolver esse problema, surgiu a computação em nuvem.

A computação em nuvem é uma entrega sob demanda de recursos de TI pela internet com precificação de pagamento conforme o uso. Com a computação em nuvem, as empresas não precisam gerenciar e manter seu próprio hardware e datacenters. Em vez disso, empresas como a AWS têm e mantêm datacenters e fornecem tecnologias e serviços de datacenter virtual para empresas e usuários pela Internet.

Para ajudar a diferenciar entre workloads em execução on-premises em comparação com a nuvem, considere um cenário no qual seus desenvolvedores devem implantar um novo recurso de aplicação. Antes de implantar, a equipe deseja testar o recurso em um ambiente de garantia de qualidade (QA) separado que tenha as mesmas configurações que o de produção. Em uma solução on-premises, um ambiente adicional exige que você compre e instale hardware, conecte o cabeamento necessário, forneça energia, instale sistemas operacionais e muito mais. Essas tarefas podem ser demoradas e caras. Enquanto isso, o tempo de comercialização do novo recurso aumenta enquanto os desenvolvedores esperam pelo ambiente de controle de qualidade (QA). Em contraste, se você executar sua aplicação na nuvem, poderá replicar todo um ambiente de produção, sempre que necessário, em questão de minutos ou até mesmo segundos. Em vez de instalar fisicamente o hardware e conectar o cabeamento, a solução é gerenciada pela Internet. 

O uso da computação em nuvem economiza tempo durante a configuração e remove o trabalho pesado sem diferenciação. Se você olhar para qualquer aplicação, verá que alguns de seus aspectos são muito importantes para sua empresa, como o código. No entanto, outros aspectos não são diferentes de qualquer outra aplicação que você possa fazer (por exemplo, a computação em que o código é executado.) Ao remover tarefas comuns repetitivas que não diferenciam seus negócios, como instalar máquinas virtuais (VMs) ou armazenar backups, você pode se concentrar naquilo que é estrategicamente exclusivo para sua empresa e permitir que a AWS cuide das tarefas demoradas que não o diferenciam de seus concorrentes. É aí que a AWS entra.

A AWS fornece serviços de computação em nuvem. Os recursos de TI mencionados na definição de computação em nuvem são produtos da AWS. Para a aplicação de diretório corporativo deste curso, você usará os produtos da AWS para arquitetar uma infraestrutura escalável, altamente disponível e econômica para hospedar a aplicação de diretório corporativo. Dessa forma, você pode disponibilizar a aplicação rapidamente, sem gerenciar hardware físico pesado.

## Seis vantagens da computação em nuvem 

* Pagamento conforme uso
  
     Em vez de investir em datacenters e hardware antes de saber como você vai usá-los, você paga somente quando usa recursos de computação e apenas pelo quanto você usa.
  
  ![image](https://github.com/daviamarall/aws/assets/40430859/bcbfe357-f327-4994-8a1d-de16506d71ec)

  
* Beneficiar-se de economia massiva em escala
  
     O uso da computação em nuvem permite obter um custo inferior ao que você obtém em seu ambiente local. Considerando que o uso de centenas de milhares de clientes é agregado na nuvem, a AWS consegue obter economias maiores de escala, o que resulta em preços mais baixos com pagamento
conforme o uso (pay as-you-go).

![image](https://github.com/daviamarall/aws/assets/40430859/7d5f12c2-b048-4197-9b5b-f0795221dd29)
  
* Parar de adivinhar a capacidade
  
  Elimine as suposições ao determinar sua necessidade de capacidade de infraestrutura. Muitas vezes, ao tomar uma decisão sobre a capacidade antes de implantar uma aplicação, você acaba precisando lidar com recursos caros e ociosos ou com capacidade limitada. Com a computação em nuvem, esses problemas são resolvidos. Você pode acessar a quantidade de capacidade que quiser e aumentar e reduzir a escala na vertical, conforme a necessidade em apenas alguns minutos.
  
![image](https://github.com/daviamarall/aws/assets/40430859/d0b0e17d-62af-4bf4-ab1c-f58c27d9047d)

* Aumentar a velocidade e a agilidade

  Os recursos de TI estão a apenas um clique de distância, o que significa que você reduz o tempo para disponibilizar recursos para seus desenvolvedores de semanas para minutos. Isso resulta em um aumento drástico na agilidade da organização, pois o custo e o tempo necessários para experimentar e desenvolver são significativamente mais baixos.
  
![image](https://github.com/daviamarall/aws/assets/40430859/9c4835b5-2c9c-4911-8717-14a06f4b42e6)

* Realizar economia de custos,

  As empresas podem se concentrar em projetos que diferenciam seus negócios em vez de manter datacenters. A computação em nuvem permite que você se concentre em seus clientes, ao invés de no trabalho pesado de estruturar, empilhar e manter a estrutura física. Isso, geralmente, é chamado de trabalho pesado indiferenciado.
  
![image](https://github.com/daviamarall/aws/assets/40430859/1ba7ff67-262b-4ede-86c1-c6cffaffe5ff)
  
* Obtenha alcance global.

  As aplicações podem ser implantadas em várias regiões ao redor do mundo com alguns cliques. Isso significa que você pode oferecer baixa latência e uma melhor experiência aos seus clientes a um custo mínimo.

![image](https://github.com/daviamarall/aws/assets/40430859/4a2f6ef8-9fd6-4b06-af49-a8e345efe039)

  
## Diagrama exemplo de serviços utilizados. 

![image](https://github.com/daviamarall/aws/assets/40430859/da035121-d371-4df2-ba4c-2caf1656e5c0)



# Infraestrutura global da AWS 

## Regiões

 ![image](https://github.com/daviamarall/aws/assets/40430859/737b9571-3e8a-40e0-aa5b-27aeeaba9667)


As regiões são locais geográficos em todo o mundo em que a AWS hospeda seus datacenters. As regiões da AWS têm o nome do local em que elas residem. Por exemplo, nos Estados Unidos, a Região do Norte da Virgínia é chamada de Região do Norte da Virgínia e a Região no Oregon é chamada de Região do Oregon. A AWS tem regiões na Ásia-Pacífico, Canadá, Europa, Oriente Médio e América do Sul, e continuamos a expandir para atender às necessidades de nossos clientes.

Cada região da AWS está associada a um nome geográfico e a um código de região.

Aqui estão exemplos de códigos de região:

* **us-east-1:** a primeira região criada na área leste dos EUA. O nome geográfico desta região é o Norte da Virgínia.
* **ap-northeast-1:** a primeira região criada na região nordeste da Ásia-Pacífico. O nome geográfico desta região é Tóquio.

![image](https://github.com/daviamarall/aws/assets/40430859/d0a87181-e4a7-4c70-a043-2a16a5923fbc)

## Escolha da região 

  Quando você decidir qual região da AWS hospedar suas aplicações e workloads, considere quatro aspectos principais: latência, preço, disponibilidade do serviço e conformidade.

## Zonas de disponibilidade 

![image](https://github.com/daviamarall/aws/assets/40430859/97177606-b1b1-44ec-a49f-e0dee85d7480)

Dentro de todas as regiões há um cluster de zonas de disponibilidade (AZs). Uma AZ consiste em um ou mais datacenters com energia, rede e conectividade redundantes. Esses datacenters operam em instalações discretas em localizações não reveladas. Eles são conectados usando links redundantes de alta velocidade e baixa latência.

As AZs também têm um nome de código. Como eles estão localizados dentro das Regiões, eles podem ser endereçados com o anexo de uma letra ao final do nome de código da Região. Por exemplo:

* **us-east-1a**: uma AZ em us-east-1 (Região Norte da Virgínia)
* **sa-east-1b**: uma AZ em sa-east-1 (Região de São Paulo)
  
Portanto, se você perceber que existe um recurso em us-east-1c, você pode inferir que o recurso está localizado em AZ c da região us-east-1.

## Manter a resiliência

Para manter sua aplicação disponível, você deve manter alta disponibilidade e resiliência. Uma prática recomendada bem-conhecida para a arquitetura de nuvem é usar serviços gerenciados com escopo da região. No mínimo, você deve usar duas AZs. Dessa forma, se uma AZ falhar, sua aplicação terá a infraestrutura em funcionamento em uma segunda AZ para assumir o tráfego.

![image](https://github.com/daviamarall/aws/assets/40430859/db6d0279-1df0-4709-bfb6-dae8e869fab1)

## Recursos
## Recursos

[Site externo: AWS: infraestrutura global](https://aws.amazon.com/about-aws/global-infrastructure/)
[Site externo: AWS: documentação de infraestrutura global da AWS](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/global-infrastructure.html)
[Site externo: AWS: zonas de disponibilidade e regiões da AWS](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)
[Site externo: AWS: endpoints de produto da AWS](https://docs.aws.amazon.com/general/latest/gr/rande.html)
[Site externo: AWS: produtos regionais da AWS](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/)

