# Actividad #3

![Descripcion de la imagen]()

Previamente se recomienda leer:
* [Apache How-To: Access Control](https://httpd.apache.org/docs/2.4/howto/access.html)
* [Apache mod_authz_host: Require Directives](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#requiredirectives)
* [The Art of Web: Apache Authorization](https://www.the-art-of-web.com/system/apache-authorization/)

---

## Ejercicios

### 1. Crea un directorio llamado "dir1" y otro llamado "dir2"

Para crear los directorios indicados, puedes utilizar el siguiente comando en la terminal:

```bash
mkdir dir1 dir2
```
![Descripcion de la imagen](https://github.com/user-attachments/assets/cef635d2-6e36-4662-979b-d2bd9ed622af)

### 2. Diferencia entre los bloques de control de acceso y su equivalencia con Require

Primer bloque (Order Deny,Allow):
Se evalúan primero las directivas Deny y luego las Allow. Dado que Deny from All deniega el acceso a todos, pero la regla Allow from 192.168.1.100 permite la entrada a esa IP específica sobrescribiendo la denegación previa, el resultado es que solo se permite el acceso a la IP 192.168.1.100.

Equivalencia en Apache 2.4 (Require):

Apache
Require ip 192.168.1.100
Segundo bloque (Order Allow,Deny):
Se evalúan primero las directivas Allow y a continuación las Deny. Como la directiva Deny from All se aplica al final y bloquea a todo el mundo, el resultado es que se deniega el acceso a absolutamente todos los usuarios (nadie puede entrar).

Equivalencia en Apache 2.4 (Require):

```Apache
Require all denied
```

### 3. Configuración para el directorio `dir1`

Para aplicar estas restricciones al directorio `dir1`, utilizamos bloques `<Directory>` empleando las directivas `Require` de Apache 2.4:

#### a. Permite el acceso de las peticiones provenientes de `10.3.0.100`

```apache
<Directory /var/www/html/dir1>
    Require ip 10.3.0.100
</Directory>
```
Nos metemos en la siguiente carpeta:
```bash
sudo nano /etc/apache2/sites-available/000-default.conf
```

Lo pegamos dentro del bloque principal <VirtualHost *:80>, justo antes de la línea de cierre 

![Descripcion de la imagen](https://github.com/user-attachments/assets/9e67a022-83e8-49b8-863d-ccfb4aed883a)

#### b. Permite el acceso desde "marisma.intranet"

```
<Directory /var/www/html/dir1>
    Require host marisma.intranet
</Directory>
```

![Descripcion de la imagen](https://github.com/user-attachments/assets/023ead58-47fc-4979-824d-07114e25faf1)

#### c. Permite el acceso desde cualquier subdominio de "marisma.intranet"

```
<Directory /var/www/html/dir1>
    Require host .marisma.intranet
</Directory>
```
![Descripcion de la imagen](https://github.com/user-attachments/assets/3147ddc9-02bf-485b-912a-494c20797f1e)

#### d. Permite el acceso de las peticiones provenientes de 10.3.0.100 con máscara 255.255.0.0

```
<Directory /var/www/html/dir1>
    Require ip 10.3.0.100/255.255.0.0
</Directory>
```
![Descripcion de la imagen](https://github.com/user-attachments/assets/0957460b-ffa6-48e4-9c08-9e36b8713fdc)

Se vería tal que asi:

![Descripcion de la imagen](https://github.com/user-attachments/assets/57cadb64-1554-4500-be6e-7365e52c1a3e)

### 3. Configuración para el directorio `dir1` (Formato clásico y equivalencia moderna)

#### a. Permite el acceso de las peticiones provenientes de 10.3.0.100
```
Allow from 10.3.0.100 
// equivalente a 
Require ip 10.3.0.100
```
#### b. Permite el acceso desde "marisma.intranet"
```
Allow from marisma.intranet  
// equivalente a 
Require host marisma.intranet
```
#### c. Permite el acceso desde cualquier subdominio de "marisma.intranet"
```
Allow from .marisma.intranet  
// equivalente a 
Require host .marisma.intranet
```
#### d. Permite el acceso de las peticiones provenientes de "10.3.0.100" con máscara "255.255.0.0"
```
Allow from 10.3.0.100/255.255.0.0  
// equivalente a 
Require ip 10.3.0.100/255.255.0.0
```
































