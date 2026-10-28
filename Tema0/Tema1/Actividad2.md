# Actividad #2 ![Descripción de la captura]()

1. Apache utilizará el puerto 81 además del 80

2. Añadir el dominio “marisma.intranet” en el fichero “hosts”
	
3. Cambia la directiva “ServerTokens” para mostrar el nombre del producto
	
4. Comprueba si se visualiza el pie de página en las páginas generadas por Apache (por ejemplo, en las páginas de error). Cambia el valor de la directiva “ServerSignature” y comprueba que funciona correctamente
	
5. Crea un directorio “prueba” y otro directorio “prueba2”. Incluye un par de páginas en cada una de ellas
	
6. Redirecciona el contenido de la carpeta “prueba” hacia “prueba2”
	
7. Es posible redireccionar tan solo una página en lugar de toda la carpeta. Pruébalo
	
8. Usa la directiva userdir
	
9. Usa la directiva alias para redireccionar a una carpeta dentro del directorio de usuario
	
10. ¿Para qué sirve la directiva Options y dónde aparece. Comprueba si apache indexa los directorios. Si es así, ¿cómo lo desactivamos?

## 1. Configurar Apache para usar el puerto 81 además del 80

El archivo correcto es /etc/apache2/ports.conf. Por defecto suele tener Listen 80. Para añadir el puerto 81 sin quitar el 80, debes mantener ambas líneas:

Listen 80
Listen 81

