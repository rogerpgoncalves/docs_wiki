# BigData & Security

**Technical Support Bulletin:**

|  TSB 202208    |Instalação de pacotes e atualização do ansible LNCC |                                          
|----------------|----------------------------------------------------| 
|Versão          | 001                                                |
|DATA            | 09/11/2022                                         |
| Elaboração     | Julio Shimizu                                      |
| Validação      | Ricardo José                                       |
| Comentários    | Versão Inicial                                     |

**Objetivo:**

> 	Descrição das etapas para instalar e atualização dos nomes dos pacotes nas regras do ansible.

1)	Identificar se a solicitação é para instalar ou só atualização do ansible.

2)	Validar os pacotes instalados nos servidores via clush, nesse exemplo o pacote é gl2ps

> sudo clush -bw @all,@sequana_all "rpm -qa | grep gl2ps"
Foi identificado nesse comando que não havia o pacote instalado nas máquinas.
Caso esse comando indique que o pacote já foi instalado seguir para o passo 3 e depois continuar no passo 8

3)	Abrir change SAB,enviar email ao cliente, anexar no SAB, relacionar chamado com a change e após atualização anexar OK do cliente. 

4)	Verificar servidores que estão IDLE para instalação
> Ambiente BASE:
> sinfo -p all

> Ambiente EXP
> sinfo -p sequana_all

5)	Precisa identificar no chamado se tem a informação de quais máquinas precisaria instalar o pacote, CPU, GPU, SMP, PHI, GDL, LOGIN, Ambiente BASE e Ambiente EXPANSAO, caso não tenha a informação perguntar para o solicitante via chamado. Instalar em um unica maquina de cada tipo que esta IDLE CPU, GPU e LOGIN, não havendo problema instalar nos nodes restantes

6)	Após aprovação da CHANGE instalar pacotes via clush nos nodes IDLE que não possuem os pacotes
sudo clush -w sdumont[1000-1143,1288-1338,1340-1359,3037-3161,3163-3179] "yum install gl2ps gl2ps-devel -y"

7)	Após instalação revalidar os nodes que foram instalados no passo 2.

8)	 Validar se os arquivos ansible estão iguais usando sum
BASE:

> sudo clush -bw sdumont[0-5] "sum /etc/ansible/core-config/playbooks/roles/login_packages/tasks/main.yml"
> sudo clush -bw sdumont[0-5] "sum /etc/ansible/core-config/playbooks/roles/compute_packages/tasks/main.yml"

**EXP:**

Não precisa pois estão em NFS

9)	Editar ansbile CPU,GPU,LOGIN (EXP), e login e package no BASE.
BASE
Logar no sdumont0 e rodar os comandos abaixo:

> sudo vi /etc/ansible/core-config/playbooks/roles/login_packages/tasks/main.yml

> sudo vi /etc/ansible/core-config/playbooks/roles/compute_packages/tasks/main.yml

EXP (No mesmo arquivo possue 3 tipos de maquinas CPU ,GPU e LOGIN se atentar)
Logar no sdumont20 ou sdumont21, precisar checar onde está montado o filesystem do /etc/ansible.

> vi /etc/ansible/inventories/group_vars/all/addons/sequana_packages.yml

10)	Após edição efetuar a copia para os nodes de 1 até 5 , e no expansão não há necessidade pois esta em NFS

Estando logado no sdumont0 onde foi alterado o arquivo:

> sudo clush -w sdumont[1-5] -c /etc/ansible/core-config/playbooks/roles/login_packages/tasks/main.yml
> sudo clush -w sdumont[1-5] -c /etc/ansible/core-config/playbooks/roles/compute_packages/tasks/main.yml
