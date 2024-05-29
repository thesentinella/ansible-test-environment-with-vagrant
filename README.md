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
vagrant up
```

### Ejecutar ansible

```
ansible -i inventory -m ping myhosts
```

Salida:
```
192.168.56.10 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
```

Encontrarás una colección de playbooks en su directorio listos para usarse. El objetivo del playbook se define como una variable. Para que coincida con el host actual de Vagrant, necesitas pasar el objetivo de la siguiente manera:
```
ansible-playbook -i inventory playbooks/addcronjob.yaml --extra-vars "target=myhosts"
```

Salida:

```
PLAY [myhosts] ******************************************************************************************************************************************************************************************************

TASK [Gathering Facts] **********************************************************************************************************************************************************************************************
ok: [192.168.56.10]

TASK [cron] *********************************************************************************************************************************************************************************************************
ok: [192.168.56.10]

PLAY RECAP **********************************************************************************************************************************************************************************************************
192.168.56.10              : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```

## Debug
Puedes acceder a la VM con:

```
vagrant ssh
```

O usando un cliente SSH predeterminado:

```
ssh vagrant@192.168.56.10
```