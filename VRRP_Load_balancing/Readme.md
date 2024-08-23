## VRRP (Virtual Router Redundancy Protocol) </br>

The VRRP protocol in our lab has two different functions: </br>
***1. Network load balancing*** </br>
***2. Redundancy in case of network failure***

<h3>Network load balancing</h3>
From the picture, we can see that there are two routers R2 and R3 on which the virtual address (vip) is set.
From computer PC1, packets are sent to router R1, while PC2 sends packets to router R2.

![Vrrp](https://user-images.githubusercontent.com/24782270/233429730-c448ed4c-885b-43d7-af6f-cd6ff34f5cfd.JPG) </br></br>

Virtual routers within a VRRP group have a unique MAC address: 00-00-5E-00-01-[VRID].</br>
VRID represents the identity of the given group and can have values ​​between 0-255. From the picture, we can see two VRRP groups, group 1 to which router R1 belongs, and Group two to which router R2 belongs.
Each group has a master and backup router.
Master routers use the virtual MAC addresses assigned to them to respond to ARP requests from hosts. The ARP request establishes a connection between devices (hosts) and the network.
Each router within a VRRP group is assigned appropriate priorities. A router with a higher priority becomes the master router, while a router with a lower priority becomes a backup router. </br>
In case we have the same priorities in one VRRP group, the IP address and that router are observed
which has a higher address becomes the virtual master router.

<h3>Redundancy in case of network failure</h3>
The task in this lab is to send packets from hosts to router R3 successfully. Router R3 does not belong to any Vrrp group. It represents a connection to an external network. </br>
By setting up appropriate virtual groups, we can ensure a certain level of redundancy.
In the event of an interruption of the operation of the master router in the VRRP group, the backup routers will assume the primary role of the master router that is interrupted. With the VRRP protocol, we ensure that there is no way to reach (SPOF), in the event of an interruption, the flow of the entire network is not stopped.
</br>
</br>
</br>
<h4>Network packet simulations</h4>
We can continuously send packets over the network with the command <em>ping 210.37.0.1 -t</em> on the PC1 or PC2 terminal. At some point, we can shut down any connection between the switch and router R2 or R1 or disconnect the connection between router R2 and R3 or R1 and R3. By observing the terminal, we can see that it takes a shorter period to resend and that a certain part of the package did not reach the desired destination.</br>
We can perform the same interruption simulation in the OSPF_Compare lab, located in the OSPF_Load_B folder, as long as only OSPF routing is applied to the given topology.
