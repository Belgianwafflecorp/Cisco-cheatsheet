# Switch

### Enter privileged EXEC mode:
```
switch> enable
```

### Enter global configuration mode:
```
switch# configure terminal
```

### Set Hostname for the Switch:
```
switch(config)# hostname [MySwitch]
```

### Enter interface configuration mode for VLAN 1:
```
switch(config)# interface vlan 1
```

### Set the IPv4 address and subnet mask for VLAN 1:
```
switch(config-if)# ip address [10.0.1.5 255.255.255.0]
```

Set the IPv6 address for VLAN 1:
```
switch(config-if)# ipv6 address [2001:db8:acad:1::1/64]
```

### Enable IPv6 on the interface:
```
switch(config-if)# ipv6 enable
```

### Ensure the interface is enabled:
(not necessary if it's already up)
```
switch(config-if)# no shutdown
```

### default-gateway (router):
```
switch(config)#ip default-gateway [192.168.0.254]
```

## Enable SSH on the Switch

### Set the domain name:
```
MySwitch(config)# ip domain-name [MyDomain.com]
```

### Generate RSA keys with a modulus of 2048 bits:
(More info about the keys in the router file)
```
MySwitch(config)# crypto key generate rsa general-keys modulus 2048
```

### Enable SSH version 2:
```
MySwitch(config)# ip ssh version 2
```

###Create a local user with privilege level 15 and a secret password:
```
MySwitch(config)# username [admin] privilege 15 secret [adminPassword]
```

### Configure the VTY Lines for SSH:
```
MySwitch(config)# line vty 0 15

MySwitch(config-line)# login local

MySwitch(config-line)# transport input ssh

MySwitch(config-line)# exit
```

### Save the configuration to NVRAM:
```
MySwitch# write memory
```

