# HQ-RTR
# /etc/net/ifaces/br0/options
TYPE=ovsbr
HOST=ens19
BOOTPROTO=static


# HQ-RTR
# /etc/net/ifaces/vlan100/options
TYPE=ovsport
BRIDGE=br0
VID=100
BOOTPROTO=static
CONFIG_IPV4=yes

# HQ-RTR
# /etc/net/ifaces/vlan100/ipv4address
192.168.100.1/28

ovs-vsctl show

# HQ-SRV
# /etc/net/ifaces/ens18.100/options
BOOTPROTO=static
TYPE=vlan
VID=100
HOST=ens18
CONFIG_IPV4=yes
DISABLED=no



ip-tun
# HQ-RTR
# /etc/net/ifaces/GRE1/options
TYPE=iptun
TUNTYPE=gre
TUNLOCAL=172.16.1.2
TUNREMOTE=172.16.2.2
TUNTTL=64
TUNOPTIONS='ttl 64'

# HQ-RTR
# /etc/net/ifaces/GRE1/ipv4address
10.0.0.1/30

Аналогично создаём конфигурацию GRE-интерфейса на BR-RTR, зеркально поменяв адреса TUNLOCAL и TUNREMOTE.

apt-get update && apt-get install openssh-server

Все дальнейшие изменения производятся в конфигурационном файле /etc/openssh/sshd_config на хостах HQ-SRV и BR-SRV.
port раскоментить + знач.
# HQ-SRV / BR-SRV
# /etc/openssh/sshd_config (в конец файла)
AllowUsers sshuser

MaxAuthTries 2
Banner /etc/openssh/banner 
echo "Authorized access only" > /etc/openssh/banner
systemctl restart sshd

ssh -p 2026 sshuser@192.168.100.2
