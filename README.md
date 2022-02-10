# DevOps-Network-Traffic-Flow
Container to Docker to Internet Traffic Flow
Lets visualise the network diagram first

![Presentation1](https://user-images.githubusercontent.com/98175634/153356868-0ed0e90d-a83b-4e5f-8701-bf7dd57db422.jpg)


Packet flow from container to internet
1. From the container any packet will flow to container eth0(172.17.0.2) to virtual ethernet.
2. The packet will be forwarded to docker0 via gateway (172.17.0.1)
3. Then from docker eth0(172.31.7.64) the packet will flow via gateway 172.31.0.1 to the router.
