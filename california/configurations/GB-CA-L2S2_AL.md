#### GB-CA-L2S2_AL Device Configurations ⚙️

**Startup Configuration**
```
Switch>enable
Switch#configure terminal
Switch(config)#hostname GB-CA-L2S2_AL
```

**Vlan Configuration**
```
GB-CA-L2S2_AL(config)#vlan 50
GB-CA-L2S2_AL(config-vlan)#name management
GB-CA-L2S2_AL(config-vlan)#vlan 100
GB-CA-L2S2_AL(config-vlan)#name resources usage
GB-CA-L2S2_AL(config-vlan)#vlan 150
GB-CA-L2S2_AL(config-vlan)#name voice
GB-CA-L2S2_AL(config-vlan)#vlan 96
GB-CA-L2S2_AL(config-vlan)#name security
GB-CA-L2S2_AL(config-vlan)#vlan 128
GB-CA-L2S2_AL(config-vlan)#name it
GB-CA-L2S2_AL(config-vlan)#vlan 160
GB-CA-L2S2_AL(config-vlan)#name finance
GB-CA-L2S2_AL(config-vlan)#vlan 176
GB-CA-L2S2_AL(config-vlan)#name hr
GB-CA-L2S2_AL(config-vlan)#vlan 200
GB-CA-L2S2_AL(config-vlan)#name native
```

**Trunk Configuration**
```
GB-CA-L2S2_AL(config)#interface range fastEthernet 0/23-24
GB-CA-L2S2_AL(config-if-range)#switchport mode trunk
GB-CA-L2S2_AL(config-if-range)#switchport trunk native vlan 200
GB-CA-L2S2_AL(config-if-range)#switchport trunk allowed vlan 50-200
GB-CA-L2S2_AL(config-if-range)#switchport nonegotiate
GB-CA-L2S2_AL(config-if-range)#channel-group 1 mode passive
GB-CA-L2S2_AL(config-if-range)#exit
GB-CA-L2S2_AL(config)#interface range fastEthernet 0/21-22
GB-CA-L2S2_AL(config-if-range)#switchport mode trunk
GB-CA-L2S2_AL(config-if-range)#switchport trunk native vlan 200
GB-CA-L2S2_AL(config-if-range)#switchport trunk allowed vlan 50-200
GB-CA-L2S2_AL(config-if-range)#switchport nonegotiate
GB-CA-L2S2_AL(config-if-range)#channel-group 2 mode active
GB-CA-L2S2_AL(config-if-range)#exit
GB-CA-L2S2_AL(config)#interface range gigabitEthernet 0/1-2
GB-CA-L2S2_AL(config-if-range)#switchport mode trunk
GB-CA-L2S2_AL(config-if-range)#switchport trunk native vlan 200
GB-CA-L2S2_AL(config-if-range)#switchport trunk allowed vlan 50-200
GB-CA-L2S2_AL(config-if-range)#switchport nonegotiate
GB-CA-L2S2_AL(config-if-range)#channel-group 5 mode active
GB-CA-L2S2_AL(config-if-range)#exit
```

**Port Channel Creation**
```
GB-CA-L2S2_AL(config)#interface port-channel 1
GB-CA-L2S2_AL(config-if)#switchport mode trunk
GB-CA-L2S2_AL(config-if)#switchport trunk native vlan 200
GB-CA-L2S2_AL(config-if)#switchport trunk allowed vlan 50-200
GB-CA-L2S2_AL(config-if)#switchport nonegotiate
GB-CA-L2S2_AL(config-if)#exit
GB-CA-L2S2_AL(config)#interface port-channel 2
GB-CA-L2S2_AL(config-if)#switchport mode trunk
GB-CA-L2S2_AL(config-if)#switchport trunk native vlan 200
GB-CA-L2S2_AL(config-if)#switchport trunk allowed vlan 50-200
GB-CA-L2S2_AL(config-if)#switchport nonegotiate
GB-CA-L2S2_AL(config-if)#exit
GB-CA-L2S2_AL(config)#interface port-channel 5
GB-CA-L2S2_AL(config-if)#switchport mode trunk
GB-CA-L2S2_AL(config-if)#switchport trunk native vlan 200
GB-CA-L2S2_AL(config-if)#switchport trunk allowed vlan 50-200
GB-CA-L2S2_AL(config-if)#switchport nonegotiate
```

