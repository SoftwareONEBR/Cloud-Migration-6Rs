<h1 align="center">

# Critérios para Estratégia dos 6 R's

![6 R's Migration Strategies](https://www.qentelli.com/sites/default/files/inline-images/Cloud-Transformation.jpg)

</h1>

| Autor(es) | Data |
| -- | -- |
| @carlosdoliveira, @rafaelvelosoAZ, @rezendesfelipe | 09/17/2021|
| Versão | 2.0 |

## Escopo
Este material abrange a estratégia de 6 R's levando-se em consideração uma migração para o **Microsoft Azure**. As informações aqui apresentadas podem se aplicar para outros provedores de cloud, em alguns casos. 

## Rehost

A Estratégia de Rehost, também conhecida como Lift-and-Shift consiste em migrar os servidores selecionados, mantendo sua configuração e infraestrutura atual (IPs, balanceamento, proxy, entre outros) para o ambiente de destino, de forma a **agilizar** e **facilitar** o processo de migração. Esta é a estratégia mais comum e a que traz resultados mais rápidos por se tratar de um processo de baixo risco e rápido retorno.

Algumas premissas são exigidas para que a estratégia de rehosting seja considerada. Para estar elegível a estratégia de *rehosting*, o servidor deve:

 * Possuir um sistema operacional suportado
> Exemplo: Windows Server 2012 R2, 2016 ou mesmo um Ubuntu são exemplos de servidores suportados para replicação.
 * Possuir um dimensionamento de disco suportado
> Exemplo: Disco de sistema operacional de até 2TB, sem dualboot, com tipo de inicialização em BIOS.
 * Possuir uma configuração de placas de rede suportada pela ferramenta de migração
 * Possuir uma função suportada

Em linhas gerais esta é a primeira abordagem utilizada quando encontramos sistemas operacionais compatíveis com as ferramentas de migração.

Para um informativo completo de todos os requisitos necessários para Rehosting, é possível consultar as seguintes referências técnicas:
 * [**Máquinas virtuais Hyper-V**](https://docs.microsoft.com/en-us/azure/migrate/migrate-support-matrix-hyper-v-migration)
 * [**Máquinas virtuais em VMware**](https://docs.microsoft.com/en-us/azure/migrate/migrate-support-matrix-vmware-migration)
 * [**Quaisquer outros cenários de migração conforme especificados na documentação**](https://docs.microsoft.com/en-us/azure/migrate/migrate-support-matrix-physical-migration) 

## Replatform
A estratégia de **Replatform** é similar ao *lift-and-shift* porém algumas particularidades exigem que esta estratégia seja adotada. Também conhecida como *lift-tinker-and-shift*, tem o objetivo de permitir as primeiras otimizações na nuvem para obter benefícios tangíveis, sem necessariamente haver mudanças significativas na arquitetura da aplicação, geralmente mantendo alguns recursos de computação e rede.
> ### Exemplo
> 
> Uma stack possui 3 servidores Web atrás de um Load Balancer e 2 Bancos de dados Mysql com replicação. O servidor MySQL está rodando e uma CentOS 4.x enquanto o servidor Web é um Servidor Ubuntu 14.04-LTS. 
> 
> Para os servidores Web é possível seguir uma estratégia de Rehosting enquanto os servidores CentOS, por não estarem em uma versão compatível, devem receber uma versão mais recente do CentOS em nuvem e os dados do banco de dados devem ser migrados através dos métodos conhecidos de replicação / dump-restore. Por fim, para os servidores com função de balanceamento de carga é possível já tomar proveito de usar uma solução gerenciada, seja de um balanceador de rede padrão (Layer 4) ou um balanceador de carga para aplicação (Layer 7).

Uma outra situação é quando não se deseja fazer uma restruturação completa da sua aplicação, mas você se dispõe a fazer algumas mudanças para otimizar tempo de gerenciamento. 

Por exemplo, você deseja um serviço de Banco de dados que seja capaz de gerenciar as próprias rotinas de Backup, não depender de patching e update de sistema operacional e, consequentemente otimize 

## Refactor / Re-write / Rearchitect
Esta abordagem leva em questão uma evolução, aprimoramento ou mesmo re-estruturação completa da aplicação como é hoje. 

Exemplos disso podem ser 

Re-imagine how the application is architected and developed using cloud-native features. This is driven by a strong business need to add features, scale, or performance that would otherwise be difficult to achieve in the application’s existing environment.

Are you looking to migrate from a monolithic architecture to a service-oriented (or server-less) architecture to boost agility or improve business continuity? This strategy tends to be the most expensive, but it can also be the most beneficial if you have a good product-market fit.

## Retain
Quando um servidor é classificado como **Retain** onde precisamos de uma reflexão maior e que, neste momento a aplicação não está pronta para uma migração.

Podemos elencar alguns motivos e dentre os principais, temos os seguintes: 
 * O servidor em questão possuir uma função que não seja suportada em nuvem pública (por exemplo um servidor DHCP), ou então uma função que não faça sentido em ir para a nuvem. Por exemplo, dados de backup de curto prazo ou dados de replicação local de servidores, etc.
 * Há alguma trava contratual que impeça a migração. Por exemplo, se houve uma renovação do contrato de aluguel de servidores, logo não faz sentido, do ponto de vista financeiro, migrar para a nuvem neste exato momento. 
 * Foi identificada uma necessidade de refatoração para permitir a viabilidade técnica da mesma para nuvem, porém não há orçamento ou equipe preparada, seja por débito técnico ou alocação, para executar estas mudanças necessárias para migração. Nestes critérios, conseguimos enquadrar que a aplicação em si seguirá uma estratégia de *Retain*. 

## Retire
Diferente da estratégia de Retain, consideramos como **Retire** soluções ou aplicações que definitivamente não fazem sentido migrar para a nuvem ou que já estão marcadas para serem decomissionadas ou descontinuadas. 

Geralmente esta escolha vem do próprio contratante. Quando se trata de um serviço não suportado pela nuvem (DHCP por exemplo), é comum que se use uma estratégia de **Retire** quando haverá uma descontinuação do ambiente onpremises como um todo. Porque desta maneira, o serviço de fato não será utilizado sob nenhuma circunstância.

## Replace / Re-purchase
Também conhecida como *drop-and-shop*, dá a possibilidade de realizar a troca de um produto por outro completamente diferente para a realização de tarefas que precisam ser executadas de imediato ou ainda uma nova forma de comprar um mesmo produto. Podendo ser a mudança de uma solução local para uma solução SaaS ou a substituição do fornecedor. Como, por exemplo, a migração de dados de um sistema de gerenciamento de relacionamento com o cliente (CRM) para o Salesforce.com, um sistema de recursos humanos (RH) para Workday ou um sistema de gerenciamento de conteúdo (CMS) para Drupal. Além disso, é comumente encontrado em bancos de dados, em que se pode optar pela compra da licença do banco de dados por hora do servidor ao invés de um valor fixo inicial de aquisição.
