# Router

### Enter Privileged EXEC Mode:
```
Router> enable
```

### Enter Global Configuration Mode:
```

Router# configure terminal
```

### Configure the device name:
(SSH requires the router to have a hostname)
```
Router(config)# hostname [MyRouter]
```

### Secure user EXEC mode:
```
Router(config)#line console 0

Router(config-line)#password [password]

Router(config-line)#login
```

### Secure remote Telnet / SSH access:
```
Router(config-line)#line vty 0 4

Router(config-line)#password [password]

Router(config-line)#login

Router(config-line)#transport input {ssh |telnet}
```

### Secure all passwords in the config file:
```
Router(config-line)#exit

Router(config)#service password-encryption
```

### Message of the day / legal notification:
("#" Is to start and and the message)
```
Router(config)#banner motd # [message] # 
```

### Configure Router Interfaces:
```
Router(config)#interface [type-and-number]

Router(config-if)#description [description-text]

Router(config-if)#ip address [ipv4-address subnet-mask]

Router(config-if)#ipv6 address [ipv6-address/prefix-length]

Router(config-if)#no shutdown
```

### Set a Domain Name:
(SSH requires a domain name)
```
MyRouter(config)# ip domain-name [mydomain.com]
```

### Generate RSA Keys:
(RSA keys are required for SSH encryption)
```
MyRouter(config)# crypto key generate rsa
```
When prompted for the size of the key, you can choose a size (e.g., 1024 or 2048 bits). A larger key size is more secure but may require more processing power.

SSH version 2 has a minimum key size of 768 bits.

### Enable SSH Version 2:
```
MyRouter(config)# ip ssh version 2
```

### Create a Username and Password:
(Define a local username and password for SSH access)
```
MyRouter(config)# username [admin] privilege 15 secret [adminpassword]
```
Pls do not use admin and adminpassword as username and password.

### Configure the VTY Lines for SSH:
(Enable the VTY lines to use the local username and password for authentication and to only accept SSH connections)
```
MyRouter(config)# line vty 0 4

MyRouter(config-line)# login local

MyRouter(config-line)# transport input ssh

MyRouter(config-line)# exit
```

### Save the Configuration:
```
MyRouter(config)# exit

MyRouter# copy running-config startup-config
```


## information / troubleshooting

### Show IP Route:
This command shows the routing table, which includes directly connected networks and their associated interfaces.
```
Router# show ip route
```
![alt text](./output%20images/show_ip_route.PNG)

### Show ARP Table:
The ARP table shows the IP to MAC address mappings for devices connected to the router's interfaces.
```
Router# show ip arp
```
![alt text](./output%20images/show_ip_arp.PNG)

### Show IP Interface Brief:
This command provides a brief summary of the status of all interfaces, including IP addresses and operational status.
```
Router# show ip interface brief
```
![alt text](./output%20images/show_ip_interface_brief.PNG)

### Show MAC Address Table:
If your router supports Layer 2 switching features, you can see the MAC address table, which shows MAC addresses learned on each interface.
```
Router# show mac address-table
```
![alt text](./output%20images/show_mac_address_table.PNG)

### Show DHCP Bindings:
If your router is acting as a DHCP server, you can see a list of DHCP bindings, which include the IP address, MAC address, lease expiration, and interface.
```
Router# show ip dhcp binding
```
![alt text](./output%20images/show_dhcp_binding.PNG)

### Show CDP Neighbors:
The Cisco Discovery Protocol (CDP) can be used to display information about directly connected Cisco devices.
```
Router# show cdp neighbors
```
![alt text](./output%20images/show_cdp_neighbors.PNG)