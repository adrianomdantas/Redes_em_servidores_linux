[HOME](/README.md/)/[Proximo](EmConstrução.md)

# Configuração e administração de redes


O sistema Linux foi criado pensando em conectividade TCP/IP, e tem excelentes ferramentas que todo _sysadmin_ deve conhecer com profundidade.

### Ferramentas da linha de comando

As ferramentas do pacote **net-tools** não são atualizadas desde 2001, porém são ainda amplamente utilizadas por administradores, atualmente é recomendada a utilização do pacote **iproute2** que além de integrar a maior parte das funções de rede em apenas uma ferramenta denominada **ip** é mais moderna e tem oferecer suporte a novos recursos como o **IPv6**.  

- Na tabela abaixo estão organizados os exemplos que estão demonstrados nos terminais a seguir a tabela

|Terminal|Pacote|Descrição|
|:---:|---|:---|
|1|iproute2|Comandos relacionado ao link (layer 2)|
|2|iproute2|Comandos relacionado ao endereço IPv4 e roteamento IPv4|
|3|iproute2|Comandos relacionado ao endereço IPv6 e roteamente IPv6|
|4|net-tools|Comandos relacionado ao endereço IPv4|
|5|net-tools|Comandos relacionado ao endereço IPv6|
|6|net-tools|Comandos relacionado ao roteamente em IPv4|
|7|net-tools|Comandos relacionado ao roteamenteo em IPv6|
|8|net-tools|Comandos relacionado ao ARP|
|9|sistema|Comandos relacionado ao ao hostname|

O comando **ip** do pacote iproute é poderoso e suas opções substituem o que era feito em diversas ferramentas do legado net-tools.

- **Terminal 1 - Comandos relacionados ao link (iproute2)**
```
01 - [root@localhost ~]# ip link show
02 - [root@localhost ~]# ip link set dev eth0 down
30 - [root@localhost ~]# ip link set dev eth0 up

# Descrição
# 01 - Exibir informações de conectividade da interface
# 02 - desabilitar a interface eth0
# 03 - Habilitar a interface eth0
```

- **Terminal 2 - Comandos relacionados ao endereçamento/rooteamento IPv4 (iproute2)** 
```
01 - [root@localhost ~]# ip address show
02 - [root@localhost ~]# ip address add 192.168.0.1/24 dev eth0
03 - [root@localhost ~]# ip address del 192.0.1/24 dev eth0
04 - [root@localhost ~]# ip neighbor show
05 - [root@localhost ~]# ip route add 0.0.0.0/0 via 10.100.1.2
06 - [root@localhost ~]# ip route del 0.0.0.0/0 via 10.100.1.2

# Descrição
# 01 - Exibir configurações de IPv4 nas interfaces
# 02 - Configurar o endereço IPv4 na interface eth0
# 03 - Remover o endereço IPv4 na interface eth0
# 04 - Exibir a tabela de vizinhança (ARP)
# 05 - Inserir a rede 0.0.0.0/0 via gateway 10.100.1.2
# 06 - Remover a rede 0.0.0.0/0 via gateway 10.100.1.2
```

- **Terminal 3 - Comandos relacionados ao endereço/roteamento IPv6 (iproute2)**
```
01 - [root@localhost ~]# ip -6 address show
02 - [root@localhost ~]# ip -6 address add 2001:db8:cafe::1/64 dev eth0
03 - [root@localhost ~]# ip -6 address del 2001:db8:cafe::1/64 dev eth0
04 - [root@localhost ~]# ip -6 neighbor show
05 - [root@localhost ~]# ip -6 route add ::/0 via 2001:db8:cafe::f
06 - [root@localhost ~]# ip -6 route del ::/0 via 2001:db8:cafe::f

# Descrição
# 01 - Exibe as configurações IPv6 nas interfaces
# 02 - Configurar o IPv6 na interface eth0
# 03 - Remover o endereço IPv6 na interface eth0
# 04 - Exibir a tabela de vizinhança (NDP)
# 05 - Inserir a rede ::/0 via gateway 2001:db8:cafe::f
# 06 - Remover a rede ::/0 via gateway 2001:db8:cafe::f
```

- **Terminal 4 - Comandos relacionados ao endereço IPv4 (net-tools)**
```
01 - [root@localhost ~]# ifconfig eth0
02 - [root@localhost ~]# ifconfig eth0 up
03 - [root@localhost ~]# ifconfig eth1 down
04 - [root@localhost ~]# ifconfig eth0 192.168.0.1/24
05 - [root@localhost ~]# ifconfig eth0 192.168.0.1 netmask 255.255.255.0
06 - [root@localhost ~]# ifconfig eth0 0.0.0.0/32

# Descrição
# 01 - Exibir configurações da interface eth0
# 02 - Habilitar a interface eth0
# 03 - Desabilitar a interface eth1
# 04 - Configurar endereço IPv4 na interface eth0
# 05 - Configurar endereço IPv4 na interface eth0
# 06 - Remover endereço IPv4 na interface eth0 (mensagem de erro)
```

