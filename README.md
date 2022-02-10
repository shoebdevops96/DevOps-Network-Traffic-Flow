# DevOps-Network-Traffic-Flow
Container to Docker to Internet Traffic Flow
Lets visualize the network diagram first

![Presentation1](https://user-images.githubusercontent.com/98175634/153356868-0ed0e90d-a83b-4e5f-8701-bf7dd57db422.jpg)


Packet flow from container to internet
1. From the container any packet will flow to container eth0(172.17.0.2) to virtual ethernet.
2. The packet will be forwarded to docker0 via gateway (172.17.0.1)
3. Then from docker eth0(172.31.7.64) the packet will flow via gateway 172.31.0.1 to the router and then to the internet.


Capturing packet in container eth0

<img width="550" alt="image" src="https://user-images.githubusercontent.com/98175634/153358243-07bc0a99-9920-4533-a89a-1ec8b43158e2.png">

Capturing eth0 packet in 80(http) port

tcpdump -i eth0 dst port 80

Now i will try to telnet one public ip in 80 port from my container. Lets see if we can trace any packet.

So from another window I command 

telnet 103.78.53.92 80

here is the result

<img width="851" alt="image" src="https://user-images.githubusercontent.com/98175634/153359655-57b581cb-dca7-4695-83a8-1a7add059129.png">


Now i will try to telnet from my docker to container and the captute the packet of container eth0 port 80

Telnet from Docker ip(172.17.0.2)

telnet 172.17.0.2 80


Now here is the captured packet from container eth0

<img width="843" alt="image" src="https://user-images.githubusercontent.com/98175634/153361390-8b9215a7-f107-4568-9acb-8e7eee5f1039.png">



Similiarly to capture packet from any specific IP we can command

tcpdump -i eth0 dst host 8.8.8.8


<img width="617" alt="image" src="https://user-images.githubusercontent.com/98175634/153362864-22c60726-cb7f-40bc-bf4f-e390c3f9d817.png">

here i am pining 8.8.8.8 from my container and above is packet captured in my container eth0 port




