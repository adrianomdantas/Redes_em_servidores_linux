
# Introdução

Tudo começou com um jovem de 21 anos chamado **Linus Benedict Torvalds** que em 25 de Agosto de 1991 apreesentou a primeira versão do Linux, a 0.01, mais tarde vieram mais 3 versões 94(v1.0), 96(v2.0), 2001(v3.0), 2015(v4.0)  
A primeira coisa a saber é que o Linux não é um sistema operacional e sim um nucleo que faz a ponte entre as distribuições (linguagens de alto nivel) com a linguagem de baixo nível (linguagem de máquinas.  


# Debian GNU/Linux
[![](https://www.debian.org/Pics/openlogo-50.png)](https://www.debian.org/ "Comunidade Debian" ) 


O Debian é uma das distribuições mais tradicionais, anunciado em 1993 pelo Ian Murdock, e desde 94 é distribuido no espirto GNU (sistema de softwares livres), em 1996 veio sua primeira versão estável.  
Um dos motivos do Debian ser uma das principais distribuições linux é seu gerenciamento de pacotes conhecido como APT (Advanced Packet tool), cada aplicação do Debian ode ser facilmente instalada no sistema por meio do APT.


# Ubunto Server
[![](https://assets.ubuntu.com/v1/ad9a02ac-ubuntu-orange.gif "Pagina Ubuntu")](https://ubuntu.com/)

O Ubunto hoje em dia é a distribuição mais usada em desktops, tem uma etratégia agressiva de lançar uma atualização a cada 6 meses, isso acaba deixando um pouco instável, porém, para contirnar este problema, a cada 2 anos é lançada uma versão TLS com suporte de longa duração(5anos), tem suporte da Canonical, uma empresa com fins lucrativos.  
Devido ao supprte a serviços de infraestrutura como (IaaS), E comum que empresas queiram contratos que garantam o funcionamento ininterrupto do sistema, e neste quesito, o Debin não consegue prover.

# Revisão de comandos basicos  

```
sysadmin@Linux:~$ mkdir teste
sysadmin@Linux:~$ touch ./teste/arquivo1.txt ./teste/arquivo2.txt 
sysadmin@Linux:~$ cd teste 
sysadmin@Linux:~/teste$ le -l
total 0
-rw-rw-r-- 1 sysadmin sysadmin 0 Mai 11 14:53 arquivo1.txt
-rw-rw-r-- 1 sysadmin sysadmin 0 Mai 11 14:53 arquivo2.txt
sysadmin@Linux:~/teste$ rm arquivo1.txt
sysadmin@Linux:~/teste$ ls -l
total 0 
-rw-rw-r-- 1 sysadmin sysadmin 0 Mai 11 14:53 arquivo2.tx
sysadmin@Linux:~/teste$ cd ..
sysadmin@Linux:~$ rm -rf ./teste 
sysadmin@Linux:~$ nano script.sh
(...) Executa o edutor de texto NANO
(...) crtl+X para sair 
sysadmin@Linux:~$ chmod +x ./script.sh 
sysadmin@Linux:~$ ls -l 
total 0
-rwxrwxr-x 1 sysadmin sysadmin 0 Mai 11 14:53 script.sh 
sysadmin@Linux:~$ ./script.sh
(...) Executa o script 
```

# Estrutura de diretórios do Linux

Assim como no Unix, no linux, os discos e partições ficam ocultas tendo o usuário apenas acesso a visão logica  da árvore de diretório do Linux.  
Apenas administradores tem uma série de ferramentas para visualizar os discos como por exemplo o comando **fdisk** ou a tabela de partições que fica rm **/etc/fstab**  
**FHS** é um padrão seguido pela comunidade Linux que orienta como os diretórios basicos devem ser nomeados e organizados, não para engessar o desenvolvedor e sim para facilitar a localização de arquivos na estrutura  
A arvore do Linux tem um ponto principal que é representado pelo "/", ou seja, é pasta principal do sistema, todos os outros diretórios são subdiretõrios    

![Arvore de diretório linux](Imagens/Linuxtree.png)  

Uma boa pratica, é deixar pelomenos as partições /home (pasta doos usuarios e /var (arquivos de log do sistema) fiquem em uma partição a parte para evitar que quando cheios, não comprometer o funcionamento do sistema.  
A tabela a baixo, mostra os diretórios que devem existir a partir da raiz do linux.  

|Diretórios| Descrição|Observaçãso|
|---|---|---|
|/bin|Binários essenciais de programas/comandos||
|/boot|Arquivos estáticos de carregador de boot||
|/dev|Arquivos que representam dispositivos fisicos||
|/etc|Arquivos de configuração do sistema||
|/home|Pasta dos usuários|Opcional|
|/lib|Modulos do kernel e bibliotecas compartilhadas||
|/media|Ponto de montagem de mídia removíveis||
|/mnt|Ponto de montagem de sistema de arquivos temporários||
|/opt|Pacotes de softwares adiciionados||
|/proc|Informações de processos do kernel||
|/root|Pasta do superusuário root|Opcional|
|/sbin|Bináruos essenciais dos sistema||
|/srv|Dados providos pelo servidor||
|/tmp|Arquivos temporários||
|/usr|Hierarquia secundária||
|/var|Dados variáveis (logs)||

# Navegação de arvore de diretórios