- **Terminal 5 - Comandos relacionados ao endereço IPv6 (net-tools)
```
01 - [root@localhost ~]# ifconfig eth0
02 - [root@localhost ~]# ifconfig eth0 up
03 - [root@localhost ~]# ifconfig eth1 down
04 - [root@localhost ~]# ifconfig eth0 inet6 add 2001:db9:cafe::1/64
05 - [root@localhost ~]# ifconfig eth0 inet6 del 2001:db9:cafe::1/64

# Descrição
# 01 - Exibir configurações da interface eth0
# 02 - Habilitar a interface eth0
# 03 - Desabilitar interface eth1
# 04 - Configurar endereço IPv6 na interface eth0
# 05 - Remover endereço IPv6 na interface eth0
```

- **Terminal 6 - Comandos relacionados ao roteamento em IPv4 (net-tools)**
```
01 - [root@localhost ~]# route -n
02 - [root@localhost ~]# route add default gateway 192.168.0.254
03 - [root@localhost ~]# route del default gateway 192.168.0.254
04 - [root@localhost ~]# route add -net 10.0.0.0/8 gw 192.168.0.254
05 - [root@localhost ~]# route del -net 10.0.0.0/8 gw 192.168.0.254

# Descrição
# 01 - Exibir a tabela de roteamento
# 02 - Inserir o gateway 192.169.0.254
# 03 - Remover o gateway 192.169.0.254
# 04 - Inserir a rede 10.0.0.0/8 via gatewway 192.168.0.254
# 05 - Remover a rede 10.0.0.0/8 via gatewway 192.168.0.254
```

- **Terminal 7 - Comandos relacionados ao roteamento IPv6 (net-tools)**
```
01 - [root@localhost ~]# route -6 -n
02 - [root@localhost ~]# route -6 add default gateway 2001:db8::f
03 - [root@localhost ~]# route -6 del default gateway 2001:db8::f
04 - [root@localhost ~]# route -6 add 2001:db8:cafe::/64 gw 2001:db8::f
05 - [root@localhost ~]# route -6 del 2001:db8:cafe::/64 gw 2001:db8::f

# Descrição
# 01 - Exibir a tabela de roteamento
# 02 - Inserir o gateway 2001:db8::f
# 03 - Remover o gateway 2001:db8::f
# 04 - Inserir a rede 2001:db8:cafe::/64 via gateway 2001:db8::f 
# 05 - Remover a rede 2001:db8:cafe::/64 via gateway 2001:db8::f 
```
O comando **arp** do pacor net-tools foi subistituido pelo comando  **show neighbor show** do pacote iproute2, segue algumas opções para o comando **arp**

|Opção|Descrição|
|:---:|---|
|-e|Para exibir os mapeamentos|
|-d|Para remover manualmente uma entrada aprendida automaticamente|
|-s|Para inserir manualmente uma entrada|

- **Terminal 8 - Comandos relacionados ao ARP (net-tools)**
```
[root@localhost ~]# arp -e
Address        HWtype    HWaddress          Flags   Mask   Iface
192.168.7.254  ether     20:11:4v:31:5f:f7  C              wlan0

[root@localhost ~]# arp -d 192.168.7.254
[root@localhost ~]# arp -s 192.168.7.200 aa:aa:aa:aa:aa:aa 

[root@localhost ~]# arp -n
Address        HWtype    HWaddress          Flags   Mask   Iface
192.168.7.200  ether     aa:aa:aa:aa:aa:aa  CM             wlan0
192.168.7..254 ether     (incomplete)                      wlan0 
``` 

O comando hostname permite verificar o nome atual do servidor de rede

- **Terminal 9 - Comandos elacionados ao nome do host**
```
[root@localhost ~]# hostname
localhost

[root@localhost ~]# hostname Adriano
[root@localhost ~]# hostname
Adriano

# ao abrir uma nova sessão o prompt irá mudar

[root@Adriano ~]# 
```

As configurações feitas diretamente por linha de comando são volateis e ao reiniciar o servidor, serão perdidas, porém dá para deixar estas configurações volateis automáticas, por exemplo, por intermédio dos serviços **rc-local.service** e **cron.service**.


### Script de inicialização

