Servidor DNS en linux Centos
=========

Instala y configura desde cero un servidor de DNS maestro y esclavo.
- Instala el servicio named.
- configuracion de seguridad selinux y firewalld.
- configura Zonas DNS.
- configuracion archivo named.conf
- agregar nuevos subdominios.

Requirements
------------
#Servidor
- Servidor Centos 6 / 7 / 8.
- conectividad a internet en el servidor controlado.

#Archivos
para crear una nueva zona con el dominio tienes que modifcar los archivos template y a gregar a las variables el dominio que vas a crear.
ejemplo copiar el archivo midominio.com.zone.j2 en la ruta ../templates/ cambiando todo de la plabra midominio por el nombre de dominio personalizado.


Role Variables
--------------

El archivo de variables se encuentra en vars/main.yml.

Variables:

Variables para las nuevas zonas.
- zoneDomain ## Dominios que agregara.
- serialZone ##Serial para cada cambio.
Varaibles para modificar, eliminar y agregar sudminios
- subDomain ##Subominio que agregaras en una zona
- serialZone ##Serial para cada cambio.
Variables para el archivo named.conf
- acls ##Define una regla de seguridad para los segmentos reconocidos.
- slaves ##Define en el DNS maestro uno a varios servidores esclavos DNS ejemplo '10.10.4.32; 10.10.5.32;' 
- slaveserver ##Define que ips escucha el DNS esclavo.
- master ##Define un solo servidor maestro en el DNS esclavo.
- masterserver ##Define que ips escucha el DNS maestro.


Playbook
----------------

Crear archivo principal manageDNS.yml

---
- hosts: host-dns
  become: true
  name: 'Configuracion e instalacion DNS Server'
  roles:
    - ansible-dns

Ejecucion playbook
------------------

#Instalar solamente el servicio DNS y configurar firewalld y selinux.
- ansible-playbook manageDNS.yml -t install

#Instalar y configurar DNS maestro desde cero.
- ansible-playbook manageDNS.yml -t install,master

#Instalar y configurar DNS esclavo desde cero.
- ansible-playbook manageDNS.yml -t install,slave

#agregar nuevo subdominio. En esta parte no olvides editar el file .j2 en la ruta de template y modificar el serial en el archivo de variables.
- ansible-playbook manageDNS.yml -t subdomain

License
-------

BSD

Autor
------------------

Luis Manuel Geronimo Sandoval(Sysadmin) canal de youtube #SysadminOne.
