# Signal TLS Proxy Behind Traefik 2

This setup assumes that you have multiple services running on your server, and traefik 2 is used as the load balancer. 
This means that Traefik will also handle the SSL termination.

To run a Signal TLS proxy, you will need a host with a domain name that has ports 80 and 443 available.

1. Install docker and docker-compose (`apt update && apt install docker docker-compose`)
2. Clone this repository
3. `./init-certificate.sh`
4. `docker-compose up --detach`

Your proxy is now running! You can share this with the URL `https://signal.tube/#<your_host_name>` 
