### Registro de Hosts via PlayBook Ansible "register.yml" ###

O método de registro a ser seguido depende das necessidades de cada host. Originalmente, o método recomendado é o **“Script curl”**, que é o padrão suportado pela Red Hat. Entretanto, é possível utilizar o **“Playbook Ansible”** para alterar configurações conforme requisitos identificados pela Consultoria da Red Hat® no ambiente, customizado para o cliente. O **“Subscription Manager”** é indicado para hosts que não foram possíveis registrar mediante os outros métodos.



> **Arquivos utilizados:**

[root@satellite-capsule ansible]# pwd
/root/ansible

[root@satellite-capsule ansible]# ls -ltr README
-rw-r--r--. 1 root root 329 Aug 30  2022 **README**

[root@satellite-capsule ansible]# ls -ltr register.yml
-rw-r--r--. 1 root root 3939 Apr  3 14:35 **register.yml**

[root@satellite-capsule ansible]# ls -ltr htsreg
-rw-r--r--. 1 root root 64860 May  8 15:45 **htsreg**

[root@satellite-capsule ansible]# ls -ltr inventory
-rw-r--r--. 1 root root 64 May  8 15:45 **inventory**

> **Script das Active Key (AK):**

[root@satellite-capsule ansible# ls -ltr group_vars/Campinas/script
-rw-r--r--. 1 root root 7668 Dec 14 12:08 **group_vars/Campinas/script**

### Procedimento para configuração dos arquivos e execução do playbook register.yml.

[root@brtlvlts2684co ansible]# cat **README**

1) Insira a entrada de hosts em ***htsreg*** (estilo /etc/hosts)
2) Insira os hosts a serem registrados no inventario ***inventory***, de acordo com os grupos (capsules). Veja mais em *group_vars*.
3) Execute o playbook, alterando a AK (cat no arquivo script). Onde "x" = "6|7|8" e "y" = "DEV|HML|PRD"
 ***"ansible-playbook -e actkey=<AK_RHELx_y> register.yml"***

### Conteúdo do arquivo (exemplos):

[1] 
[root@satellite-capsule ansible]# tail -f htsreg


10.129.230.60 brtlvlty1011sl

~

10.129.180.152 brtlvltb137sl

#

[2]
[root@satellite-capsule ansible]# cat inventory

[Server]


10.238.2.102

10.129.201.243


[Campinas]

10.129.180.152

#

[3]
[root@satellite-capsule ansible]# **ansible-playbook -e actkey=AK_RHEL6_DEV register.yml**


PLAY [Modify DNS on Server] 

TASK [Modify /etc/hosts on Server] 

PLAY [Register host to Red Hat Satellite] 

TASK [Gathering Facts] 

TASK [SM file (Oracle6)] 

TASK [SM file (Oracle7)] 

TASK [SM file (Oracle8)] 


#

### Validar o registro do host ###

[root@host-destino ~]# **subscription-manager identity**

system identity: 8dc3cd94-27aa-4515-8cfc-d22cb285fd1f

name: DirName:/O=telefonica_brasil_ti/CN=8dc3cd94-27aa-4515-8cfc-d22cb285fd1f, host-destino

org name: Telefonica Brasil TI

org ID: telefonica_brasil_ti

environment name: DEV/CV_RHEL6


