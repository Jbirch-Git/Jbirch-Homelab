# NAT Lab

In this lab we will be creating multiple NAT configurations to display the different NAT use cases.

Topology for this lab:

![Topology](Images/Topology.png)

# Static NAT

First we will configure Static NAT on R1 to mask the inside address on the outside interface.

Lets first define the zones within the topology.

![Topology-Zones](Images/Topology-Zones.png)

In this you can see the inside local/global as well as outside local/global zones. In this example we will be NAT'ing the Inside local zone to an IP on the inside local address space. From the outside global's perspective the traffic will be coming from the outside local address.

To define the zones you use the following command on the interface level:

ip nat (inside) or (outside)

Inside is where your endpoints and local networks live outside normally points to the internet or an external connection. This is not mandatory you can use outside to define the inside and inside to define the outside.

On R1 we defined the loopback interface as the inside zone and E0/0 as the outside zone.

Now lets create the static NAT to transform 1.1.1.1 from the inside zone to 10.1.0.3/24 going to the outside zone. Once we apply this 10.1.0.3 is assigned to 1.1.1.1 and only 1.1.1.1 any other inside address cannot use this IP NAT as this is a static assignment.

R1:

ip nat inside source static 1.1.1.1 10.1.0.3

Let's now run a ping to 10.1.0.2 and see the result through a packet capture on the E0/0 interface.

![Static-PCAP](Images/STATIC-PCAP.png)

As we can see the interface capture shows the source traffic coming from 10.1.0.3 which is a result of R1 NAT'ing the traffic before sending it out that interface.

Here is a look at the NAT translation table.

![R1-NAT-Table](Images/R1-NAT-Table.png)

We can see this entry lives in the NAT table even if its not passing any traffic at the time. 1.1.1.1 will translate to 10.1.0.3.