![Descripción de la captura](https://github.com/user-attachments/assets/af181101-4a3a-4a64-8eb0-d57e2d1ff3cb)

## 2. Añadir el dominio “marisma.intranet” en el fichero “hosts”

El archivo se llama /etc/hosts. Además, el dominio debe ir junto marisma.intranet

Abre el archivo con permisos de administrador:

sudo nano /etc/hosts

![Descripción de la captura](https://github.com/user-attachments/assets/3420757e-68d4-4390-9afb-0d9e3c36907e)

Y añade la siguiente línea al final:

127.0.0.1   marisma.intranet

![Descripción de la captura](https://github.com/user-attachments/assets/16df8fe4-aea9-4e44-be69-7e43cd054c2e)


## 3. Modificar la directiva ServerTokens

Se modifica la directiva ServerTokens en la configuración de Apache para mostrar el nombre del producto en las respuestas del servidor HTTP. Para ello, se establece el valor Prod, que muestra únicamente la identificación del producto (Apache) y oculta información adicional sobre su versión y configuración
Para ello entramos en la siguiente carpeta (sudo nano /etc/apache2/conf-available/security.conf) y comprobamos que aparece lo siguiente: ServerTokens Prod (Si no aparece lo añadimos cambiando el que esta)

![Descripción de la captura](https://github.com/user-attachments/assets/da00ee8d-11e4-4b2e-9a80-9198ec1c9e86)


## 4. Modificar la directiva ServerSignature

Se comprueba si Apache muestra un pie de página en las páginas generadas por el servidor, como las páginas de error. Para ello, se modifica la directiva ServerSignature en el archivo security.conf

ServerSignature On

![Descripción de la captura](https://github.com/user-attachments/assets/cb1bb6e6-87c2-4a46-8d70-70998b0a3bd2)

Con el valor On, Apache muestra información del servidor en el pie de página de las páginas generadas por él. Para comprobarlo, se provoca un error, por ejemplo, accediendo a una URL inexistente

Después, se cambia el valor a Off para ocultar dicha información y se repite la prueba para verificar que el cambio funciona correctamente

![Descripción de la captura](https://github.com/user-attachments/assets/75055e06-39d2-4315-b154-1763c0fd580b)


## 5. Crear los directorios prueba y prueba2

Se crean dos directorios dentro del sitio web de Apache, llamados prueba y prueba2. En cada uno se incluyen dos páginas HTML para comprobar que el servidor puede acceder a su contenido

![Descripción de la captura](https://github.com/user-attachments/assets/a754fea7-f177-41bd-b415-2cd7057fed85)

![Descripción de la captura](https://github.com/user-attachments/assets/c10f6bdb-c0f8-46dc-bd91-ec0ed7309ce3)

## 6. Redireccionar el contenido de prueba hacia prueba2

Se configura Apache para redirigir las peticiones realizadas al directorio prueba hacia prueba2. De esta forma, al acceder a una página de prueba, el navegador se dirige al directorio de destino
En la carpeta de la imagen usando "sudo nano" para entrar. En lo ultimo escribimos "Redirect /prueba /prueba2"
![Descripción de la captura](https://github.com/user-attachments/assets/926cda0b-bc83-4425-8353-c3cec0f9dbb2)

Luego de eso usamos el comando "Sudo systemctl restart apache2" para reiniciar el servicio


## OJO!!!

Hay que ejecutar el siguiente comando para activar la virtualizacion

![Descripción de la captura](https://github.com/user-attachments/assets/78338913-5a5a-46a1-9a3b-beae05e9d907)


## 7. Redirección de una página específica

Es posible acotar la redirección para que afecte únicamente a un archivo concreto en lugar de a todo un directorio completo. 

* **Configuración aplicada:**
  ```apache
  Redirect /prueba/pagina.html /prueba2/nueva_pagina.html

Previamente, en el navegador, comprobamos que nos sale al ejecutar la pagina

![Descripción de la captura](https://github.com/user-attachments/assets/7cf6fb16-093f-42ff-b1f6-47c3e55760f7)

Creamos las carpetas que vamos a modificar

![Descripción de la captura](https://github.com/user-attachments/assets/d894c647-8648-49c7-ac14-fdd70ecd5131)

Ahora si, nos vamos de nuevo al archivo de configuración (/etc/apache2/apche2.conf) y modificamos esa linea mencionada con anterioridad

![Descripción de la captura](https://github.com/user-attachments/assets/40d530b3-ecbf-4bf5-b7e8-9e330d02a282)

Con eso ya puesto, nos vamos al navegador y lo comprobamos 

![Descripción de la captura](https://github.com/user-attachments/assets/ee390bcb-8610-41c4-baf0-d67f5c7bbbb2)

## 8. Habilitación y configuración del módulo Userdir (`userdir`)

Se configuró el módulo `userdir` de Apache para permitir que los usuarios del sistema operativo puedan alojar y servir páginas web personales desde sus propios directorios home.

Pasos realizados:
1. **Activación del módulo:** Se habilitó `userdir` en el servidor web mediante la terminal:
   ```bash
   sudo a2enmod userdir

![Descripción de la captura](https://github.com/user-attachments/assets/e3fde0e8-9bc1-4fd9-a444-5f846611c961)

Reiniciamos Apache
Creamos una carpeta de prueba para nuestro usuario

![Descripción de la captura](https://github.com/user-attachments/assets/56bfe509-159a-43ce-8c58-ae925e45c915)

Creamos un archivo index

![Descripción de la captura](https://github.com/user-attachments/assets/d2acc001-7a0d-4916-b93b-5af0603ec581)

Y comprobamos que funciona al escribir en el navegador "http://localhost/~tu_usuario/"

![Descripción de la captura](https://github.com/user-attachments/assets/c08da326-aeeb-4a3c-a5a8-5c0cfbb82b10)

## OJO!!!

Si no te llega a cargar y te sale el error "Forbidden" es porque dicho usuario o carpeta no tiene lo suficientes permisos por lo cual hacemos lo siguiente

![Descripción de la captura](https://github.com/user-attachments/assets/05bacc7e-b3b4-4427-8418-230b1a0f0b61)

## 9. Uso de la directiva Alias hacia el directorio de usuario
La directiva Alias permite mapear URLs específicas a directorios físicos que se encuentran fuera del directorio raíz principal del servidor web (DocumentRoot). En este caso, la utilizaremos para redirigir una ruta web hacia una carpeta concreta dentro del directorio de un usuario del sistema.

Modificación del archivo de configuración:
Nos dirigimos al archivo de configuración de Apache (por ejemplo, en /etc/apache2/apache2.conf o dentro de los sitios habilitados en /etc/apache2/sites-available/000-default.conf) para añadir la directiva Alias.

![Descripción de la captura](https://github.com/user-attachments/assets/c190ac5d-a868-4d32-8eb0-f97c0cedaa27)

Reiniciar el servidor web:
Para aplicar los cambios realizados en la configuración de Apache, reiniciamos el servicio mediante la terminal:

![Descripción de la captura](https://github.com/user-attachments/assets/f942b325-24c6-46e5-b81a-47f6efcaf45e)

Comprobación en el navegador:
Abrimos el navegador web y accedemos a la ruta configurada (http://localhost/mi_alias) para verificar que el contenido de la carpeta del usuario se muestra correctamente.


![Descripción de la captura](https://github.com/user-attachments/assets/582a00f4-e8ce-446a-8ab7-a69d28f6179c)


## 10. Uso y configuración de la directiva Options

¿Para qué sirve la directiva `Options` y dónde aparece? Comprueba si Apache indexa los directorios. Si es así, ¿cómo lo desactivamos?

* **¿Para qué sirve la directiva `Options`?**
  Sirve para controlar qué características o funcionalidades del servidor web están activadas o desactivadas en un directorio específico. Permite configurar aspectos como el seguimiento de enlaces simbólicos, la ejecución de scripts o la visualización del listado de archivos.

* **¿Dónde aparece?**
  Aparece dentro de los bloques de configuración de directorios de Apache, específicamente delimitada por etiquetas como `<Directory>` o `<DirectoryMatch>` (por ejemplo, en el archivo `/etc/apache2/sites-available/000-default.conf` o en un archivo `.htaccess`).

![Descripción de la captura](https://github.com/user-attachments/assets/c1e6d20c-2637-43ad-8288-de4148e88642)

* **Comprobar si Apache indexa los directorios:**
  Puedes comprobarlo fácilmente si entras desde el navegador a una carpeta de tu servidor web que **no** contenga ningún archivo principal de inicio (como `index.html` o `index.php`). Si Apache te muestra en pantalla una lista con los ficheros y subcarpetas que contiene ese directorio en lugar de un error de acceso denegado, significa que **sí está indexando** los directorios.

![Descripción de la captura](https://github.com/user-attachments/assets/ad98c809-9e16-44b4-9ada-0e06156a3c9c)

* **¿Cómo lo desactivamos?**
  Para deshabilitar la indexación automática y evitar que los usuarios puedan ver el contenido de las carpetas, debes anteponer un signo menos a la opción (`-Indexes`). 

  Debe quedar configurado de la siguiente manera en tu archivo de Apache:

``apache
<Directory /home/josemariabq/mi_carpeta>
    Options -Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>
``

![Descripción de la captura](https://github.com/user-attachments/assets/82fa6766-47ae-4b5f-918a-ab4d4f2e4037)







