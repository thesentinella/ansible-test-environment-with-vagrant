# Ansible test environment with vagrant
Un entorno Vagrant para ejecutar Ubuntu 24.04 listo para probar comandos/playbooks de Ansible.

Dado que Vagrant proporciona entornos de trabajo fáciles de configurar, reproducibles y portátiles, este repositorio te ayuda a crear playbooks de Ansible en un entorno de prueba seguro utilizando Vagrant para emular entornos reales.

Una vez inicies el entorno con el comando vagrant up, estarás listo para ejecutar Ansible. El repositorio contiene un inventario preconfigurado listo para trabajar con el host de destino. Utilizamos una instancia de Ubuntu 24.04 y el usuario predeterminado de Vagrant para iniciar sesión.

## Cómo usar

### Requisitos Previos
- Instalar Vagrant y VirtualBox.
- Tener una clave SSH ubicada en: ~/.ssh/id_rsa.pub

### Levantar el Entorno
Iniciar el host de destino con Vagrant:
```
$ vagrant up
```
