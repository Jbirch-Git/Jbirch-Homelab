# IBGP-RR LAB

In this Lab we are displaying the use case for RR within the same AS (IBGP Peers) to avoid having to create a full mesh IBGP neighbor configuration.

The reason Route Reflection is required is because IBGP neighbors will not advertise a network received from one IBGP neighbor to another IBGP neighbor.

![Routing Diagram](./Images/test.png)
