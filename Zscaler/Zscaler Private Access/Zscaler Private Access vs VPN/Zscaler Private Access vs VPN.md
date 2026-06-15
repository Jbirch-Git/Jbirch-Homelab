#  Zscaler Private Access vs VPN

In this lab we are going to be talking about key differentiators between Zscaler Private Access and traditional VPN's. We are going to dive deeper into key components that stand out to help overall security, exposure and strenghten our audit posture.

# What is Zscaler Private Access

I will keep this short and sweet. Zscaler Private Access is a Zero trust Network Access platform which ties together both on premise and off premise application level access while evaluating additional contexts and Identity.

# Architecture

Let's briefly touch on the architecture that is foundational to Zscaler Platform and how we provide global application level access both securely and with a great user experience.

First let's talk about our traditional network. In this Architecture we find ourselves with multiple branch sites, an HQ and maybe some Iaas or Paas services as cloud workloads. Each interconnect between these resources require IPsec tunnel. Routed networks and Potentially inbound services or exposed public IP's. For us to support remote users we also add SSL or Ipsec Client VPN's.

![Legacy-Architecture](Images/Legacy-Architecture.png)

This architecture brings a lot of pain points forward that we can look to solve.

1: Public Address exposure  
2: Implicit Network trust  
3: Complex Policy and Network Administration  
4: Overly Permissive Client VPN  

How can we improve these pain point and what is the result from going through this change. Let's get into the technical nitty gritty for each and expose what true Zero Trust enlightenment brings.

# Public Address exposure

We have all been there. Cyber Insurance, External Pentest and Audit reports or even newly disclosed CVE's. A fundamental component to the network is your border. It determines how visible you are to the internet, how risky your business is classified by what resources are standing behind those public IP's and even what CVE's may be waiting to be exploited on your yearly pentest or Cyber Scan.

Because of the legacy network architecture we are forced to have exposed endpoints at each location. Firewall at the Branch and DC, NVA in the cloud or even an endpoint IP right off Azure. How can we do better, how can we reduce partially or even completely remove our public footprint? Hint, its Zscaler.

![ZTE-Architecture](Images/ZTE-Architecture.png)

If we look at the new Architecture above we have a key distinction. Remote users are connecting to the Zscaler POP through a DTLS/TLS connection but our deployed app connectors in the cloud and in the DC are NOT listening inbound for a TLS connection. There is no DNAT or exposed IP because connectivity is stitched at the Zscaler POP, app connectors also flow outbound over TLS to the Zscaler POP to relay information back to the user.

By removing VPN concentrators we no longer have public address exposure at the DC, Cloud or at the branch for end user connectivity. The application is requested by the device and the Zero Trust Exchange determines which app connector can reach the application to complete the connection and is then stitches to the Datacenter that the user is connected through.

# Implicit Network trust











# Reference Document List

https://www.zscaler.com/products-and-solutions/zero-trust-exchange-zte#assess-risk
