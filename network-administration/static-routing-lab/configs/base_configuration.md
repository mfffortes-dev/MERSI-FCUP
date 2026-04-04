## RLin (Linux Router)
### ip configuration
    - ip addr add 170.2.0.3/16 dev eth0
    - ip addr add 192.180.40.3/24 dev eth1
    - ip addr add 192.180.30.3/24 dev eth2

    - ip link set eth0 up
    - ip link set eth1 up
    - ip link set eth2 up

- enabled forwarding
    - echo 1 > /proc/sys/net/ipv4/ip_forward

OR

### ip configuration
- auto lo
- iface lo inet loopback

- auto eth0
- iface eth0 inet static
        - address 170.2.0.3
        - netmask 255.255.0.0

- auto eth1
- iface eth1 inet static
        - address 192.180.40.3
        - netmask 255.255.255.0

- auto eth2
- iface eth2 inet static
        - address 192.180.30.3
        - netmask 255.255.255.0



## Term1
### ip configuration
- ip addr add 170.2.0.33/16 dev eth1
- ip link set eth1 up

- verifiry command
    - ip route

### route configuration
- ip route add default via 170.2.0.3
- ip route add 192.180.40.0/24 via 170.2.0.1

OR 
### ip configuration
- vi /etc/network/interfaces
    - auto lo
    - iface lo inet loopback

    - auto eth1
    - iface eth1 inet static
        - address 170.2.0.33
        - netmask 255.255.0.0
        - gateway 170.2.0.3
        
### route configuration
up ip route add 192.180.40.0/24 via 170.2.0.1



## Term2
### ip configuration
- ip addr add 192.180.40.44/24 dev eth0
- ip addr add 192.180.30.44/24 dev eth1

- ip link set eth0 up
- ip link set eth1 up

- disable forwarding
    - echo 0 > /proc/sys/net/ipv4/ip_forward

 ### route configuration
- ip route add default via 192.180.40.2


OR
### ip configuration/ permanente
- auto lo
- iface lo inet loopback

- auto eth0
- iface eth0 inet static
   - address 192.180.40.44
   - netmask 255.255.255.0
   - gateway 192.180.40.2

- auto eth1
- iface eth1 inet static
   - address 192.180.30.44
   - netmask 255.255.255.0

- ifdown eth0 eth1
- ifup eth0 eth1

### command verification
- traceroute -n -q 1 170.2.0.33


## RCis1 (Cisco Router)
- enable
- configure terminal

- interface f2/0
    - ip address 170.2.0.1 255.255.0.0
    - no shutdown

- interface f0/0
    - ip address 195.70.40.25 255.255.255.252
    - no shutdown

- end

### route configuration
- configure terminal
- ip route 192.180.40.0 255.255.255.0 195.70.40.26



## RCis2 (Cisco Router)
- enable
- configure terminal

- interface f2/0
    - ip address 192.180.40.2 255.255.255.0
    - no shutdown

- interface f0/0
    - ip address 195.70.40.26 255.255.255.252
    - no shutdown

end

### route configuration
- configure terminal
- ip route 170.2.0.0 255.255.0.0 195.70.40.25




