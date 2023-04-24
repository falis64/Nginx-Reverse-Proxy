# Nginx-Reverse-Proxy

# What are ports?
A port in networking is a software-defined number associated to a network protocol that receives or transmits communication for a specific service. A port number is a 16-bit unsigned integer, which ranges from 0 to 65535. Applications use ports to establish communication channels with other applications running on remote devices over the network.

- port (22) - used for ssh connection
- port (80) - used for HTTP connection
- port (443) - used for HTTPS connection

# What is a reverse proxy? How is it different from a proxy?

A reverse proxy is a type of proxy server that sits between client devices and one or more servers. It receives requests from clients on behalf of servers and forwards them to the appropriate server. The server's response is then returned to the client by the reverse proxy. A reverse proxy helps to improve performance, security, and scalability of web applications by offloading server resources and serving as a single point of contact for clients.

A proxy server, on the other hand, acts as an intermediary between clients and servers. It receives requests from clients and forwards them to the appropriate server. The server's response is then returned to the client by the proxy. A proxy server helps to improve security and privacy by masking the identity of clients from servers and vice versa.

The main difference between a reverse proxy and a proxy is the direction of traffic flow. In a proxy, traffic flows from the client to the server, while in a reverse proxy, traffic flows from the server to the client.

![image](https://user-images.githubusercontent.com/129381619/232850754-4e0a360e-f818-416a-b1f2-1cd742e8ca2c.png)

# Nginx's default configuration:
The default configuration for Nginx is stored in the sites-available directory. This directory contains a file called default that defines the default server block for Nginx. The default server block listens on port 80 and serves files from the /var/www/html directory.

# How do you set up a Nginx reverse proxy?

Follow the steps below to set it up:
1) Start your VM by using vagrant up in VS Code terminal. For this, ensure that app.js is not being deployed automatically in your provisioning.sh

2) Connect to your VM with Bash terminal by navigating into your project folder with cd command and then use vagrant ssh command

3) Use command cd /etc/nginx/sites-available in order to navigate inside the nginx configuration folder

4) Create a new configuration file with nano by using the following command: sudo nano nodeapp.conf (name could be anything, but try to make logical)

5) Inside the file type the following code:

```
server {
   listen 80;
   server_name 192.168.10.100;

   location / {
       proxy_pass http://192.168.10.100:3000;
       proxy_set_header Host $host;
       proxy_set_header X-Real-IP $remote_addr;
       proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
       proxy_set_header X-Forwarded-Proto $scheme;
   }
}
```
````server_name ***`  - can be the name of your server or your ip address```

6) Use ctrl+x to exit nano, then press y to save the changes, and then press enter to save the name of the file

7) Enable the configuration by creating a symbolic link to enable a new config file: sudo ln -s /etc/nginx/sites-available/nodeapp.conf /etc/nginx/sites-enabled/nodeapp.conf

8) Checnk configuration for errors sudo nginx -t

9) Reload nginx - sudo systemctl reload nginx

10) Go back to your home folder by using cd command and then navigate in to cd app

11) Launch app by using node app.js

12) Paste your ip, without port number, into browser and check if it works:
