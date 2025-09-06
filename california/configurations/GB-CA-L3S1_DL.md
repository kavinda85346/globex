#### GB-CA-L3S1_DL Device Configurations ⚙️

**Startup Configuration**
```
Switch>enable
Switch#configure terminal
Switch(config)#hostname GB-CA-L3S1_DL
```

**Vlan Configuration**
```
GB-CA-L3S1_DL(config)#vlan 50
GB-CA-L3S1_DL(config-vlan)#name management
GB-CA-L3S1_DL(config-vlan)#vlan 100
GB-CA-L3S1_DL(config-vlan)#name resources usage
GB-CA-L3S1_DL(config-vlan)#vlan 150
GB-CA-L3S1_DL(config-vlan)#name voice
GB-CA-L3S1_DL(config-vlan)#vlan 96
GB-CA-L3S1_DL(config-vlan)#name security
GB-CA-L3S1_DL(config-vlan)#vlan 128
GB-CA-L3S1_DL(config-vlan)#name it
GB-CA-L3S1_DL(config-vlan)#vlan 160
GB-CA-L3S1_DL(config-vlan)#name finance
GB-CA-L3S1_DL(config-vlan)#vlan 176
GB-CA-L3S1_DL(config-vlan)#name hr
GB-CA-L3S1_DL(config-vlan)#vlan 200
GB-CA-L3S1_DL(config-vlan)#name native
```

**Switchports VLAN Assignment**
```
GB-CA-L3S1_DL(config)#interface fastEthernet 0/1
GB-CA-L3S1_DL(config-if)#switchport mode access
GB-CA-L3S1_DL(config-if)#switchport access vlan 8
GB-CA-L3S1_DL(config-if)#exit
GB-CA-L3S1_DL(config)#interface fastEthernet 0/2
GB-CA-L3S1_DL(config-if)#switchport mode access
GB-CA-L3S1_DL(config-if)#switchport access vlan 16
GB-CA-L3S1_DL(config-if)#exit
GB-CA-L3S1_DL(config)#interface fastEthernet 0/3
GB-CA-L3S1_DL(config-if)#switchport mode access
GB-CA-L3S1_DL(config-if)#switchport access vlan 24
GB-CA-L3S1_DL(config-if)#exit
GB-CA-L3S1_DL(config)#interface fastEthernet 0/4
GB-CA-L3S1_DL(config-if)#switchport mode access
GB-CA-L3S1_DL(config-if)#switchport access vlan 32
GB-CA-L3S1_DL(config-if)#exit
GB-CA-L3S1_DL(config)#interface fastEthernet 0/5
GB-CA-L3S1_DL(config-if)#switchport mode access
GB-CA-L3S1_DL(config-if)#switchport access vlan 36
GB-CA-L3S1_DL(config)#interface range fastEthernet 0/6-24
GB-CA-L3S1_DL(config-if)#switchport mode access
GB-CA-L3S1_DL(config-if)#switchport access vlan 40
```

**Trunk Configuration**
```
GB-CA-L3S1_DL(config)#interface range gigabitEthernet 1/0/21-22
GB-CA-L3S1_DL(config-if-range)#switchport mode trunk
GB-CA-L3S1_DL(config-if-range)#switchport trunk native vlan 200
GB-CA-L3S1_DL(config-if-range)#switchport trunk allowed vlan 50-200
GB-CA-L3S1_DL(config-if-range)#switchport nonegotiate
GB-CA-L3S1_DL(config-if-range)#channel-group 4 mode passive
GB-CA-L3S1_DL(config-if-range)#exit
GB-CA-L3S1_DL(config)#interface range gigabitEthernet 1/0/19-20
GB-CA-L3S1_DL(config-if-range)#switchport mode trunk
GB-CA-L3S1_DL(config-if-range)#switchport trunk native vlan 200
GB-CA-L3S1_DL(config-if-range)#switchport trunk allowed vlan 50-200
GB-CA-L3S1_DL(config-if-range)#switchport nonegotiate
GB-CA-L3S1_DL(config-if-range)#channel-group 5 mode active
GB-CA-L3S1_DL(config-if-range)#exit
GB-CA-L3S1_DL(config)#interface range gigabitEthernet 1/0/23-24
GB-CA-L3S1_DL(config-if-range)#switchport mode trunk
GB-CA-L3S1_DL(config-if-range)#switchport trunk native vlan 200
GB-CA-L3S1_DL(config-if-range)#switchport trunk allowed vlan 50-200
GB-CA-L3S1_DL(config-if-range)#switchport nonegotiate
GB-CA-L3S1_DL(config-if-range)#channel-group 2 mode passive
GB-CA-L3S1_DL(config-if-range)#exit
GB-CA-L3S1_DL(config)#interface gigabitEthernet 1/1/1
GB-CA-L3S1_DL(config-if)#switchport mode trunk
GB-CA-L3S1_DL(config-if)#switchport trunk native vlan 200
GB-CA-L3S1_DL(config-if)#switchport trunk allowed vlan 50-200
GB-CA-L3S1_DL(config-if)#switchport nonegotiate
```

