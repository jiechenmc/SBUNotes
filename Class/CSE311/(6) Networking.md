
The five protocol layers are:
- Application
- Transport (TCP UDP)
- Network (IP ICMP)
- Data Link (ARP ETHERNET WIFI)
- Physical layers (COPPER FIBER)

You can figure out the mac address of a IP by using ARP to query

Subnet Mask /n = n is the number of 1 in 32 bits

![[Pasted image 20230322222442.png]]

The number of subnet networks = 2<sup>n-24</sup>

![[Pasted image 20230322222837.png]]


![[Pasted image 20230322225557.png]]

The number of supernetted networks = 2<sup>n-21</sup>

<h1>Homework 3</h1>

Installing Lamp tldr;

install apache2
let it through the firewall

SSL-cert-snake oil is a self-signed certificate.

### Tunneling

>ssh -L 80:130.245.155.30:9000 ta@130.245.155.30

This will tunnel localhost on the local machine to 130.245.155.30:9000 through ta@130.245.155.30

>ssh -R 8080:130.245.155.33:9001 ta@130.245.155.30

This will tunnel localhost:8080 from the remote machine to 130.245.155.30:9001 through the local machine