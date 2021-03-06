---

copyright:
  years: 2019
lastupdated: "2019-07-16"

keywords: pricing model, hourly, per hour, VPC, CPU, vCPU, virtual core, cost, scalability, estimation, optimize your cost, billing

subcollection: blockchain

---

{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:note: .note}
{:important: .important}
{:tip: .tip}
{:gif: data-image-type='gif'}
{:pre: .pre}

# Precificação para o {{site.data.keyword.blockchainfull_notm}} Platform for {{site.data.keyword.cloud_notm}}
{: #ibp-saas-pricing}

Este guia ajuda a entender o modelo de precificação para o {{site.data.keyword.blockchainfull}} Platform for {{site.data.keyword.cloud_notm}} e quanto você pagará ao desenvolver e aumentar sua rede de blockchain de componentes de peers, nós de pedido e autoridades de certificação, que são baseados no Hyperledger Fabric v1.4.1.
{:shortdesc}

_Esse modelo de precificação é somente para o {{site.data.keyword.blockchainfull_notm}} Platform for {{site.data.keyword.cloud_notm}}. Se você estiver usando o plano Starter ou o plano Enterprise e tiver perguntas sobre precificação, consulte a [precificação](/docs/services/blockchain?topic=blockchain-ibp-pricing) do plano Starter e do plano Enterprise._

## Modelo de precificação
{: #ibp-saas-pricing-model}

O {{site.data.keyword.blockchainfull_notm}} Platform apresenta um novo modelo de precificação por hora que é baseado em usos de virtual processor core (VPC). Esse modelo simplificado é baseado na quantia de CPU (ou VPC) que os seus nós do {{site.data.keyword.blockchainfull_notm}} Platform consomem por hora, em uma taxa simples de **$0,29 USD/VPC-hora**.

Um VPC é uma unidade de medida usada para determinar o custo de licenciamento de produtos {{site.data.keyword.IBM_notm}}. Ele é baseado no número de núcleos virtuais (vCPUs) que estão disponíveis para o produto. Um vCPU é um núcleo virtual que é designado a uma máquina virtual ou a um núcleo do processador físico. Para propósitos de estimativa de custo do {{site.data.keyword.blockchainfull_notm}} Platform, **1 VPC = 1 CPU = 1 vCPU = 1 Núcleo**.
{:note}

Para uma estimativa do custo total, lembre-se de que sua rede de blockchain consiste em um cluster {{site.data.keyword.cloud_notm}} Kubernetes que contém os componentes do {{site.data.keyword.blockchainfull_notm}} Platform e usa o armazenamento de sua escolha. Seu cluster {{site.data.keyword.cloud_notm}} Kubernetes e o armazenamento que você escolhe incorrem em encargos separados. Você não será cobrado pelo cluster em que a instância do Operational Tooling, também conhecida como console, está em execução. Consulte o tópico [Referência de arquitetura](/docs/services/blockchain/howto?topic=blockchain-ibp-console-overview#ibp-console-overview-architecture) para obter uma ilustração. Mais detalhes sobre como calcular encargos são descritos abaixo.

### Você é um desenvolvedor?
{: #ibp-saas-pricing-developer}

Os desenvolvedores podem começar com nossa [extensão para VS Code](https://marketplace.visualstudio.com/items?itemName=IBMBlockchain.ibm-blockchain-platform){: external} grátis. Use esse ambiente do desenvolvedor integrado para gravar, testar, depurar e empacotar contratos inteligentes localmente e para a implementação do {{site.data.keyword.blockchainfull_notm}} Platform, bem como para gravar aplicativos clientes. Inicie do zero ou acesse tutoriais e amostras para aprender os fundamentos do blockchain. Em seguida, volte e vincule uma instância de serviço do {{site.data.keyword.blockchainfull_notm}} Platform ao seu cluster do Kubernetes para que seja possível construir sua rede de blockchain usando o console.

## Benefícios do novo modelo de precificação
{: #ibp-saas-pricing-benefits}

- **Nenhuma taxa de associação**: a liberdade de taxas de associação significa que é possível investir diretamente em seus componentes de blockchain.
- **Clareza de estimativa**: um modelo de precificação por hora simples torna a estimativa de custo clara e fácil usando a ferramenta de estimador de custos que está disponível no painel do {{site.data.keyword.cloud_notm}}.
- **Nenhuma taxa mínima necessária**: pague somente o que você usar, nenhum pacote mínimo por hora do VPC é necessário, o que torna muito barato para ser iniciado.
- **Escalabilidade de cálculo**: você tem a opção de escalar seu cálculo para cima durante os períodos de pico de uso ou para baixo até uma fração de minuto de capacidade para quando o cálculo não é necessário para minimizar a despesa.  

Em resumo, esses recursos removem a complexidade da contabilidade para limitações de associação ou cálculo de compra à frente de suas necessidades.

## Elementos chave de custo
{: #ibp-saas-pricing-elements}

Como sua rede de blockchain consiste em um cluster {{site.data.keyword.cloud_notm}} Kubernetes que contém os componentes do {{site.data.keyword.blockchainfull_notm}} Platform e usa o armazenamento de sua escolha, cada um dos elementos a seguir forma seu custo total:

- A taxa fixa do **{{site.data.keyword.blockchainfull_notm}} Platform** de $0,29 USD/VPC-hora. Essa taxa representa o encargo para os componentes de blockchain em seu cluster do Kubernetes.
- Precificação em camadas do cluster **{{site.data.keyword.cloud_notm}} Kubernetes Service** que é visível no {{site.data.keyword.cloud_notm}} quando você provisiona seu cluster pago. Isso inclui os encargos para seu cálculo, isto é, CPU e memória. Os {{site.data.keyword.cloud_notm}} Kubernetes Services são precificados em um modelo em camadas que é baseado no número de horas de uso por mês. Portanto, quando você examinar os planos de precificação, considere que o uso 24x7 é equivalente a 720 horas por mês. Consulte a tabela na [página do Catálogo do Kubernetes Service](https://cloud.ibm.com/kubernetes/catalog/cluster){: external} para obter mais detalhes sobre a precificação do cluster.
- Escolha o plano de **armazenamento** que funciona para suas necessidades. Consulte o tópico [Entendendo o básico do armazenamento do Kubernetes](/docs/containers?topic=containers-kube_concepts#kube_concepts) para saber mais sobre as opções de classe de armazenamento e o quanto elas [custam](https://www.ibm.com/cloud/file-storage/pricing){: external}. Os nós do {{site.data.keyword.blockchainfull_notm}} Platform usam a classe de armazenamento padrão para o cluster. Quando você provisiona um cluster Kubernetes no {{site.data.keyword.cloud_notm}}, ele é pré-configurado com o [Armazenamento de arquivo de nível Bronze](/docs/containers?topic=containers-file_storage#file_predefined_storageclass) como o plug-in de armazenamento persistente.

## Exemplos de precificação
{: #ibp-saas-pricing-scenarios}

A tabela a seguir fornece dois exemplos de precificação com [alocações de recurso padrão]( #ibp-saas-pricing-default), a menos que seja indicado de outra forma.
- O cenário de **Rede de teste** é adequado para iniciar e testar contratos inteligentes.
- O cenário **Associar uma rede de produção** inclui dois peers que são recomendados para alta disponibilidade e uma Autoridade de Certificação (CA) que é necessária para associação de organização.
   - Esses peers podem associar uma rede de produção do {{site.data.keyword.blockchainfull_notm}} Platform que está hospedada em outro lugar.
   - Os nós podem sempre ser discados de volta para um estado de utilização mínima (0,001 CPU) quando eles não estão em uso para [reduzir custos](/docs/services/blockchain?topic=blockchain-ibp-console-govern#ibp-console-govern-reallocate-resources).
   - Como esse cenário é destinado a um ambiente de **produção**:
     - Os recursos de cálculo padrão foram duplicados para fornecer maior capacidade.
     - A classe de armazenamento [Silver](/docs/containers?topic=containers-file_storage#file_silver){: external} é escolhida para desempenho mais rápido.

| Opções de precificação** (1 VPC = 1 CPU)| **Rede de teste** | **Associar uma rede de produção** |
|-|------------|-----------------------------|
| **Alocação de CPU** |  1,65 de CPU <br> Inclui: <br> - 1 peer <br> - 2 CAs <br> -1 nó de pedido| 4,5 CPU <br> Inclui: <br> - 2 peers (para HA) <br> **(Cálculo padrão 2x)** <br>- 1 CA <br>  |
| **Custo por hora: {{site.data.keyword.blockchainfull_notm}} Platform** | US$ 0,48 <br> (1,65 de CPU x US$ 0,29 VPC/hora) | $1,31 USD <br> (4,5 CPU x $0,29 USD/VPC-h) |
| **Custo por hora: cluster {{site.data.keyword.cloud_notm}} Kubernetes**    | US$ 0,12 <br> (Cálculo: camada 2 x 4) <br> (Alocação de IP: US$ 16/mês) | $0,46 USD <br> (Cálculo: camada 8 x 32) <br> (Alocação de IP: US$ 16/mês) |
| **Custo por hora: armazenamento** | $0,07 USD <br> 340 GB  <br> [Bronze](https://www.ibm.com/cloud/file-storage/pricing){: external} <br>  2 IOPS/GB | US$ 0,13 <br> 420 GB <br> [Silver](https://www.ibm.com/cloud/file-storage/pricing){: external} <br> 4 IOPS/GB  |
| **Custo por hora total** | **US$ 0,67** | **$1,90 USD**| |
** Visualize o {{site.data.keyword.blockchainfull_notm}} Platform sem encargos por 30 dias ao vincular sua instância de serviço do {{site.data.keyword.blockchainfull_notm}} Platform a um cluster grátis do {{site.data.keyword.cloud_notm}} Kubernetes. O desempenho será limitado por rendimento, armazenamento e funcionalidade. O {{site.data.keyword.cloud_notm}} excluirá seu cluster Kubernetes após 30 dias e não será possível migrar nós nem dados de um cluster grátis para um cluster pago.  

Seus custos reais variam dependendo de fatores adicionais, como taxa de transação, o número de canais que você requer, o tamanho da carga útil nas transações e o número máximo de transações simultâneas. Os exemplos de precificação acima são baseados em um cluster Kubernetes de zona única do {{site.data.keyword.cloud_notm}} apenas.  Se você tiver escolhido um cluster com múltiplas zonas, haverá taxas extras para as zonas adicionais e o balanceador de carga de múltiplas zonas necessários.
{:note}

Não há limite para o número de instâncias de serviço que é possível provisionar e associar a um único cluster Kubernetes, mas é necessário assegurar que os recursos adequados estejam disponíveis monitorando o uso de CPU, memória e armazenamento para evitar interrupção do serviço. Os nós do {{site.data.keyword.blockchainfull_notm}} Platform não precisam estar em seu próprio cluster. É possível ter outros serviços do {{site.data.keyword.cloud_notm}} em execução no cluster em que seus componentes de blockchain estão em execução, mas novamente é necessário assegurar-se de que tenha o cálculo e o armazenamento adequados para direcionar todos os requisitos de todas as instâncias de serviço.  

**Pronto para começar a usar?** Consulte [Introdução ao {{site.data.keyword.blockchainfull_notm}} Platform](/docs/services/blockchain?topic=blockchain-get-started-ibp) para ver as opções. 

## Alocações de recursos padrão
{: #ibp-saas-pricing-default}

Os valores na tabela a seguir são úteis para estimar o custo por hora de sua rede customizada com base em CPU, cálculo e armazenamento. Esses valores mínimos recomendados são suficientes para a introdução. À medida que você monitorar o uso de sua rede, poderá descobrir que seus requisitos e custos reais variam dependendo de seu caso de uso e de suas necessidades de segurança e disponibilidade.  

| **Componente** (todos os contêineres) | CPU  | Memória (GB) | Armazenamento (GB) |
|--------------------------------|---------------|-----------------------|------------------------|
| **Peer**                       | 1.1            | 2.4                   | 200 (inclui 100 GB para peer e 100 GB para CouchDB)|
| **CA**                         | 0,1            | 0,2                    | 20                     |
| **Nó de pedido**                    | 0,35           | 0,9                    | 100                    |


## faturamento
{: #ibp-saas-pricing-billing}

Suas informações de faturamento e uso para sua conta **Pagamento conforme o uso** estão disponíveis no painel do {{site.data.keyword.cloud_notm}} em seu ladrilho de [uso](https://cloud.ibm.com/billing/usage). Um serviço de medição pega as capturas instantâneas por hora de seu uso total de VPC do {{site.data.keyword.blockchainfull_notm}} Platform para que a quantia de uso acumulativo mensal seja refletida no ladrilho **Uso**.

Ao criar um novo nó, ele pode levar até uma hora para que o uso do VPC seja refletido no bloco **Uso** do painel do {{site.data.keyword.cloud_notm}}.
{:note}

### Monitorando seu uso
{: #ibp-saas-pricing-usage}

Antes de obter uma conta, é possível monitorar os custos de cluster do {{site.data.keyword.blockchainfull_notm}} Platform e do cluster Kubernetes por meio do quadro **Uso** do painel do {{site.data.keyword.cloud_notm}}. O uso de VPC do {{site.data.keyword.blockchainfull_notm}} Platform é avaliado por hora.  **Esses custos são apenas estimativas.** Os custos reais são refletidos em sua conta mensal.

#### Uso do {{site.data.keyword.blockchainfull_notm}} Platform e do Kubernetes Service

<!--This clip provides a simple example of how to view your charges for an {{site.data.keyword.blockchainfull_notm}} Platform that includes a single CA node.

![Monitoring your usage](../images/usage_monitoring.gif){: gif}
-->

Navegue para **Gerenciar** na parte superior de seu painel do {{site.data.keyword.cloud_notm}}, clique em **Faturamento e uso** e, em seguida, clique em **Uso** no menu à esquerda. O gráfico de pizza na subseção **Serviços** fornece um detalhamento de seu custo total pelos tipos de ofertas de serviços que você usou e consumiu este mês. Use esse gráfico para entender como seu {{site.data.keyword.blockchainfull_notm}} Platform, seu serviço do Kubernetes e o armazenamento contribuem com o custo total.

Quando você rolar para baixo, será possível ver um detalhamento semelhante por **Tipo** e **Custo** em uma visualização de lista. É possível localizar "Kubernetes Service" e "Blockchain Platform" listados juntamente com os outros serviços que você provisionou em seu cluster. Clique em **Visualizar planos** ao lado de cada um desses itens para entender seu detalhamento de custo por métrica. Por exemplo, `VIRTUAL_PROCESSOR_CORE_HOURS` representa o número total de horas de VPC que foram avaliadas até agora.  Use esse valor para ver quanto você vai ser cobrado com base na métrica de precificação **US$ 0,29/hora de VPC**.

#### Encargos de alocação de IP

Quando você provisiona um cluster Kubernetes no {{site.data.keyword.cloud_notm}}, uma taxa mensal fixa é avaliada para a alocação de IP. Esta taxa é cobrada por zona, de modo que se você provisionar três zonas em seu cluster, será possível multiplicar esse encargo por três. O exemplo abaixo mostra o encargo para uma única zona.

![Encargos de alocação de IP](../images/ip_allocation_charge.png "Encargos de alocação de IP do cluster Kubernetes")

Esse encargo é visível na guia **Faturas** do bloco Uso. Clique no link sob **Próxima fatura recorrente** para ver seus encargos para a alocação de IP.

#### Uso de armazenamento

Se você estiver usando o {{site.data.keyword.cloud_notm}} File Storage, os custos serão avaliados mensalmente, portanto, uma estimativa de custos de armazenamento não ficará visível até o término do mês. No entanto, o armazenamento que você provisionou durante todo o mês é listado como itens de linha no quadro Uso em **Vendas** > **Pedidos**. Consulte a coluna **Itens** para obter uma descrição do armazenamento que foi dinamicamente provisionado quando você implementou um peer, uma CA ou um nó de pedido.

## Otimizando o custo de seus nós
{: #ibp-saas-pricing-shutdown}

Um dos principais benefícios do modelo de precificação do {{site.data.keyword.blockchainfull_notm}} Platform é a capacidade de parar ou excluir recursos quando eles não são necessários.

- **Alternar seus nós para o Estado de utilização mínima**  
  A CPU em nós individuais pode ser escalada para baixo para 0,001 CPU para minimizar os encargos completamente. Tomar essas ações renderiza o nó não funcional. Quando o cálculo for necessário posteriormente, será possível usar a opção de realocação no console do {{site.data.keyword.blockchainfull_notm}} Platform para escalar para cima para o que é necessário. Para obter mais informações sobre como os recursos podem ser realocados, consulte [Realocando recursos](/docs/services/blockchain?topic=blockchain-ibp-console-govern#ibp-console-govern-reallocate-resources).

- **Excluir peer não usado e implementar um novo quando necessário**  
  Como o livro-razão é armazenado no nó de pedido, quando você implementa um novo peer e associa um canal, o peer recebe uma cópia do livro-razão distribuído. O drawback para essa abordagem é que você precisa gerar novos certificados e associar o peer aos canais novamente.

  Não é recomendável excluir um nó de CA porque os dados nele nunca poderão ser recuperados. Da mesma forma, se você tiver apenas um único nó de pedido, ele nunca deverá ser excluído.  
  {:important}

- **Monitorar e ajustar sua alocação de recurso com base em suas necessidades**  
  Ao monitorar seu uso de recurso ao longo do tempo, você pode decidir que é possível escalar para baixo os recursos que estão alocados para um nó enquanto ainda assegura o desempenho adequado. Quando você seguir instruções para [realocar recursos](/docs/services/blockchain?topic=blockchain-ibp-console-govern#ibp-console-govern-reallocate-resources) no console, os efeitos no VPC total para o nó serão atualizados e poderão ser usados para estimar os custos mensais revisados.
