# Actividad #2 ![Descripción de la captura]()

1. Apache utilizará el puerto 81 además del 80

2. Añadir el dominio “marisma.intranet” en el fichero “hosts”
	
3. Cambia la directiva “ServerTokens” para mostrar el nombre del producto.
	
4. Comprueba si se visualiza el pie de página en las páginas generadas por Apache (por ejemplo, en las páginas de error). Cambia el valor de la directiva “ServerSignature” y comprueba que funciona correctamente. 
	
5. Crea un directorio “prueba” y otro directorio “prueba2”. Incluye un par de páginas en cada una de ellas.
	
6. Redirecciona el contenido de la carpeta “prueba” hacia “prueba2”
	
7. Es posible redireccionar tan solo una página en lugar de toda la carpeta. Pruébalo.
	
8. Usa la directiva userdir
	
9. Usa la directiva alias para redireccionar a una carpeta dentro del directorio de usuario.
	
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

Se modifica la directiva ServerTokens en la configuración de Apache para mostrar el nombre del producto en las respuestas del servidor HTTP. Para ello, se establece el valor Prod, que muestra únicamente la identificación del producto (Apache) y oculta información adicional sobre su versión y configuración.
Para ello entramos en la siguiente carpeta (sudo nano /etc/apache2/conf-available/security.conf) y comprobamos que aparece lo siguiente: ServerTokens Prod (Si no aparece lo añadimos cambiando el que esta)

![Descripción de la captura](https://github.com/user-attachments/assets/da00ee8d-11e4-4b2e-9a80-9198ec1c9e86)


## 4. Modificar la directiva ServerSignature

Se comprueba si Apache muestra un pie de página en las páginas generadas por el servidor, como las páginas de error. Para ello, se modifica la directiva ServerSignature en el archivo security.conf.

ServerSignature On

![Descripción de la captura](https://github.com/user-attachments/assets/cb1bb6e6-87c2-4a46-8d70-70998b0a3bd2)

Con el valor On, Apache muestra información del servidor en el pie de página de las páginas generadas por él. Para comprobarlo, se provoca un error, por ejemplo, accediendo a una URL inexistente.

Después, se cambia el valor a Off para ocultar dicha información y se repite la prueba para verificar que el cambio funciona correctamente.

![Descripción de la captura](https://github.com/user-attachments/assets/75055e06-39d2-4315-b154-1763c0fd580b)























