# API Manager Documentation

In the event of CPU overload, please follow the instructions below:

1. SSH into all Container Engines [1, 2, 3], DPMS [1, 2] machines, and the API Manager.

2. Comment out the intended API Manager node from the Nginx configuration files with the following addresses: (node1: 10.211.9.10) and (node2: 10.211.9.11).

    2.1. On the Container Engines, use the "docker exec" command to enter the Nginx container and access the configuration file.
        
        2.1.1. After entering the Nginx container, modify the configuration files located at: /etc/nginx/conf.d/default.conf.

    2.2. Nginx is installed as a service on the two DPMS machines, and it does not require the use of Docker.
        
        2.2.1. The path to the Nginx configuration files on the DPMS machines is: /etc/nginx/conf.d.

3. Once the first two steps are completed, on the API Manager machine use the "docker-compose down" command to delete the container, followed by running the command "docker-compose up" to recreate the containers.

4. Finally, uncomment the API Manager IP from the Nginx configurations on both the Container Engines and DPMS machines.
   4.1. if more than one api machine has the cpu overload its necessery to do this steps separately for each api mannager machine.
