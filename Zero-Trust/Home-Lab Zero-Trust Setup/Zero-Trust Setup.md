#  Home-Lab Zero Trust Setup

I will be deploying Cloud Flares Zero Trust free tier solution to my homelab to display a simple Zero trust configuration as well as help quantify the differences between Zero Trust architecture vs traditional network architectures.

The first step which is important for publishing DNS records that point public hostnames to internal applications is to have a public domain and set cloudflare are your DNS server through NS records.

There is a step by step process that guides you through theses steps as you register your domain into Cloud Flare. Once completed you can see the NS servers under your domain > DNS > Records.

![NS-Record](Images/NS-Record.png)