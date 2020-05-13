Servidor DNS en Centos
=========

Instala y configura desde cero un servidor de DNS maestro y esclavo.
- Instala el servicio named.
- configuracion de seguridad selinux y firewalld.
- configura Zonas DNS.
- configuracion archivo named.conf
- agregar nuevos subdominios.

Requirements
------------

- Servidor Centos 6 / 7 / 8.
- conectividad a internet en el servidor controlado.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

Luis Manuel Geronimo Sandoval(Sysadmin) canal de youtube #SysadminOne.
