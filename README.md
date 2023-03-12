# webmin-opennebula

Instalación de un servidor Webmin en OpenNebula con Terraform y Ansible.

## Prerrequisitos

1. Instalar Docker Desktop para [Windows y macOS](https://www.docker.com/products/docker-desktop/)
   o [Linux](https://docs.docker.com/desktop/linux/install/).

2. En Windows, instalar [Scoop](https://scoop.sh) usando PowerShell:

   ```powershell
   Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
   [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
   Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh')
   ```

   Y después instalar los comandos necesarios:

   ```powershell
   scoop install make
   ```

## Puesta en marcha

1. Crear el fichero `.env` a partir de `env-example` y configurar las variables.
2. Crear el fichero `terraform/variables.tf` a partir de `terraform/variables.tf.example` y configurar las variables.
3. Construir el contenedor donde se ejecuta Terraform.

    ```shell
    make build
    ```
4. Crear la clave privada SSH para Ansible e inicializar Terraform.

    ```shell
    make init
    ```

5. Desplegar la máquina virtual en OpenNebula.

    ```shell
    make apply
    ```

6. Conectarse a la máquina virtual.

   https://ip:10000

## Referencias

- [Downloading and Installing](https://webmin.com/download/)
- [How to Install Webmin with free Let's Encrypt SSL Certificate on Ubuntu 22.04](https://www.howtoforge.com/tutorial/ubuntu-webmin-installation/)
- [Configuring Nginx reverse proxy for webmin](https://stackoverflow.com/questions/22608942/configuring-nginx-reverse-proxy-for-webmin)
- [2 Ways to change user password with Ansible](https://www.howtouselinux.com/post/change-user-password-with-ansible)
- [How to pass password to Ansible from environment variable](https://medium.com/opsops/how-to-pass-password-to-ansible-from-environment-variable-bd5c566bc8a1)
