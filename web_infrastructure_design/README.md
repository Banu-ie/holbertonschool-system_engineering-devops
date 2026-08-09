# Web infrastructure design

This project is about designing the web infrastructure behind a website reachable at `www.foobar.com`, starting from a single-server LAMP-style setup and progressively evolving it into a distributed, secured, monitored, and horizontally-scaled infrastructure.

Each task was whiteboarded by hand. A photo of each whiteboard diagram is linked from the corresponding answer file in this directory.

## Tasks

### 0. Simple web stack
A single server hosting a web server (Nginx), an application server, the application code base, and a MySQL database, reachable via a `www` A record pointing `foobar.com` to the server's IP.

Covers: what a server/domain name/web server/app server/database is, how DNS resolves `www.foobar.com`, and why this setup is a single point of failure, causes downtime on deploy, and can't scale.

Diagram link: see [`0-simple_web_stack`](./0-simple_web_stack)

### 1. Distributed web infrastructure
Adds a load balancer (HAProxy) in front of two identical servers, each running a web server, application server, code base, and MySQL node, with the databases set up in a Primary-Replica configuration.

Covers: load balancing algorithms, active-active vs active-passive, Primary-Replica replication, and remaining issues (load balancer SPOF, no firewall/HTTPS, no monitoring).

Diagram link: see [`1-distributed_web_infrastructure`](./1-distributed_web_infrastructure)

### 2. Secured and monitored web infrastructure
Adds three firewalls, an SSL certificate to serve the site over HTTPS, and monitoring clients on each server.

Covers: what firewalls and HTTPS protect against, how monitoring agents collect and report data, monitoring QPS specifically, and the issues introduced by terminating SSL at the load balancer, having a single write-capable database node, and colocating all components per server.

Diagram link: see [`2-secured_and_monitored_web_infrastructure`](./2-secured_and_monitored_web_infrastructure)

### 3. Scale up
Splits the web server, application server, and database onto their own dedicated servers, and clusters the load balancer with a second one for redundancy.

Covers: why isolating each component lets it scale independently, and why clustering the load balancer removes it as a single point of failure.

Diagram link: see [`3-scale_up`](./3-scale_up)

## Author
Banu
