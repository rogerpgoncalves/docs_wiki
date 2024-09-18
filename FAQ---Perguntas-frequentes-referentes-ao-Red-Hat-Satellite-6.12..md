
# Documento instrutivo para a equipe técnica Atos/Eviden.         

> Este documento é voltado às equipes técnicas que atuam com Red Hat Satellite da Telefônica Brasil S/A. Neste, são contempladas as perguntas frequentes referentes ao Red Hat® Satellite 6.12.
#

# Registro
> **Como registrar um host?**

O documento instrutivo “RegistroSatelliteTEF” detalha os métodos de registro de hosts Red Hat Enterprise Linux (RHEL) ao Red Hat Satellite 6.10. Atualmente, os métodos de registro são: 

* Script curl (padrão)

* Subscription Manager

* Playbook Ansible (customizado)

Além disso, é possível utilizar o script /root/register.sh, disponível nos capsules.

>**Como registrar um host?**

O método de registro a ser seguido depende das necessidades de cada host. Originalmente, o método recomendado é o “Script curl”, que é o padrão suportado pela Red Hat. Entretanto, é possível utilizar o “Playbook Ansible” para alterar configurações conforme requisitos identificados pela Consultoria da Red Hat® no ambiente, customizado para o cliente. O “Subscription Manager” é indicado para hosts que não foram possíveis registrar mediante os outros métodos.

>**Como corrigir erros de registro?**

O documento instrutivo “ErrosRegistroTEF” detalha os erros de registro de hosts Red Hat Enterprise Linux® (RHEL) ao Red Hat® Satellite 6.10, com soluções. Ademais, o script /root/register.sh, disponível nos capsules, automatiza as correções, após os erros serem identificados pelo usuário.

>**Há diferença entre o registro de hosts RHEL de outras distribuições?**

Não. Os métodos de registros são os mesmos, exceto pré-requisitos. Possivelmente, será necessário instalar o pacote “subscription-manager”, realizar o update e remover alguns pacotes (tal qual “rhn-client-tools”) como etapas adicionais. Verifique na documentação oficial quais hosts são suportados no Red Hat® Satellite 6.10.



##
# **Conversão para RHEL**

> **Como converter hosts OEL 7.9 para RHEL 7.9?**

O documento instrutivo “Convert2RHEL-OEL79” detalha as etapas necessárias para conversões de sistemas Oracle Enterprise Linux® (OEL) para Red Hat Enterprise Linux® (RHEL), versões 7.9, utilizando o Red Hat® Satellite 6.10. Certifique-se de que há backup disponível. Verifique na documentação oficial quais hosts são suportados para conversão.


##
# **Repositórios e pacotes**

> Como gerenciar repositórios nos hosts?

Assegure que o host está corretamente registrado no Red Hat® Satellite. Identifique a identidade do sistema, o nome do host, da organização, ID da organização e o nome do ambiente (<lifecycle-enviorment>/<content_view> )
    
    subscription-manager identity

Verifique se o subscription-manager está configurado para gerenciar repositórios no host. O valor esperado é 1 (enabled).

    grep manage_repos /etc/rhsm/rhsm.conf

Ateste que não há repositórios além do gerenciado pelo subscription-manager. Somente deverá constar o “/etc/yum.repos.d/redhat.repo”.

    ls /etc/yum.repos.d/*.repo

Para visualizar repositórios disponíveis (na Content View e Lifecycle Environment registrados):

    subscription-manager repos --list

Para habilitar/desabilitar repositórios:

    subscription-manager repos --[enable/disable] <Repo ID>

> Como corrigir erros de repositório “[Errno 14] problem making ssl connection” nos hosts?
Os pacotes “nss”, “curl” e “subscription-manager” deverão ser atualizados. Recomendamos, inicialmente, a conexão direta com a CDN da Red Hat (registro) devido à possível necessidade de atualização de dependências. Posteriormente, o host poderá ser registrado no Red Hat® Satellite 6.10.


1. **Remova pacotes katello, caso estejam presentes**

    a. rpm -qa | grep katello 

    b. yum remove katello*

2. **Limpe as configurações do subscription-manager**

    a. subscription-manager clean

3. **Ajuste o arquivo de configuração RHSM (/etc/rhsm/rhsm.conf)**

    a. CDN da Red Hat.  
    
    Validar
    
    i. hostname = subscription.rhsm.redhat.com
    
    ii. prefix = /subscription

    iii. baseurl= https://cdn.redhat.com

    b. manage_repos = 1

    c. proxy_hostname = nskp.redecorp.br

    d. proxy_port = 8080

4. **Registre o host mediante o método Activation Key**

    a. subscription-manager register

5. **Atache o pool necessário para acesso de repositórios externos**

    a. subscription-manager list --all --available

    b. subscription-manager attach --pool=<pool_id>

6. **Limpe o cache do yum**

    a. yum clean all

7. **Atualize os pacotes necessários**

    a. yum update nss curl subscription-manager

8. **Desregistre e limpe o cache do subscription-manager**

    a. subscription-manager unregister

    b. subscription-manager clean

9. **Instale o pacote katello do capsule responsável pelo registro local**

    a. yum localinstall katello-ca-consumer

10. **Verifique o proxy do RHSM (/etc/rhsm/rhsm.conf)**

    a. proxy_hosname =
    
    b. proxy_port =

11.  **Verifique que não há proxy, na comunicação host-capsule, em variáveis de ambiente e na configuração do subscription-manager.**

        a. export no_proxy="brtlvlts2681co.redecorp.br,brtlvlts2682co.redecorp.br,brtlvlts2683co.redecorp.br,brtlvlts2684co.redecorp.br,brtlvlts2686co.redecorp.br,$no_proxy"

        i. A configuração acima é temporária. Assegure que seja persistente

12. **Registre via AK**

    a. subscription-manager register --org=telefonica_brasil_ti --activationkey=${AK}

    i. AK: activation key para registro


##
# **Nomenclatura**

> **Capsule integrado**

O capsule integrado é o servidor Satellite primário. No ambiente da Telefônica Brasil S/A:

* Capsule da localização “Novo Data Center” (NDC)

    FQDN: brtlvlts2681co.redecorp.br

> **Capsule**

O capsule é um servidor que fornece serviços para discovery, provisionamento e configuração de hosts, podendo ser externo ao Satellite primário (capsule integrado). No ambiente da Telefônica Brasil S/A:

* Novo Data Center (NDC)

  FQDN: brtlvlts2681co.redecorp.br

* Chucri Zaidan (Berrini)

  FQDN: brtlvlts2682co.redecorp.br

* Curitiba

  FQDN: brtlvlts2683co.redecorp.br

* Campinas

  FQDN: brtlvlts2684co.redecorp.br

* Sites Core

  FQDN: brtlvlts2686co.redecorp.br

* Azure

  FQDN: brtazlts0070co.redecorp.br

> **Host**

Um host é qualquer cliente Linux que o Red Hat® Satellite gerencia.

#
# Documentação oficial

[Convert2RHEL](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/converting_from_an_rpm-based_linux_distribution_to_rhel/index)

[Convert2RHEL Support Policy](https://access.redhat.com/support/policy/convert2rhel-support)

[Red Hat® Satellite 6.12](https://access.redhat.com/documentation/en-us/red_hat_satellite/6.12/html/managing_hosts/index)

