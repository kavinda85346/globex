#### GB-NY-R_CCL Device Configurations ⚙️

**Startup Configuration**
```
Router>enable
Router#configure terminal
Router(config)#hostname GB-NY-R_CCL
GB-NY-R_CCL(config)#interface gigabitEthernet 1/0
GB-NY-R_CCL(config-if)#ip address 200.100.50.17 255.255.255.248
GB-NY-R_CCL(config-if)#no shutdown
GB-NY-R_CCL(config-if)#interface gigabitEthernet 0/0
GB-NY-R_CCL(config-if)#ip address 200.100.50.10 255.255.255.252
GB-NY-R_CCL(config-if)#no shutdown
```

**OSPF Configuration**
```
GB-NY-R_CCL(config)#router ospf 1
GB-NY-R_CCL(config-router)#router-id 3.3.3.3
GB-NY-R_CCL(config-router)#network 200.100.50.8 0.0.0.7 area 1
GB-NY-R_CCL(config-router)#network 200.100.50.16 0.0.0.7 area 2
GB-NY-R_CCL(config-router)#passive-interface g 2/0
GB-NY-R_CCL(config-router)#passive-interface g 3/0
GB-NY-R_CCL(config-router)#exit
GB-NY-R_CCL(config)#interface gigabitEthernet 0/0
GB-NY-R_CCL(config)#ip ospf 1 area 1
GB-NY-R_CCL(config)#interface gigabitEthernet 1/0
GB-NY-R_CCL(config)#ip ospf 1 area 2
```

**HSRP Configuration**
```
GB-NY-R_CCL(config)#interface gigabitEthernet 0/0
GB-NY-R_CCL(config-if)#standby 2 ip 200.100.50.11
GB-NY-R_CCL(config-if)#standby 2 priority 100
GB-NY-R_CCL(config-if)#standby 2 preempt
GB-NY-R_CCL(config-if)#exit
GB-NY-R_CCL(config)#interface gigabitEthernet 1/0
GB-NY-R_CCL(config-if)#standby 3 ip 200.100.50.19
GB-NY-R_CCL(config-if)#standby 3 priority 100
GB-NY-R_CCL(config-if)#standby 3 preempt
```

**Subinterface Configuration**
```
GB-NY-R_CCL(config)#interface gigabitEthernet 2/0.50
GB-NY-R_CCL(config-subif)#ip address 172.16.8.30 255.255.255.224
GB-NY-R_CCL(config-subif)#encapsulation dot1Q 50
GB-NY-R_CCL(config-subif)#description management vlan interface
GB-NY-R_CCL(config-subif)#interface gigabitEthernet 2/0.100
GB-NY-R_CCL(config-subif)#encapsulation dot1Q 100
GB-NY-R_CCL(config-subif)#ip address 172.16.8.62 255.255.255.224
GB-NY-R_CCL(config-subif)#description usage vlan interface
GB-NY-R_CCL(config-subif)#interface gigabitEthernet 2/0.150
GB-NY-R_CCL(config-subif)#encapsulation dot1Q 150
GB-NY-R_CCL(config-subif)#ip address 172.16.8.94 255.255.255.224
GB-NY-R_CCL(config-subif)#description voice vlan interface
GB-NY-R_CCL(config-subif)#interface gigabitEthernet 2/0.96
GB-NY-R_CCL(config-subif)#encapsulation dot1Q 96
GB-NY-R_CCL(config-subif)#ip address 172.16.8.126 255.255.255.224
GB-NY-R_CCL(config-subif)#description security vlan interface
GB-NY-R_CCL(config-subif)#exit
GB-NY-R_CCL(config)#interface gigabitEthernet 3/0.128
GB-NY-R_CCL(config-subif)#encapsulation dot1Q 128
GB-NY-R_CCL(config-subif)#ip address 172.16.8.158 255.255.255.224
GB-NY-R_CCL(config-subif)#description it vlan interface
GB-NY-R_CCL(config-subif)#interface gigabitEthernet 3/0.160
GB-NY-R_CCL(config-subif)#encapsulation dot1Q 160
GB-NY-R_CCL(config-subif)#ip address 172.16.8.174 255.255.255.240
GB-NY-R_CCL(config-subif)#description finance vlan interface
GB-NY-R_CCL(config-subif)#interface gigabitEthernet 3/0.176
GB-NY-R_CCL(config-subif)#encapsulation dot1Q 176
GB-NY-R_CCL(config-subif)#ip address 172.16.8.190 255.255.255.240
GB-NY-R_CCL(config-subif)#description hr vlan interface
GB-NY-R_CCL(config-subif)#interface gigabitEthernet 3/0.200
GB-NY-R_CCL(config-subif)#encapsulation dot1Q 200 native
GB-NY-R_CCL(config-subif)#ip address 172.16.8.206 255.255.255.240
GB-NY-R_CCL(config-subif)#description native vlan interface
GB-NY-R_CCL(config-subif)#exit
GB-NY-R_CCL(config)#interface gigabitEthernet 2/0
GB-NY-R_CCL(config-if)#no shutdown
GB-NY-R_CCL(config-if)#exit
GB-NY-R_CCL(config)#interface gigabitEthernet 3/0
GB-NY-R_CCL(config-if)#no shutdown
GB-NY-R_CCL(config-if)#exit
```

