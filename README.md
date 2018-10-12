Building a simple LAMP stack and deploying Application using Ansible Playbooks.
-------------------------------------------

Se migró el script de redHat a ubuntu

       [webservers]
web3 ansible_port=2221 ansible_ssh_private_key_file=./key.private

       [dbservers]
web2 ansible_port=2222 ansible_ssh_private_key_file=./key.private



        ansible-playbook -i ./hosts site.yml

una vez ejecutado el playbook, entrar al ip del web3 asignado
-se agrego el directorio server con dos dockers para los servicios
-se editaron los roles, y se tuvo que eliminar el uso de SELinux
-Se edito el clean_all.sh, create_docker.sh, los hosts
-Por ahora se puede accesar al servidor y muestra mensaje de bienvenida

#NOTA IMPORTANTE
Se usa el servicio de apache2, lo cual toca ir a eliminar la carpeta que se genera (index.html)
para que el comando de copiado de la URL del ejemplo se ejecute (todo antes de ejecutar el playbook).

Para esto:
1.-Entrar al docker que ejecuta el servidor web
       sudo docker exec -it web3 bash
2.-Entrar a la carpeta raíz donde guarda apache sus archivos
       cd var/www/html
3.-Eliminar index.html
       rm index.html

luego de eso se ejecuta el playbook
