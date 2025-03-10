# EBGP LAB

In this Lab we are creating a 5 router EBGP peering network. This has a total of 4 AS's with one containing an IBGP peer.

Assets in the Lab:

R1,R2,R3,R4,R5

We are going to connect R1,R2,R3,R4 and R5 in the following topology.

![Topology](Images/Topology.png)

- The Networks used will be 10.X.0.0/24. X will be the combined number of the router numbers. R1,R2 = 10.12.0.0/24 etc.
- We will also have a loopback on each router based on their router number that we will be advertising over BGP Ex: R1 = 1.1.1.1.

R1 = 10.12.0.1, 10.51.0.1  
R2 = 10.12.0.2, 10.23.0.1  
R3 = 10.23.0.2, 10.34.0.1  
R4 = 10.34.0.2  
R5 = 10.51.0.2  

To cut down on the length of the document I will not be documenting all configuration for all peers. Lets start with R5 to R1 and the rest of the routers follow suit.

R5:  
router bgp 65544  
neighbor 10.51.0.1 remote-as 65545  
neighbor 10.51.0.1 activate  
address-family ipv4 unicast  
network 5.5.5.0 mask 255.255.255.0  

R1:  
router bgp 65545  
neighbor 10.51.0.2 remote-as 65545  
neighbor 10.51.0.2 activate  
address-family ipv4 unicast  
network 1.1.1.0 mask 255.255.255.0  

These same steps apply for all other routers in the topology just with different remote-as numbers.

Once all the neighbors are online lets take a look at the far most router R5's BGP table.

![R5-Route-Table](Images/R5-Route-Table.png)