**DHCP Pool Configuration**
```
GB-NY-R_CCL(config)#ip dhcp excluded-address 172.16.8.28 172.16.8.30
GB-NY-R_CCL(config)#ip dhcp excluded-address 172.16.8.60 172.16.8.62
GB-NY-R_CCL(config)#ip dhcp excluded-address 172.16.8.92 172.16.8.94
GB-NY-R_CCL(config)#ip dhcp excluded-address 172.16.8.124 172.16.8.126
GB-NY-R_CCL(config)#ip dhcp excluded-address 172.16.8.156 172.16.8.158
GB-NY-R_CCL(config)#ip dhcp excluded-address 172.16.8.172 172.16.8.174
GB-NY-R_CCL(config)#ip dhcp excluded-address 172.16.8.188 172.16.8.190
GB-NY-R_CCL(config)#ip dhcp excluded-address 172.16.8.204 172.16.8.206
GB-NY-R_CCL(config)#ip dhcp pool management
GB-NY-R_CCL(dhcp-config)#network 172.16.8.0 255.255.255.224
GB-NY-R_CCL(dhcp-config)#default-router 172.16.8.30
GB-NY-R_CCL(dhcp-config)#ip dhcp pool usage
GB-NY-R_CCL(dhcp-config)#network 172.16.8.32 255.255.255.224
GB-NY-R_CCL(dhcp-config)#default-router 172.16.8.62
GB-NY-R_CCL(dhcp-config)#ip dhcp pool voice
GB-NY-R_CCL(dhcp-config)#network 172.16.8.64 255.255.255.224
GB-NY-R_CCL(dhcp-config)#default-router 172.16.8.94
GB-NY-R_CCL(dhcp-config)#ip dhcp pool security
GB-NY-R_CCL(dhcp-config)#network 172.16.8.96 255.255.255.224
GB-NY-R_CCL(dhcp-config)#default-router 172.16.8.126
GB-NY-R_CCL(dhcp-config)#ip dhcp pool it
GB-NY-R_CCL(dhcp-config)#network 172.16.8.128 255.255.255.224
GB-NY-R_CCL(dhcp-config)#default-router 172.16.8.158
GB-NY-R_CCL(dhcp-config)#ip dhcp pool finance
GB-NY-R_CCL(dhcp-config)#network 172.16.8.160 255.255.255.240
GB-NY-R_CCL(dhcp-config)#default-router 172.16.8.174
GB-NY-R_CCL(dhcp-config)#ip dhcp pool hr
GB-NY-R_CCL(dhcp-config)#network 172.16.8.176 255.255.255.240
GB-NY-R_CCL(dhcp-config)#default-router 172.16.8.190
GB-NY-R_CCL(dhcp-config)#ip dhcp pool native
GB-NY-R_CCL(dhcp-config)#network 172.16.8.192 255.255.255.240
GB-NY-R_CCL(dhcp-config)#default-router 172.16.8.206
```





