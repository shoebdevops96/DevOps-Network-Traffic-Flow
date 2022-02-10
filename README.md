# DevOps-Network-Traffic-Flow
Container to Docker to Internet Traffic Flow
Lets visualise the network diagram first

![Presentation1](https://user-images.githubusercontent.com/98175634/153356868-0ed0e90d-a83b-4e5f-8701-bf7dd57db422.jpg)


Packet flow from container to internet
1. From the container any packet will flow to container eth0(172.17.0.2) to virtual ethernet.
2. The packet will be forwarded to docker0 via gateway (172.17.0.1)
3. Then from docker eth0(172.31.7.64) the packet will flow via gateway 172.31.0.1 to the router and then to the internet.


Capturing packet in container eth0

<img width="550" alt="image" src="https://user-images.githubusercontent.com/98175634/153358243-07bc0a99-9920-4533-a89a-1ec8b43158e2.png">

Capturing eth0 packet in 80(http) port

tcpdump -i eth0 dst port 80

Now i will try to telnet one public in 80 port from my container. Lets see if we can trace any packet.

So from another window I command 

telnet 103.78.53.92 80

here is the result

<img width="851" alt="image" src="https://user-images.githubusercontent.com/98175634/153359655-57b581cb-dca7-4695-83a8-1a7add059129.png">





