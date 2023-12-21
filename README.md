# API Manager Documentation

In the event of CPU overload, please follow the instructions below:

1. SSH into all Container Engines [1, 2, 3], DPMS [1, 2] machines, and the API Managers.

2. Comment out the intended API Managers node from the Nginx configuration files with the following addresses: (node1: 10.211.9.10) and (node2: 10.211.9.11).

    2.1. On the Container Engines, use the "docker exec" command to enter the Nginx container and access the configuration file.
        
        2.1.1. After entering the Nginx container, modify the configuration files located at: /etc/nginx/conf.d/default.conf.

    2.2. Nginx is installed as a service on two DPMS machines, and it does not require the use of Docker.
        
        2.2.1. The path to the Nginx configuration files on the DPMS machines is: /etc/nginx/conf.d.

3. Once the first two steps are completed, on the API Managers, use the "docker-compose down" command to delete the containers, followed by running the command "docker-compose up" to recreate the containers.

    3.1. If the issue persists, you can delete the /mnt/data/api-manager file and redo step 3.

4. Finally, uncomment the API Managers' IP from the Nginx configurations on both the Container Engines and DPMS machines.
