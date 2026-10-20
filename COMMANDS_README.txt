----------------Static Routing----------------
Lan1 and Lan2

For Lan1 and vica verca. 
comands:
Router>enable
Router# configure terminal
Router(config)# ip route (netip of Lan2) (subnet of lan2) (ipof the router2)
Router(config)# exit
Router# write

Example:
Router>enable
Router# configure terminal
Router(config)# ip route 10.0.0.0 255.0.0.0 20.0.0.2
Router(config)# exit
Router# write


----------------RIP----------------
eazy method 
do same for all routers:
open router:
goto config tab:
Under ROUTING SELECT RIP:
add all the netip that exists in the topoplgy one by one:
example:
10.0.0.0
20.0.0.0
30.0.0.0
192.168.10.0
192.168.20.0
192.168.30.0

or do with CLI method:
Router>enable
Router# configure terminal
Router(config)# router rip
Router(config-router)# network 10.0.0.0
Router(config-router)# network 20.0.0.0
Router(config-router)# network 30.0.0.0
Router(config-router)# network 192.168.30.0
Router(config-router)# network 192.168.20.0
Router(config-router)# network 192.168.10.0
Router(config-router)# exit
Router(config)# exit
Router# write  

----------------Single OSPF----------------
same for next router connected to lan:
no config for 3rd router withouth any pc:

Router>enable
Router# configure terminal
Router(config)# router ospf 1
Router(config-router)# network (lan netip) (lansubnet) area 0
Router(config-router)# network (neighobour1router netip) area 0
Router(config-router)# network (neighobour2router netip) area 0
Router(config-router)# exit
Router(config)# exit
Router# write

----------------Multi OSPF----------------
just add the neibours netip connected to the routers(be smart):
Router>enable
Router# configure terminal
Router(config)# router ospf 1

example for center router use ur brain for the side 2:
Router(config-router)# network 10.1.1.0 0.225.225.225 area 0
Router(config-router)# network 20.1.1.0 0.225.225.225 area 0
Router(config-router)# ex

Router(config)# ex
Router# write
----------------BGP----------------
Configuration commands(respect to router):
Router> enable 
Router# configure terminal
Router(config)#router bgp 1
Router(config-router)#neighbor 20.0.0.2 remote-as 2
Router(config-router)#network 10.0.0.0
Router(config-router)#end

Router#write

Tocheck:
Router#show ip route bgp

To remove Bgp router config:
Router# configure terminal
Router(config)# no router bgp 1
Router(config)# end
Router# write memory