# Nginx-Reverse-Proxy

# What are ports?
A port in networking is a software-defined number associated to a network protocol that receives or transmits communication for a specific service. A port number is a 16-bit unsigned integer, which ranges from 0 to 65535. Applications use ports to establish communication channels with other applications running on remote devices over the network.

# What is a reverse proxy? How is it different from a proxy?

A reverse proxy is a type of proxy server that sits between client devices and one or more servers. It receives requests from clients on behalf of servers and forwards them to the appropriate server. The server's response is then returned to the client by the reverse proxy. A reverse proxy helps to improve performance, security, and scalability of web applications by offloading server resources and serving as a single point of contact for clients.

A proxy server, on the other hand, acts as an intermediary between clients and servers. It receives requests from clients and forwards them to the appropriate server. The server's response is then returned to the client by the proxy. A proxy server helps to improve security and privacy by masking the identity of clients from servers and vice versa.

The main difference between a reverse proxy and a proxy is the direction of traffic flow. In a proxy, traffic flows from the client to the server, while in a reverse proxy, traffic flows from the server to the client.

![image](https://user-images.githubusercontent.com/129381619/232850754-4e0a360e-f818-416a-b1f2-1cd742e8ca2c.png)

# Nginx's default configuration:
The default configuration for Nginx is stored in the sites-available directory. This directory contains a file called default that defines the default server block for Nginx. The default server block listens on port 80 and serves files from the /var/www/html directory.

# How do you set up a Nginx reverse proxy?
