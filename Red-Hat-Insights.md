## **Sobre o Red Hat Insights**
O Red Hat Insights ([documentação aqui](https://access.redhat.com/documentation/en-us/red_hat_insights/2023)) é um aplicativo de software como serviço (SaaS) incluído em quase todas as assinaturas do Red Hat Enterprise Linux, Red Hat OpenShift e Red Hat Ansible Automation Platform.

Alimentado por análises preditivas, o Red Hat Insights fica mais inteligente com cada peça adicional de inteligência e dados. Ele pode descobrir automaticamente insights relevantes, recomendar as próximas ações personalizadas e proativas e até mesmo automatizar tarefas. Usando o Red Hat Insights, os clientes podem se beneficiar da experiência e conhecimento técnico dos Red Hat Certified Engineers, facilitando a identificação, priorização e resolução de problemas antes que as operações comerciais sejam afetadas.

Como uma oferta SaaS, localizada no Red Hat Hybrid Cloud Console , o Red Hat Insights é atualizado regularmente. As atualizações regulares expandem o arquivo de conhecimento do Insights em tempo real para refletir os novos desafios de TI que podem afetar a estabilidade dos sistemas de missão crítica.
&nbsp;

## **Instalando o Red Hat Insights para Red Hat Enterprise Linux (RHEL).**
&ensp;
A instalação do Red Hat Insights geralmente envolve a instalação do cliente Insights e, em seguida, o registro de sistemas para uso com o Insights. Você pode usar métodos diferentes para registrar e instalar o Insights. Um assistente de registro também está disponível para orientá-lo no processo de registro e instalação do Insights. Você também pode usar a ferramenta Remote Host Configuration (RHC). O método de instalação que você usa pode depender de condições como,

* Se você está se conectando ao Red Hat pela primeira vez

* Se você usa uma determinada versão do RHEL

* Se você deseja fazer uma instalação automatizada ou instalação manual

* Outros fatores
&ensp;

## **Instalando o Red Hat Insights usando o Registration Assistant como um guia interativo.**
&ensp;
Você pode usar o Registration Assistant como ponto de partida para ajudá-lo a começar a usar o Red Hat Insights. O Assistente de Registro fornece um guia interativo para ajudá-lo a registrar e instalar o Insights. Para iniciar o Assistente de Registro, clique ou acesse:

**[Red Hat Hybrid Cloud Console > Red Hat Enterprise Linux > Red Hat Insights > Registrar Sistemas](https://console.redhat.com/insights/registration#SIDs=&tags=)**
&ensp;
## **Instalando o Red Hat Insights usando o Guia de Configuração do Cliente.**
&ensp;
Você também pode começar a usar o Insights seguindo as etapas na documentação do produto para configurar o cliente Insights. Para instalar o Red Hat Insights, use:

* Guia de configuração do cliente para Red Hat Insights

* Visão geral do cliente do Insights

* Distribuição de clientes do Red Hat Insights

O cliente Insights está disponível para os seguintes lançamentos do Red Hat Enterprise Linux (RHEL).

| RHEL release      | Comentários |
| -------------     | ------------- |
| RHEL 9            | Distribuído com o cliente Insights pré-instalado.|
| RHEL 8            | Distribuído com o cliente Insights pré-instalado, a menos que o RHEL 8 tenha sido instalado como uma instalação mínima.|
| RHEL 7                | Distribuído com o pacote RPM do cliente Insights carregado, mas não instalado.|
| RHEL 6.10 and later  | Você deve baixar o pacote RPM do cliente Insights e instalá-lo.|

## **Instalação do cliente Insights em versões mais antigas.**

* As versões 6 e 7 do RHEL não vêm com o cliente Insights pré-instalado. Se você tiver uma dessas versões, execute os seguintes comandos em seu terminal:

*[root@server ~]# yum install insights-client*

* Em seguida, registre o sistema no Red Hat Insights for Red Hat Enterprise Linux:

*[root@server ~]# insights-client --register*
&ensp;

## **Instalando o cliente Insights em um sistema existente gerenciado pelo Red Hat Cloud Access.**

Use estas instruções para implantar o Red Hat Insights para Red Hat Enterprise Linux em um sistema Red Hat Enterprise Linux (RHEL) existente conectado ao Red Hat Cloud Access.

> Pré-requisitos

* Acesso de nível raiz para o sistema.

> Procedimento

* Digite o seguinte comando para instalar a versão atual do pacote do cliente Insights:

*[root@server ~]# yum install insights-client*

> Note

Instalação do cliente Insights em versões mais antigas. 
As versões 6 e 7 do RHEL não vêm com o cliente Insights pré-instalado. Se você tiver uma dessas versões, execute os seguintes comandos em seu terminal:

*[root@server ~]# yum install insights-client*
&ensp;
## **Instalando insights-client em um sistema existente gerenciado pelo Red Hat Update Infrastructure.**

Use estas instruções para implantar o Insights for Red Hat Enterprise Linux em um sistema Red Hat Enterprise Linux existente, adquirido no mercado de nuvem, gerenciado pela Red Hat Update Infrastructure (RHUI).

> Pré-requisitos

* Acesso de nível raiz para o sistema.

> Procedimento

* Digite o seguinte comando para instalar a versão atual do pacote do cliente Insights::

*[root@server ~]# yum install insights-client*

&nbsp;
Como a CLI do cliente Insights e o arquivo de configuração interagem.

O cliente Insights é executado automaticamente, de acordo com as configurações de seu agendador. Por padrão, ele é executado a cada 24 horas. Para executar o cliente interativamente, insira o comando insights-client.

Quando o cliente é executado, os seguintes valores e configurações controlam seu comportamento:

* Os valores fornecidos ao executar insights-client a partir da CLI substituem temporariamente as configurações predefinidas do arquivo de configuração e as configurações do ambiente do sistema. Quaisquer valores fornecidos para opções no comando insights-client são usados apenas para essa instância do cliente Insights.

* As configurações nos arquivos de configuração (/etc/insights-client/insights-client.conf e /etc/insights-client/remove.conf) substituem as configurações do ambiente do sistema.

* Os valores de quaisquer variáveis de ambiente do sistema (printenv) não são afetados pela CLI ou pelos arquivos de configuração do cliente.

Note

Se você estiver usando o RHEL 6.9 ou anterior, o comando do cliente é *redhat-access-insights.*
&ensp;
## **Instalando o cliente Insights em uma instalação mínima do RHEL.**

O cliente Insights não é instalado automaticamente em sistemas executando a instalação mínima do Red Hat Enterprise Linux 8.
Para obter mais informações sobre instalações mínimas, consulte Configurando a seleção de software em Executando uma instalação RHEL padrão.

> Pré-requisitos

* Acesso de nível raiz ao sistema.

> Procedimento

1. Para criar uma instalação mínima com o cliente Insights, selecione Minimal Installation nas opções RHEL Software Selection no instalador do Anaconda.

2. Certifique-se de selecionar a caixa de seleção Padrão na seção Software Adicional para Ambiente Selecionado. A opção Standard inclui o pacote insights-client na instalação do RHEL.

3. Se você não marcar a caixa de seleção Padrão, o RHEL será instalado sem o pacote insights-client`. Se isso acontecer, use dnf install para instalar o cliente Insights posteriormente.
&ensp;

## **Registrando seu sistema com o Red Hat Insights.**
&ensp;
Depois de instalar o cliente Insights e configurar a autenticação, você deve registrar seu sistema no Red Hat Insights para Red Hat Enterprise Linux. O registro permite que você use os serviços do Red Hat Insights para Red Hat Enterprise Linux.

Como opção, você pode atribuir um nome de exibição para seu host ao registrar seu sistema. O nome de exibição identifica o sistema no Red Hat Insights para Red Hat Enterprise Linux UI. Se você não atribuir um nome de exibição ao registrar o sistema, o Red Hat Insights para Red Hat Enterprise Linux usa o valor padrão em /etc/hostname.
 
> Pré-requisitos

* Permissões de nível raiz para seu sistema.

* O cliente Insights está instalado em seu sistema.

> Procedimento

1. Insira o comando insights-client com a opção --register.

*[root@insights]# insights-client --register*

2. Opcional. Para especificar o nome de exibição do sistema, inclua a opção --display-name. 

> Por exemplo:

*[root@insights]# insights-client --register --display-name*

> Verificação

* Insira o comando insights-client com a opção --status.

*[root@insights]# insights-client --status*

O sistema é registrado localmente via arquivo .registered.
Registrado em 2019-08-20T12:56:48.356814
A API do Insights confirma o registro.

Agora você pode acessar os serviços Red Hat Insights for Red Hat Enterprise Linux baseados em nuvem.
&ensp;

## **Cancelando o registro do seu sistema com o Insights.**
&ensp;
Você pode cancelar o registro do seu sistema com o Red Hat Insights para Red Hat Enterprise Linux. Ao fazer isso, as informações do sistema não são mais carregadas no Insights for Red Hat Enterprise Linux.

> Pré-requisitos

• Acesso de nível raiz ao seu sistema.

• Seu sistema está registrado no Insights for Red Hat Enterprise Linux.

> Procedimento

1. Insira o comando insights-client com a opção --unregister.

*[root@insights]# insights-client --unregister*

Registro cancelado com sucesso do Red Hat Insights Service

> Verificação

* Insira o comando insights-client com a opção --status.

*[root@insights]# insights-client --status*

System is NOT registered locally via .registered file. 
Unregistered at 2021-03-12T10:36:39.257300
Insights API says this machine was unregistered at 2021-03-12T00:36:39.000Z
&ensp;

## **Registrando novamente seu sistema com o Red Hat Insights.**

> Observação

A opção –-force-reregister está sendo obsoleta. A execução da opção –-force-reregister com o comando insights-client resultará na seguinte mensagem de erro:

*[root@insights]# ERROR: `force-reregistration`*

foi reprovado. 

Por favor, use `insights-client --unregister && insights-client --register` 

em vez de

Para registrar novamente os sistemas no Red Hat Insights para Red Hat Enterprise Linux e também evitar quaisquer entradas de host duplicadas no serviço de inventário do Insights após o novo registro, execute o comando insights-client duas vezes usando duas opções:

1. --cancelar registro
2. --registrar

> Pré-requisitos

* Permissões de nível raiz para seu sistema.

* O cliente Insights está instalado em seu sistema.

> Procedimento

1. Insira o comando insights-client com a opção --unregister.

*[root@insights]# insights-client --unregister*

2. Insira o comando insights-client com a opção --register.

*[root@insights]# insights-client --register*

> Verificação

*Successful implementation of the re-registration commands using insights-client command with the —-unregister option followed by the insights-client command with the —-register option results in the following message:*

*[root@insights]# Successfully uploaded report for*

Visualize o console do Red Hat Insights em https://console.redhat.com/insights/
&ensp;

## **Exibindo a versão do cliente.**

Você pode exibir a versão do cliente e a versão principal do cliente.

> Pré-requisitos

* Acesso de nível raiz ao seu sistema.

> Procedimento

* Insira o comando insights-client com a opção --version.

*[root@insights]# insights-client --version*

Client: 3.0.6-0
Core: 3.0.121-1


&ensp; &ensp;


## **Exemplos:**


* **Instalação do Pacote no RHEL 6 (idem para RHEL 7)**

[root@nome_host ~]# cat /etc/redhat-release

Red Hat Enterprise Linux Server release 6.6 (Santiago)

[root@nome_host ~]#

[root@nome_host ~]# yum install insights-client

Loaded plugins: product-id, search-disabled-repos, security, subscription-manager

This system is not registered with an entitlement server. You can use subscription-manager to register.

Setting up Install Process

Installed:

  insights-client.noarch 0:3.0.14-4.el6_10

Complete!

[root@nome_host ~]#

[root@nome_host ~]# rpm -qa|grep insights

insights-client-3.0.14-4.el6_10.noarch

[root@nome_host ~]#

&ensp;
- Registrando o host:

[root@nome_host ~]# insights-client --register

[root@nome_host ~]#

&ensp;
- Host Registrado

root@nome_host ~]# yum list installed | grep -i insights

insights-client.noarch              3.0.14-4.el6_10                    @convert-to-rhel

root@nome_host ~]#

root@nome_host ~]# insights-client --status

System is registered locally via .registered file. Registered at 2023-01-30T12:27:58.761197

Insights API confirms registration.

root@nome_host ~]#