**Assinging VLANs for Switchports**
```
GB-CA-L2S2_AL(config)#interface fastEthernet 0/1
GB-CA-L2S2_AL(config-if)#switchport mode access
GB-CA-L2S2_AL(config-if)#switchport access vlan 100
GB-CA-L2S2_AL(config-if)#exit
GB-CA-L2S2_AL(config)#interface fastEthernet 0/2
GB-CA-L2S2_AL(config-if)#switchport mode access
GB-CA-L2S2_AL(config-if)#switchport access vlan 128
GB-CA-L2S2_AL(config-if)#exit
GB-CA-L2S2_AL(config)#interface range fastEthernet 0/3-20
GB-CA-L2S2_AL(config-if-range)#switchport mode access
GB-CA-L2S2_AL(config-if-range)#switchport access vlan 200
```

**VLAN Interface Configuration**
```
GB-CA-L2S2_AL(config)#interface vlan 50
GB-CA-L2S2_AL(config-if)#description management vlan interface
GB-CA-L2S2_AL(config-if)#ip address 10.5.2.26 255.255.255.224
GB-CA-L2S2_AL(config-if)#no shutdown
GB-CA-L2S2_AL(config-if)#exit
GB-CA-L2S2_AL(config)#interface vlan 100
GB-CA-L2S2_AL(config-if)#description usage vlan interface
GB-CA-L2S2_AL(config-if)#ip address 10.5.2.58 255.255.255.224
GB-CA-L2S2_AL(config-if)#no shutdown
GB-CA-L2S2_AL(config-if)#exit
GB-CA-L2S2_AL(config)#interface vlan 150
GB-CA-L2S2_AL(config-if)#description voice vlan interface
GB-CA-L2S2_AL(config-if)#ip address 10.5.2.90 255.255.255.224
GB-CA-L2S2_AL(config-if)#no shutdown
GB-CA-L2S2_AL(config-if)#exit
GB-CA-L2S2_AL(config)#interface vlan 96
GB-CA-L2S2_AL(config-if)#description security vlan interface
GB-CA-L2S2_AL(config-if)#ip address 10.5.2.122 255.255.255.224
GB-CA-L2S2_AL(config-if)#no shutdown
GB-CA-L2S2_AL(config-if)#exit
GB-CA-L2S2_AL(config)#interface vlan 128
GB-CA-L2S2_AL(config-if)#description it vlan interface
GB-CA-L2S2_AL(config-if)#ip address 10.5.2.154 255.255.255.224
GB-CA-L2S2_AL(config-if)#no shutdown
GB-CA-L2S2_AL(config-if)#exit
GB-CA-L2S2_AL(config)#interface vlan 160
GB-CA-L2S2_AL(config-if)#description finance vlan interface
GB-CA-L2S2_AL(config-if)#ip address 10.5.2.170 255.255.255.240
GB-CA-L2S2_AL(config-if)#no shutdown
GB-CA-L2S2_AL(config-if)#exit
GB-CA-L2S2_AL(config)#interface vlan 176
GB-CA-L2S2_AL(config-if)#description hr vlan interface
GB-CA-L2S2_AL(config-if)#ip address 10.5.2.186 255.255.255.240
GB-CA-L2S2_AL(config-if)#no shutdown
GB-CA-L2S2_AL(config-if)#exit
GB-CA-L2S2_AL(config)#interface vlan 200
GB-CA-L2S2_AL(config-if)#description native vlan interface
GB-CA-L2S2_AL(config-if)#ip address 10.5.2.202 255.255.255.240
GB-CA-L2S2_AL(config-if)#no shutdown
```

**STP Configuration**
```
GB-CA-L2S2_AL(config)#spanning-tree mode pvst
GB-CA-L2S2_AL(config)#interface range fastEthernet 0/1-2
GB-CA-L2S2_AL(config-if-range)#spanning-tree portfast
GB-CA-L2S2_AL(config-if-range)#spanning-tree bpduguard enable
```












