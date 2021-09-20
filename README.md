<h1 align="center">

# Critérios para Estratégia dos 6 R's

![6 R's Migration Strategies](https://www.qentelli.com/sites/default/files/inline-images/Cloud-Transformation.jpg)

</h1>

| Autor | Data |
| -- | -- |
| Carlos Oliveira | 09/10/2021|
| Versão | 1.0 |

## Escopo
Este material abrange a estratégia de 6 R's levando-se em consideração uma migração para o **Microsoft Azure**. As informações aqui apresentadas podem se aplicar para outros provedores de cloud, em alguns casos. 

## Rehost

A Estratégia de Rehost, também conhecida como Lift-and-Shift consiste em replicar os servidores selecionados para o ambiente de destino de forma a **agilizar** e **facilitar** o processo de migração. Esta é a estratégia mais comum e a que traz resultados mais rápidos por se tratar de um processo de baixo risco e rápido retorno.

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
A estratégia de **Replatform** é similar ao *lift-and-shift* porém algumas particularidades exigem que esta estratégia seja adotada. Um servidor sem um sistema operacional suportado, por exemplo, pode se encaixar nesta estratégia. O approach de migração neste caso é preparar uma instância virtual na nuvem pública e realizar uma migração individualiada dos dados. 
> ### Exemplo
> 
> Uma stack possui 3 servidores Web atrás de um Load Balancer e 2 Bancos de dados Mysql com replicação. O servidor MySQL está rodando e uma CentOS 4.x enquanto o servidor Web é um Servidor Ubuntu 14.04-LTS. 
> 
> Para os servidores Web é possível seguir uma estratégia de Rehosting enquanto os servidores CentOS, por não estarem em uma versão compatível, devem receber uma versão mais recente do CentOS em nuvem e os dados do banco de dados devem ser migrados através dos métodos conhecidos de replicação / dump-restore.

Uma outra situação é quando não se deseja fazer uma restruturação completa da sua aplicação, mas você se dispõe a fazer algumas mudanças para otimizar tempo de gerenciamento. 

Por exemplo, você deseja um serviço de Banco de dados que seja capaz de gerenciar as próprias rotinas de Backup, não depender de patching e update de sistema operacional e, consequentemente otimize 

## Refactor / Re-write / Rearchitect
Esta abordagem leva em questão uma evolução, aprimoramento ou mesmo a re-estruturação completa da aplicação em relação a como ela é hoje. No Refactor / Re-write / Rearchitect você não vai simplesmente tentar encaixar a arquitetura da aplicação atual na nuvem, mas sim fazer uma rearquitetura; adotar os serviços gerenciados que o provedor de nuvem fornece.

Neste R, repensa-se como o aplicativo é arquitetado e desenvolvido usando recursos nativos da nuvem. Isso acontece devida a uma forte necessidade de negócios de adicionar recursos, escalar recursos ou aprimorar o desempenho da aplicação que, de outra maneira, seria dificilmente alcançável tendo em vista o seu ambiente existente.

Você quer migrar de uma arquitetura monolítica para uma arquitetura orientada a serviços (ou serverless) para aumentar a agilidade ou melhorar a continuidade dos negócios? Essa estratégia tende a ser a mais cara, mas também pode ser a mais benéfica se você tiver uma boa adequação do produto ao mercado.

### Aplicação do Refactor / Re-write / Rearchitect em Azure

* Mudar a arquitetura de um servidor web, adicionando um Azure Load Balancer na frenter do servidor ao invés de deixá-lo exposto à web;

* Refatorar a aplicação para que ela rode em uma Instância de Contêiner do Azure ao invés de rodar em uma máquina virtual, garantindo a "portabilidade" da aplicação para outros ambientes;

* Adotar premissas de computação serverless com o Azure Functions ou Azure Logic Apps.

## Retain
Quando um servidor é classificado como **Retain** entendemos que sua estratégia envolve a não-migração da workload. 

Principalmente isso se dará ao fato de possuir uma função que não seja suportada em nuvem pública (por exemplo um servidor DHCP), ou então uma função que não faça sentido em ir para a nuvem. Por exemplo, dados de backup de curto prazo ou dados de replicação local de servidores, etc.

## Retire
Diferente da estratégia de Retain, consideramos como **Retire** soluções ou aplicações que definitivamente não fazem sentido migrar para a nuvem ou que já estão marcadas para serem decomissionadas ou descontinuadas. 

Geralmente esta escolha vem do próprio contratante. Quando se trata de um serviço não suportado pela nuvem (DHCP por exemplo), é comum que se use uma estratégia de **Retire** quando haverá uma descontinuação do ambiente onpremises como um todo. Porque desta maneira, o serviço de fato não será utilizado sob nenhuma circunstância.

## Replace / Re-purchase



