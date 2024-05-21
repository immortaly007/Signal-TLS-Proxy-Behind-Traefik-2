# Signal TLS Proxy Behind Traefik 2

This setup assumes that you have multiple services running on your server, and [Traefik 2](https://traefik.io/traefik/) is used as the load balancer. 
This means that Traefik will also handle the SSL termination.

To run a Signal TLS proxy, you will need a host with a domain name that has ports 80 and 443 available. Optionally, this host may already have [Traefik 2.0](https://traefik.io/traefik/) installed with a Docker provider configured. To run the proxy:

1. Install [Docker](https://docs.docker.com/get-docker/) & [Docker compose](https://docs.docker.com/compose/install/).
2. Clone this repository
3. Update the following line in the `docker-compose.yml` file, by adding the correct traefik labels; replace `signal.mydomain.com` by your hostname.
   ```
   traefik.tcp.routers.signal-proxy.rule=HostSNI("signal.mydomain.com") 
   ```
4. Update your e-mail address in `/data/traefik/traefik.yml`; `certificatesResolvers.leresolver.acme.email`
5. (Optional) if you already have a running Traefik, comment out/delete the traefik service in the `docker-compose.yml` file, and make sure that the certresolver name for the proxy container matches your Traefik installation.
6. `docker compose up --detach --build`

Your proxy is now running! You can share this with the URL `https://signal.tube/#<your_host_name>`
