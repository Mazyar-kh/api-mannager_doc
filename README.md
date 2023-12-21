# api-mannager_doc
#in case of cpu overload follow the instructions below:

1) ssh to all ContainerEngines[1,2,3], DPMS[1,2] machines and the API Mannagers.
2) secondly commentout the Intended API Mannagers node from nginx config files address{(node1:10.211.9.10)(node2:10.211.9.11)}.
   2.1) on the ContainerEngines we need to use "docker exec" command to enter the nginx container to have access to the config file.
           2.1.1) after entering the nginx countainer we can change the files in the following path: /etc/nginx/conf.d/default.conf.
   2.2) nginx is installed as a service on two dpms machines and we do not need to use docker.
           2.2.1)path to nginx config files on the dpms: /etc/nginx/conf.d.

3) after compliteing first two steps on the api-mannagers we use "docker-compuse down" command to delete the containers and then we run command "docker-compuse up" to recreate the containers.
    [3.1]) if the problem percise we can delete the /mnt/data/api-mannager file and redo the step 3.

4) at the end we uncomment the API Mannagers ip from nginx configs from both ContainerEngines and DPMS machines.
