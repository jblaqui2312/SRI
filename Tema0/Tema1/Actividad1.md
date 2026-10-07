# Actividad #1
![Descripción de la captura]()
Lee el siguiente artículo e instala Apache en Ubuntu:
https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-20-04-es

## 1.Instalar Apache y actualizar el firewall

Para comenzar con la configuración del servidor web en mi máquina Ubuntu, en primer lugar procedo a actualizar la lista de paquetes del gestor `apt` e instalar el paquete correspondiente a Apache

### 1.1. Actualizar el índice de paquetes

Ejecuto el siguiente comando para asegurarme de obtener la información más reciente de los repositorios:

```sudo apt update```

### Capturas de pantalla
![Descripción de la captura](https://github.com/user-attachments/assets/5fbb0742-b567-45cd-9371-7c372f6fb060)

```sudo apt install apache2```

### Capturas de pantalla
![Descripción de la captura](https://github.com/user-attachments/assets/e215c018-91ee-4cb5-afcf-5c69ff83210c)


## 1.2 Configuración del firewall (UFW)

Una vez completada la instalación de Apache, procedo a ajustar la configuración del firewall (`ufw`) para permitir el tráfico web

### 1.2.1 Listar los perfiles de aplicaciones disponibles en UFW

Para verificar qué perfiles de aplicación reconoce el firewall, ejecuto el siguiente comando:

```sudo ufw app list```

### Capturas de pantalla
![Descripción de la captura](https://github.com/user-attachments/assets/78b6c657-bc84-4a38-a418-0f0a1d9726d6)

### 1.2.2 Análisis de los perfiles de Apache
Analizo las opciones disponibles para seleccionar la más adecuada:

Apache: Abre únicamente el puerto 80 (tráfico web HTTP no cifrado)

Apache Full: Abre el puerto 80 (HTTP) y el puerto 443 (tráfico cifrado HTTPS con TLS/SSL)

Apache Secure: Abre únicamente el puerto 443 (HTTPS cifrado)

Dado que acabo de realizar la instalación base de Apache y aún no dispongo de un certificado TLS/SSL configurado, selecciono el perfil Apache para permitir el tráfico por el puerto 80


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

Para acceder a la página web predeterminada de Apache desde un navegador, procedo a obtener la dirección IP pública de mi servidor

### 1.3.1. Obtener la IP mediante las herramientas del sistema (`iproute2`)

En primer lugar, consulto la dirección IP asignada a la interfaz de red ejecutan el siguiente comando:

```ip addr show eth0 | grep inet | awk '{ print $2; }' | sed 's/\/.*$//'```

![Descripción de la captura](https://github.com/user-attachments/assets/d2877061-f875-4de7-b444-ffcd96470ce0)

## 2. Instalar MySQL

Una vez configurado y verificado el servidor web Apache, procedo a instalar el sistema gestor de bases de datos **MySQL**, necesario para almacenar y administrar los datos del sitio web

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


# 3. Instalación de PHP

Ya contamos con Apache para la interfaz visual y MySQL para la gestión de la información. Ahora incorporamos PHP, encargado de ejecutar el código para generar páginas dinámicas

Para lograrlo, instalamos el paquete principal junto con dos complementos indispensables: `libapache2-mod-php` (para que Apache interprete archivos PHP) y `php-mysql` (para conectar PHP con la base de datos)

Ejecutamos el siguiente comando en la terminal:

\`\`\`bash
sudo apt install php libapache2-mod-php php-mysql
\`\`\`


![Descripción de la captura](https://github.com/user-attachments/assets/253e83de-3c76-4560-9af0-5ce773ac53a8)

## 3.1 Comprobación de la Instalación de PHP

Una vez finalizada la instalación, podemos verificar que todo funcione correctamente y comprobar la versión instalada ejecutando el siguiente comando en la terminal:

\`\`\`bash
php -v
\`\`\`


![Descripción de la captura](https://github.com/user-attachments/assets/5fdbf2e2-eb4e-4af4-9377-94481843c785)


# 4. Creación de un Host Virtual para el Sitio Web

Apache permite utilizar hosts virtuales para gestionar múltiples dominios desde un mismo servidor. En esta guía emplearemos `JMBQ` como ejemplo (debes cambiarlo por tu dominio real).

Ubuntu 20.04 incluye un sitio web predeterminado en `/var/www/html`. Para evitar modificarlo y facilitar la administración de varios sitios, crearemos una nueva estructura de carpetas dentro de `/var/www` para nuestro dominio, manteniendo la carpeta predeterminada solo como respaldo.

Creamos la carpeta correspondiente para el dominio utilizando el siguiente comando:

\`\`\`bash
sudo mkdir /var/www/JMBQ
\`\`\`


![Descripción de la captura](https://github.com/user-attachments/assets/5c54cc5e-1da6-4c5c-915e-045f8de5528b)

Luego, asignamos la propiedad del directorio a nuestro usuario actual mediante la variable de entorno `$USER`:

\`\`\`bash
sudo chown -R $USER:$USER /var/www/JMBQ
\`\`\`


![Descripción de la captura](https://github.com/user-attachments/assets/8aea3bf2-fe2b-4751-8969-5373a5a32493)

Abrimos un nuevo archivo de configuración dentro del directorio `sites-available` de Apache utilizando el editor `nano`:

\`\`\`bash
sudo nano /etc/apache2/sites-available/JMBQ.conf
\`\`\`


![Descripción de la captura](https://github.com/user-attachments/assets/5c8f978e-c6a9-45d4-a048-2a78692e43e8)

Esto abrirá un archivo en blanco donde pegaremos la siguiente estructura de configuración básica:


![Descripción de la captura](https://github.com/user-attachments/assets/26d5cbe3-679d-4a86-ae7c-bb3f41a32b25)

Con esta configuración le indicamos a Apache que sirva el sitio desde la ruta `/var/www/JMBQ`. Si deseas realizar pruebas sin un dominio configurado, puedes comentar las líneas `ServerName` y `ServerAlias` agregando un símbolo `#` al inicio.

A continuación, habilitamos el nuevo host virtual con el comando `a2ensite`:

\`\`\`bash
sudo a2ensite JMBQ
\`\`\`


![Descripción de la captura](https://github.com/user-attachments/assets/34f5f097-3831-4c1c-a3e5-168ce9758048)

Si no empleas un nombre de dominio personalizado, es obligatorio desactivar el sitio predeterminado de Apache para evitar que sobrescriba nuestra configuración. Para ello, ejecutamos:

\`\`\`bash
sudo a2dissite 000-default
\`\`\`


![Descripción de la captura](https://github.com/user-attachments/assets/2aa662e0-f438-4593-a38e-d8fb37972e00)

Verificar y Aplicar la Configuración
Antes de reiniciar el servidor, es fundamental comprobar que la configuración de Apache no tenga errores de sintaxis:

\`\`\`bash
sudo apache2ctl configtest
\`\`\`


![Descripción de la captura](https://github.com/user-attachments/assets/9d55b1b9-d136-473b-a6b8-3afa052081bd)

Si todo es correcto, recarga el servicio de Apache para aplicar los cambios:

\`\`\`bash
sudo systemctl reload apache2
\`\`\`


![Descripción de la captura](https://github.com/user-attachments/assets/9bffbb1c-6d62-4ae1-aa73-9bc660c03308)

Crear la Página de Prueba
El sitio web ya está activo, pero el directorio raíz (\`/var/www/JMBQ\`) está vacío. Crea un archivo \`index.html\` para verificar que el host virtual funciona correctamente:

\`\`\`bash
sudo nano /var/www/JMBQ/index.html
\`\`\`


![Descripción de la captura](https://github.com/user-attachments/assets/b65cc4b3-18e9-4558-8abe-3bcc334e65c6)

Añade el siguiente código HTML de prueba dentro del archivo:

\`\`\`html
<h1>It works!</h1>
<p>This is the landing page of <strong>JMBQ</strong>.</p>
\`\`\`


![Descripción de la captura](https://github.com/user-attachments/assets/a00ddfaf-0d74-411b-8f44-a88782d26544)


Verificar en el Navegador
Una vez realizados los pasos anteriores, abre tu navegador web y escribe el nombre de dominio o la dirección IP de tu servidor para comprobar que todo funciona correctamente:

\`\`\`text
http://server_domain_or_IP
\`\`\`


![Descripción de la captura](https://github.com/user-attachments/assets/8cdbacbe-9618-44a5-b577-6dd3a4f2c056)


Configurar la Prioridad de Archivos (DirectoryIndex)
Si deseas cambiar el comportamiento predeterminado de cómo Apache sirve los archivos de inicio (por ejemplo, para que priorice \`index.php\` sobre \`index.html\`), edita el archivo de configuración del módulo:

\`\`\`bash
sudo nano /etc/apache2/mods-enabled/dir.conf
\`\`\`


![Descripción de la captura](https://github.com/user-attachments/assets/b28ae81d-968b-4152-98fd-1144b7ff36b3)

Asegúrate de que el orden de los archivos en la directiva \`DirectoryIndex\` quede configurado de la siguiente manera:

\`\`\`apache
<IfModule mod_dir.c>
        DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>
\`\`\`


![Descripción de la captura](https://github.com/user-attachments/assets/5e0dda03-b9f0-4b91-afdd-9e60f653413d)

Una vez guardados y cerrados los cambios, recarga Apache para aplicarlos:

\`\`\`bash
sudo systemctl reload apache2
\`\`\`


# 5. Probar el procesamiento de PHP en su servidor web

Ahora que dispone de una ubicación personalizada para alojar los archivos y las carpetas de su sitio web, crearemos una secuencia de comandos PHP de prueba para verificar que Apache pueda gestionar solicitudes y procesar solicitudes de archivos PHP.
Cree un archivo nuevo llamado info.php dentro de su carpeta root web personalizada:

\`\`\`bash
nano /var/www/JMBQ/info.php
\`\`\`


![Descripción de la captura](<img width="889" height="117" alt="image" src="https://github.com/user-attachments/assets/5ddaa780-0a00-465f-9535-3c9eb9a689f5" />
)

Con esto se abrirá un archivo vacío. Añada el siguiente texto, que es el código PHP válido, dentro del archivo:

\`\`\`php
/var/www/JMBQ/info.php
<?phpphpinfo();
\`\`\`


![Descripción de la captura](<img width="898" height="122" alt="image" src="https://github.com/user-attachments/assets/ce433049-e235-42aa-8313-cb4d03a2a889" />
)

Cuando termine, guarde y cierre el archivo.
Para probar esta secuencia de comandos, diríjase a su navegador web y acceda al nombre de dominio o la dirección IP de su servidor, seguido del nombre de la secuencia de comandos, que en este caso es info.php:

\`\`\`text
http://server_domain_or_IP/info.php
\`\`\`

Verá una página similar a la siguiente:


![Descripción de la captura](<img width="1006" height="604" alt="image" src="https://github.com/user-attachments/assets/42f7dd39-d8f3-45bc-a915-89b5570350dd" />
)

Tras comprobar la información pertinente sobre su servidor PHP a través de esa página, es recomendable que elimine el archivo que creó

\`\`\`bash
sudo rm /var/www/JMBQ/info.php
\`\`\`


![Descripción de la captura](<img width="503" height="45" alt="image" src="https://github.com/user-attachments/assets/9a13d554-e59c-44e1-9a0d-5f28e814233b" />
)












