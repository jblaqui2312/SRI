# Actividad #1
![Descripción de la captura]()
Lee el siguiente artículo e instala Apache en Ubuntu:
https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-20-04-es

## 1.Instalar Apache y actualizar el firewall

Para comenzar con la configuración del servidor web en mi máquina Ubuntu, en primer lugar procedo a actualizar la lista de paquetes del gestor `apt` e instalar el paquete correspondiente a Apache.

### 1.1. Actualizar el índice de paquetes

Ejecuto el siguiente comando para asegurarme de obtener la información más reciente de los repositorios:

```sudo apt update```

### Capturas de pantalla
![Descripción de la captura](https://github.com/user-attachments/assets/5fbb0742-b567-45cd-9371-7c372f6fb060)

```sudo apt install apache2```

### Capturas de pantalla
![Descripción de la captura](https://github.com/user-attachments/assets/e215c018-91ee-4cb5-afcf-5c69ff83210c)


## 1.2 Configuración del firewall (UFW)

Una vez completada la instalación de Apache, procedo a ajustar la configuración del firewall (`ufw`) para permitir el tráfico web.

### 1.2.1 Listar los perfiles de aplicaciones disponibles en UFW

Para verificar qué perfiles de aplicación reconoce el firewall, ejecuto el siguiente comando:

```sudo ufw app list```

### Capturas de pantalla
![Descripción de la captura](https://github.com/user-attachments/assets/78b6c657-bc84-4a38-a418-0f0a1d9726d6)

### 1.2.2 Análisis de los perfiles de Apache
Analizo las opciones disponibles para seleccionar la más adecuada:

Apache: Abre únicamente el puerto 80 (tráfico web HTTP no cifrado).

Apache Full: Abre el puerto 80 (HTTP) y el puerto 443 (tráfico cifrado HTTPS con TLS/SSL).

Apache Secure: Abre únicamente el puerto 443 (HTTPS cifrado).

Dado que acabo de realizar la instalación base de Apache y aún no dispongo de un certificado TLS/SSL configurado, selecciono el perfil Apache para permitir el tráfico por el puerto 80.


### 1.2.3 Permitir el tráfico en el puerto 80

Para habilitar únicamente el tráfico web no cifrado mediante el perfil **Apache**, ejecuto el siguiente comando:

```sudo ufw allow in "Apache```

### Capturas de pantalla
![Descripción de la captura](https://github.com/user-attachments/assets/8d7fb16c-eff4-426b-81af-8cd627d71c66)

### 1.2.4 Comprobar el estado del firewall
A continuación, verifico que la regla se ha aplicado correctamente y que el tráfico para Apache está permitido:

```sudo ufw status```

### Capturas de pantalla
![Descripción de la captura](https://github.com/user-attachments/assets/810aeefc-14ec-46fd-b80e-a56fb4cc7278)

### 1.2.5 Verificación de funcionamiento en el navegador
Para comprobar que todo se ha configurado de manera correcta, me dirijo a un navegador web e introduzco la dirección IP pública de mi servidor:

http://TU_DIRECCION_IP

### Capturas de pantalla

![Descripción de la captura](https://github.com/user-attachments/assets/36eb0c97-5d71-42a5-81d9-a83d0ce0b35c)

## 1.3 Identificar la IP pública del servidor y verificar Apache

Para acceder a la página web predeterminada de Apache desde un navegador, procedo a obtener la dirección IP pública de mi servidor.

### 1.3.1. Obtener la IP mediante las herramientas del sistema (`iproute2`)

En primer lugar, consulto la dirección IP asignada a la interfaz de red ejecutan el siguiente comando:

```ip addr show eth0 | grep inet | awk '{ print $2; }' | sed 's/\/.*$//'```

![Descripción de la captura](https://github.com/user-attachments/assets/d2877061-f875-4de7-b444-ffcd96470ce0)

## 2. Instalar MySQL

Una vez configurado y verificado el servidor web Apache, procedo a instalar el sistema gestor de bases de datos **MySQL**, necesario para almacenar y administrar los datos del sitio web.

### 2.1 Instalación del servidor MySQL

Para descargar e instalar el paquete `mysql-server`, ejecuto en la terminal el siguiente comando:

```sudo apt install mysql-server```

![Descripción de la captura](https://github.com/user-attachments/assets/2657c56c-9327-4fcf-a187-5a3665c44b1b)


### 2.2 Ejecutar el script de seguridad (mysql_secure_installation)
Una vez completada la instalación, ejecuto la secuencia de comandos de seguridad interactiva que viene preinstalada con MySQL. Este paso es recomendable para eliminar ajustes predeterminados inseguros y restringir el acceso a la base de datos:

```sudo mysql_secure_installation```

![Descripción de la captura](https://github.com/user-attachments/assets/12a5451d-e2a9-4271-b01a-10d53be09010)

### 2.3 Configuración del plugin de validación de contraseñas (VALIDATE PASSWORD PLUGIN)
Al iniciar el script, la terminal me hace la primera pregunta sobre la activación del plugin de validación de contraseñas:

VALIDATE PASSWORD PLUGIN can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough. Would you like to setup VALIDATE PASSWORD plugin?
Press y|Y for Yes, any other key for No:

![Descripción de la captura](https://github.com/user-attachments/assets/2b5789e9-c8da-4dc8-873f-1b4404c404ac)

Cuando termine, compruebe si puede iniciar sesión en la consola de MySQL al escribir lo siguiente:

```sudo mysql```

![Descripción de la captura](https://github.com/user-attachments/assets/0e3f15f6-3285-4af2-8cbe-c8a0bc4efb97)


















