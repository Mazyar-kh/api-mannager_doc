# API Manager Operational Guidelines

In the event of CPU overload, it is imperative to follow the protocol outlined below:

1. Access all Container Engines [1, 2, 3], BDMS [1, 2, 3] machines, and the API Manager via SSH.

2. Exclude the specified API Manager nodes from the Nginx configuration files using the following IP addresses: (node1: 10.211.9.10), (node2: 10.211.9.11), and (node3: 10.211.9.12), in accordance with the structure of the included configuration files.

    2.1. For the Container Engines, utilize the "docker exec" command to enter the Nginx container and navigate to the configuration file.
        
        2.1.1. Within the Nginx container, make the necessary modifications to the configuration files located at: /etc/nginx/conf.d/default.conf.

    2.2. Nginx is installed as a service on the three BDMS machines and does not require the use of Docker.

        2.2.1. The path to the Nginx configuration files on the BDMS machines is: /etc/nginx/conf.d.

3. Upon completing the initial steps, execute the "docker-compose down" command on the API Manager machine to remove the container, followed by running "docker-compose up" to recreate the containers.

4. Subsequently, reinstate the API Manager IP in the Nginx configurations on both the Container Engines and BDMS machines.

    4.1. If multiple API machines are experiencing CPU overload, it is essential to perform these procedures separately for each API Manager machine.

Remark: It is imperative to omit API Managers one by one for ensuring high availability (HA) of applications.
