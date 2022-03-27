[HOME](/README.md/)/[Proximo](EmConstrução.md)

### Introdução

Tudo começou com um jovem de 21 anos chamado **Linus Benedict Torvalds** que em 25 de Agosto de 1991 apreesentou a primeira versão do Linux, a 0.01, mais tarde vieram mais 3 versões 94(v1.0), 96(v2.0), 2001(v3.0), 2015(v4.0)  
A primeira coisa a saber é que o Linux não é um sistema operacional e sim um nucleo que faz a ponte entre as distribuições (linguagens de alto nivel) com a linguagem de baixo nível (linguagem de máquinas.  


### Debian GNU/Linux
[![](https://www.debian.org/Pics/openlogo-50.png)](https://www.debian.org/ "Comunidade Debian" ) 


O Debian é uma das distribuições mais tradicionais, anunciado em 1993 pelo Ian Murdock, e desde 94 é distribuido no espirto GNU (sistema de softwares livres), em 1996 veio sua primeira versão estável.  
Um dos motivos do Debian ser uma das principais distribuições linux é seu gerenciamento de pacotes conhecido como APT (Advanced Packet tool), cada aplicação do Debian ode ser facilmente instalada no sistema por meio do APT.


### Ubunto Server
[![](https://assets.ubuntu.com/v1/ad9a02ac-ubuntu-orange.gif "Pagina Ubuntu")](https://ubuntu.com/)

O Ubunto hoje em dia é a distribuição mais usada em desktops, tem uma etratégia agressiva de lançar uma atualização a cada 6 meses, isso acaba deixando um pouco instável, porém, para contirnar este problema, a cada 2 anos é lançada uma versão TLS com suporte de longa duração(5anos), tem suporte da Canonical, uma empresa com fins lucrativos.  
Devido ao supprte a serviços de infraestrutura como (IaaS), E comum que empresas queiram contratos que garantam o funcionamento ininterrupto do sistema, e neste quesito, o Debin não consegue prover.

### Revisão de comandos basicos  

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
### Estrutura de diretórios do Linux

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

### Navegação de arvore de diretórios

Para a navegação no Linux, usa-se o comando **cd** , ex: ` ~$ cd nome_do_diretório ` nete caso estamos usando um caminho relativo, parte do diretório atual que o usuário está, é considerado caminho completo todo aquele que começa a partir da rais **/**.   
Existe um caminho para sabermos em qual diretório estamos, é o comando **pmd**.   
Também tem os atalhos como **~** que leva direto ao diretório do usuário ou o **/** que leva direto ao diretório raiz, ou seja, o **~** para o usuário fulano, subistituie o **/home/fulano.**  
O comando **"."** (ponto) faz referencia ao diretório atual e o comando **".."** (2 pontos) faz referência a um nível superior.

Usando o comando **ls -l** com o caminha absoluto
```
root@Linux:/# ls -l /etc/dhcp
total 28
(...)
-rw-w--w-- 1 root 1735 Jan 16 2017 dhclient.conf 
-rw-w--w-- 1 root 3331 Jan 19 2017 dhcpd6.conf 
-rw-w--w-- 1 root 3496 Jan 19 2017 dhspd.conf 
```
Usando o comando **ls -l** com o camilho relativo a partir da posição corrente com e sem o **"."**.
```
root@Linux:/# cd etc 
root@Linux:/etc ls -l ./dhcp/
total 28
(...)
-rw-r--r-- 1 root root 1735 Jan 16 2017 dhclient.conf
-rw-r--r-- 1 root root 3331 Jan 19 2017 dhcpd6.conf
-rw-r--r-- 1 root root 3496 Jan 19 2017 dhspd.conf
``` 
```
root@Linux:/# cd etc 
root@Linux:/etc ls -l dhcp/
total 28
(...)
-rw-r--r-- 1 root root 1735 Jan 16 2017 dhclient.conf
-rw-r--r-- 1 root root 3331 Jan 19 2017 dhcpd6.conf
-rw-r--r-- 1 root root 3496 Jan 19 2017 dhspd.conf
```

### Manipulação de arquivos e diretórios

Para a manipulação de arquivos, são utilizados os seguintes comandos:

|Comando|Ação|
|:---:|---|
|touch|cria um arquivo vazio|
|cat|consulta um arquivo|
|cp|copia um arquivo|
|mv|move ou renomeia uma rquivo|
|rm|remove um arquivo|
|mkdir|cria um diretório|
|rmdir|remove diretorio(vazio)|

Um arquivo também é criado automaticamente quando tentamos executa-lo com um editor de texto ex: `~$ vi arquivo.txt` automaticamente o **arquivo.txt** será criado no local em que o comando foi executado.  
Os editores de texto mais comuns no Linux são: vi, vim, nano e mcedit sendo que os dois ultimos são os mais amigaveis para aprender a mexe, e os dois primeiros os mais usados pelos administradores por praticas antigas e por muitas vezes serem a unica opção em um servidor linux.  
**Resumo das teclas e comandos no vi/vim**
|Tecla/comando|Ação|
|:-:|-|
|A|Inserir texto no final da linha|
|dd|Remover uma linha inteira (e colocar na memoria)|
|i|Entrar em modo de edição na posição atual do cursor|
|I|Insere texto no inicio da linha|
|o|Adiciona linha abaixo do cursos atual|
|O|Adicionar linha acima do cursor atual|
|p|Colar conteúdo da memoria no texto|
|r|Substituir um único caractere|
|s|Substituir texto na atual posição do cursor|
|u|desfaze a ultima ação executada|
|x|Apagar um unico caractere|
|y|Copiar um item na memoria|
|yy|Copiar uma linha inteira na memoria|
|:!|Permite executar um comando do shell|
|:q|Sair do aplicativo|
|:q!|Sair do aplicatidvo sem salvar as alterações|
|:wq|Sair do aplicatidvo e salvar as alterações|
|:w|Salva as alteraçoes do arquivo sem sair|

Outro comando bem util é o **ln -s**, que cria um link simbólico (atalho) para um arquivo que esteja em outro diretório, por exemplo:  
Este comando vai criar um link simbólic (atalho) no diretório home para o arquivo **texto.txt** que está no diretório root 
`[root@localhost home]# ln -s /root/texto.txt /home/`
OBS.: O link simbólico não precisa ter o memso nome do arquivo original

### Permissões em arquivos e diretórios

Assim como no Unix, o Linux tem basicamente 3 tipos de permissão para os arquivos  
r ou 4 ( 2<sup>4</sup> ) = leitura | w ou 2 ( 2<sup>1</sup> ) = escrita | x ou 1 ( 2<sup>0</sup> ) = execição  

**Leitura**, permite a visualização porém não a modificação ou execução;  
**Escrita**, permite a modificação assim como deletar ou mover o arquivo;  
**Execução**, Permite a execussão do arquivo por script ou programas. 

Existem também 3 níveis de permissão para os arrquivos:    
Usuário | Grupo | Outros  

Usuário é o proprietário ou ou criador do arquivo que automaticamente pertence a um grupo de mesmo nome, e caso o objeto não se encaixe nestas duas opções, automaticamente é enxergado pelo sistema como outros, mas isso pode ser alterado pelo administrador do sistema  
Estes níveis podem ser observados quando utilizar o comando **ls -l**  
```
[root@localhost home]# ls -l
total 4
drwxr-xr-x 2 root root 37 Mar 27 12:36 teste


```
Observe que no começo da linha tem os caracteres `drwxr-xr-x`, devemos enxergar estes caracteres separadamente d|rwx|r-x|r-x: 
**d**		diretório do sistema (tabela 1.1)  
**rwx**		permissão de usuário/proprietário (tabela 1.2)   
**r-x**		permissão do grupo (tabela 1.2)  
**r-x**		permissão outros (tabela 1.2)  
**root**	Proprietário  
**root**	grupo
   
tabela 1.1  
|Caractere|Descrição|
|:---:|:---|
|-|Arquivo|
|l|Link simbólico(atalho)|
|d|Diretório|
|b|Arquivo de dispositivo|
|c|Arquivo de dispositivo|
|p|Canal FIFO|
|s|Socket|

tabela 1.2  
|Valor numérico|Tipo de permissão|
|:---:|:---:|
|0|---|
|1|--x|
|2|-w-|
|3|-wx|
|4|r--|
|5|r-x|
|6|rw-|
|7|rwx|

Para alterar o nível de permissão e a permissão, usamos o comando **chmod**:  
```
chmod [permissão por nível] [arquivo]
```
Exemplo:
```
[root@localhost home]# ls -l
total 4
drwxr-xr-x 2 root root 37 Mar 27 12:36 teste
[root@localhost home]# chmod 774 arquivo.txt
[root@localhost home]# ls -l
total 4
drwxrwxr-- 2 root root 37 Mar 27 12:36 arquivo.txt
```

Outra forma de utilozar o comando **chmod** é com letras ao invés de usar com numeros:
```
[root@localhost home]# ls -l
total 4
drw-rwxr-- 2 root root 37 Mar 27 12:36 arquivo.txt
[root@localhost home]# chmod u=rw,g=w,o= arquivo.txt
[root@localhost home]# ls -l
total 4
drw--w---- 2 root root 37 Mar 27 12:36 arquivo.txt
```
Ou no caso de querer dar uma permissão plena a um arquivo qualquer
```
[root@localhost home]# ls -l
total 4
drw--w---- 2 root root 37 Mar 27 12:36 arquivo.txt
[root@localhost home]# chmod +x arquivo.txt
[root@localhost home]# ls -l
total 4
drwx-wx--x 2 root root 37 Mar 27 12:36 arquivo.txt
```
Observe que todos os niveis ficaram com permissão de execussão.  
No caso de diretório, a forma de usar o **chmod** é o mesmo porém o significado das letras **rwx** muda.  
A permissão de leitura, permite que você consiga ver o arquivo dentro do diretório usando o comando **ls** mas não permite acessar o arquivo, a mesma coisa com a permissão de executar, 
A permissão de escrita permite que seja movido ou excluido  arquivo.  

Também é possivel maniputar o usuário e o grupo atravém do comando **chown**, vamos supor que o arquivo.txt que pertence ao usuário root e grupo root, (root:root) vai passar a pertencer ao usuáio sysadmin e grupo admin
```
[root@localhost teste]# ls -l
total 0
-rw-r--r-- 1 root root 0 Mar 27 13:51 arquivo.txt
[root@localhost teste]# chown sysadmin:admin arquivo.txt
[root@localhost teste]# ls -l
total 0
-rw-r--r-- 1 sysadmin admin 0 Mar 27 13:51 arquivo.txt
```
Não é possivel que qualquer um possa alterar este arquivo, apenas o usuário proprietário ou o super usuário root.  

### Comando encadeados e redirecionamento de fluxo

O Shell nos permite encadear comandos, seja ele sequencial ou condicional além de ser possível direcionar a saida do comando para outros comando ous para outros arquivos (normamente de texto).  
Para isso temos algumas opções de operadores lógicos, um deles usado para separa comandos sequenciais é o **";"**.  
```
<comando 1>;<comando 2>;<comando 3>
```
exemplo:
```
[root@localhost teste]# clear ; ifconfig
```
O comando acima vai limpar a tela e na sequencia vai mostrar a saida do comando **ifconfig**  

O encadeamento condicional podemos escolher se executa um segundo comando se o primeiro comando for executado com sucesso ou sem sucesso  
Na primeira opção, podemos usar  operador lógico **|| (OU)** 
```
[root@localhost home]# rm teste/ || echo "não foi possivel excluir o diretório"
rm: cannot remove 'teste/': Is a directory
não foi possivel excluir o diretório
```
Para seguntda opç~eo, executar o segundo comando só se o primeiro for executado com sucesso, usamos o operador lógico **&& (E)**
```
[root@localhost home]# rm -r teste/ && echo "diretório excluido"
diretório excluido
[root@localhost home]# ls
[root@localhost home]#  
```

Podemos usar a saida de um comando na entrada de um outro comando usando o caractere **| (pipe)** e ainda redirecionar esta saida par aum arquivo .txt por exemplo
```
[root@localhost home]# ps aux | grep ssh > arquivo.txt
[root@localhost home]# cat arquivo.txt
root       224  0.0  0.8   5036  1568 hvc0     S+   16:11   0:00 grep --color=auto ssh
[root@localhost home]#  
 ```
No cado como foi usado o caractere **">"** a saida sobrescreverá o conteúdo original arquivo **.txt**, se for utilizado o caractere **">>"** a saída sera anexada ao conteúdo já existente no arquivo.  
Caso seja direcionado a saída a um arquivo inexistente, o sistema cria o arquivo automaticamente.