# ansible-vagrant
Despliegue automatico de wordpress con ansible y vagrant

El escenario está compuesto por 2 máquinas:
nodo1 - MariaDB y Bind9
nodo2 - Nginx con FPM

Requisitos:
dhcp en la interfaz donde se lanzen las máquinas
añadir el DNS en el fichero /etc/resolv.conf

La dirección del DNS y el nombre de la web se muestran al final de la configuración de ansible