**Port Channel Configuration**
```
GB-CA-L3S1_DL(config)#interface port-channel 4
GB-CA-L3S1_DL(config-if)#switchport mode trunk
GB-CA-L3S1_DL(config-if)#switchport trunk native vlan 200
GB-CA-L3S1_DL(config-if)#switchport trunk allowed vlan 50-200
GB-CA-L3S1_DL(config-if)#switchport nonegotiate
GB-CA-L3S1_DL(config-if)#exit
GB-CA-L3S1_DL(config)#interface port-channel 5
GB-CA-L3S1_DL(config-if)#switchport mode trunk
GB-CA-L3S1_DL(config-if)#switchport trunk native vlan 200
GB-CA-L3S1_DL(config-if)#switchport trunk allowed vlan 50-200
GB-CA-L3S1_DL(config-if)#switchport nonegotiate
GB-CA-L3S1_DL(config-if)#exit
GB-CA-L3S1_DL(config)#interface port-channel 2
GB-CA-L3S1_DL(config-if)#switchport mode trunk
GB-CA-L3S1_DL(config-if)#switchport trunk native vlan 200
GB-CA-L3S1_DL(config-if)#switchport trunk allowed vlan 50-200
GB-CA-L3S1_DL(config-if)#switchport nonegotiate
GB-CA-L3S1_DL(config-if)#exit
```

**Inter-VLAN Routing Configuration**
```
GB-CA-L3S1_DL(config)#ip routing
GB-CA-L3S1_DL(config)#interface vlan 50
GB-CA-L3S1_DL(config-if)#description management vlan interface
GB-CA-L3S1_DL(config-if)#ip address 10.5.2.29 255.255.255.224
GB-CA-L3S1_DL(config-if)#no shutdown
GB-CA-L3S1_DL(config-if)#exit
GB-CA-L3S1_DL(config)#interface vlan 100
GB-CA-L3S1_DL(config-if)#description usage vlan interface
GB-CA-L3S1_DL(config-if)#ip address 10.5.2.61 255.255.255.224
GB-CA-L3S1_DL(config-if)#no shutdown
GB-CA-L3S1_DL(config-if)#exit
GB-CA-L3S1_DL(config)#interface vlan 150
GB-CA-L3S1_DL(config-if)#description voice vlan interface
GB-CA-L3S1_DL(config-if)#ip address 10.5.2.93 255.255.255.224
GB-CA-L3S1_DL(config-if)#no shutdown
GB-CA-L3S1_DL(config-if)#exit
GB-CA-L3S1_DL(config)#interface vlan 96
GB-CA-L3S1_DL(config-if)#description security vlan interface
GB-CA-L3S1_DL(config-if)#ip address 10.5.2.125 255.255.255.224
GB-CA-L3S1_DL(config-if)#no shutdown
GB-CA-L3S1_DL(config-if)#exit
GB-CA-L3S1_DL(config)#interface vlan 128
GB-CA-L3S1_DL(config-if)#description it vlan interface
GB-CA-L3S1_DL(config-if)#ip address 10.5.2.157 255.255.255.224
GB-CA-L3S1_DL(config-if)#no shutdown
GB-CA-L3S1_DL(config-if)#exit
GB-CA-L3S1_DL(config)#interface vlan 160
GB-CA-L3S1_DL(config-if)#description finance vlan interface
GB-CA-L3S1_DL(config-if)#ip address 10.5.2.173 255.255.255.240
GB-CA-L3S1_DL(config-if)#no shutdown
GB-CA-L3S1_DL(config-if)#exit
GB-CA-L3S1_DL(config)#interface vlan 176
GB-CA-L3S1_DL(config-if)#description hr vlan interface
GB-CA-L3S1_DL(config-if)#ip address 10.5.2.189 255.255.255.240
GB-CA-L3S1_DL(config-if)#no shutdown
GB-CA-L3S1_DL(config-if)#exit
GB-CA-L3S1_DL(config)#interface vlan 200
GB-CA-L3S1_DL(config-if)#description native vlan interface
GB-CA-L3S1_DL(config-if)#ip address 10.5.2.205 255.255.255.240
GB-CA-L3S1_DL(config-if)#no shutdown
```

**STP Configuration**
```
GB-CA-L3S1_DL(config)#spanning-tree mode pvst
```









