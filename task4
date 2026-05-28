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
