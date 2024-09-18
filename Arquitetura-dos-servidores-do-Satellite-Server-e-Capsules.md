## **Componentes da arquitetura do Red Hat Satellite versão 6.12**


> **Satellite Server:** 
O Satellite Server permite que você planeje e gerencie o ciclo de vida do conteúdo e a configuração de Capsule Servers e hosts por meio de GUI, CLI ou API. O Satellite Server organiza o gerenciamento do ciclo de vida usando organizações como unidades principais de divisão. As organizações isolam conteúdo para grupos de hosts com requisitos específicos e tarefas de administração. Por exemplo, a equipe de construção do sistema operacional pode usar uma organização diferente da equipe de desenvolvimento da web.

#

> **Capsule Servers:** Os Capsule Servers espelham o conteúdo do Satellite Server para estabelecer fontes de conteúdo em várias localizações geográficas. Isso permite que os sistemas host obtenham conteúdo e configuração dos Capsule Servers em seus locais e não do servidor Satellite central. O número mínimo recomendado de Capsule Servers é, portanto, dado pelo número de regiões geográficas onde a organização que usa Satellite opera. O Red Hat Satellite Capsule Server fornece um proxy para muitas funções do Satellite, incluindo armazenamento de repositório, DNS, DHCP e configuração mestre do Puppet. A instalação do Satellite Server contém uma instancia do Capsule Server integrada. Para ambientes distribuídos, Capsule Servers adicionais podem ser implementados em hosts separados. Esses Capsule Serves fornecem redundância para serviços Satellite, a fim de oferecer alta disponibilidade e para expandir para maiores cargas de trabalho conforme o número de hosts gerencias aumenta.
#
> **Foreman:** Aplicativo open source usado para provisionamento e gerenciamento de ciclo de vida de hosts físicos e virtuais. O Foreman pode configurar sistemas automaticamente usando vários métodos, como os módulos Kickstart e Puppet. O Foreman também fornece dados históricos para relatórios, auditoria e solução de problemas.
#
> **Katello:** Aplicativo de gerenciamento de subscrição e repositórios. Ele fornece um meio de se inscrever nos repositórios da Red Hat e fazer o download de conteúdo. Diferentes versões de conteúdo podem ser aplicadas a hosts específicos para corresponder a seus estágios em estágios de ciclo de vida completo de desenvolvimento de software (SDLC).
#
> **Candlepin:** Serviço que lida com o gerenciamento de subscrição.
#
> **Pulp:** Serviço que lida com o gerenciamento de conteúdo e repositório. O Pulp gerencia visualizações de conteúdo, planos de sincronização e a transferência e conteúdo síncrona ou com atraso para Capsule Servers.
# 
> **Hammer:** Ferramenta de CLI que fornece os equivalentes de linha de comando e shell para a maioria das funções disponíveis por meio de IU da web do servidor Satellite. O Hammer usa variáveis de ambiente, aliases e redirecionamento para outras ferramentas da CLI a fim de agilizar a interação com o servidor Satellite.
#
> **REST API:** O Red Hat Satellite inclui um serviço de API RESTful para que os administradores de sistema e desenvolvedores escrevam scripts personalizados e aplicativos de terceiros que façam interface com o Red Hat Satellite.
#

> **Fonte: https://access.redhat.com/documentation/pt-br/red_hat_satellite/6.12**

#
* ##  Satellite Server (Novo Data Center - NDC)
 
     FQDN: brtlvlts2681co.redecorp.br

    * [Hostname](https://github.com/BR-SAM-SW-HPC/imagens-vivo/blob/main/brtlvlts2681co.redecorp.br-hostname.PNG)
    * [Cpu e Memoria](#)
    * [Volumetria e Filesystem](#)
    * [Rsyslog](#) 
    * [Log Rotate](#)
    * [Kernel](#)
    * [Kdump](#)
    * [Memoria Usada (kdump)](#)
    
* ##  Capsule Chucri Zaidan (Berrini)
    
    FQDN: brtlvlts2682co.redecorp.br

    * [Hostname](#)
    * [Cpu e Memoria](#)
    * [Volumetria e Filesystem](#)
    * [Rsyslog](#)
    * [Log Rotate](#)
    * [Kernel](#)
    * [Kdump](#)
    * [Memoria Usada (kdump)](#)

* ##  Capsule Curitiba

    FQDN: brtlvlts2683co.redecorp.br

    * [Hostname](#)
    * [Cpu e Memoria](#)
    * [Volumetria e Filesystem](#)
    * [Rsyslog](#) 
    * [Log Rotate](#)
    * [Kernel](#)
    * [Kdump](#)
    * [Memoria Usada (kdump)](#)

* ##  Capsule Campinas

    FQDN: brtlvlts2684co.redecorp.br

    * [Hostname](#)
    * [Cpu e Memoria](#)
    * [Volumetria e Filesystem](#)
    * [Rsyslog](#) 
    * [Log Rotate](#)
    * [Kernel](#)
    * [Kdump](#)
    * [Memoria Usada (kdump)](#)

* ##  Capsule Sites Core

    FQDN: brtlvlts2686co.redecorp.br

    * [Hostname](#)
    * [Cpu e Memoria](#)
    * [Volumetria e Filesystem](#)
    * [Rsyslog](#)
    * [Log Rotate](#)
    * [Kernel](#)
    * [Kdump](#)
    * [Memoria Usada (kdump)](#)

* ##  Capsule Azure

    FQDN: brtazlts0070co.redecorp.br

    * [Hostname](#)
    * [Cpu e Memoria](#)
    * [Volumetria e Filesystem](#)
    * [Rsyslog](#) 
    * [Log Rotate](#)
    * [Kernel](#)
    * [Kdump](#)
    * [Memoria Usada (kdump)](#)

#
