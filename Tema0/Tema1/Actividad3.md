## Actividad #1

Busca información sobre las siguientes directivas y el valor que toman por defecto y el lugar donde se encuentra definida.

### Directivas de identificación

* **ServerName**: 
* **ServerAdmin**: 
* **ServerTokens**: 

### Directivas de localización de ficheros

* **DocumentRoot**: 
* **ErrorLog**: 
* **CustomLog**: 
* **ServerRoot**: 

### Directivas de control de la conexión

* **Timeout**: 
* **KeepAlive**: 
* **MaxKeepAliveRequests**: 
* **KeepAliveTimeout**: 

### Otras

* **LogLevel**: 
* **LogFormat**: 

---

## Solución

### Directivas de identificación

* **ServerName**: Nombre del servidor y puerto.  
  * *Ubicación:* `#sites-enabled/000-default.conf`
  * *Valor por defecto:* `www.example.com` (o comentado por defecto)

* **ServerAdmin**: Email del administrador de Apache.
  * *Ubicación:* `#sites-enabled/000-default.conf`
  * *Valor por defecto:* `webmaster@localhost`

* **ServerTokens**: Información a incluir en las cabeceras de respuesta HTTP.
  * *Ubicación:* `#apache2.conf` (o `security.conf`)
  * *Valor por defecto:* `Full` (en algunas distros puede ser `OS` o `Minimal`)

---

### Directivas de localización de ficheros

* **DocumentRoot**: Establece el directorio raíz donde se servirán los documentos web.
  * *Ubicación:* `#sites-enabled/000-default.conf`
  * *Valor por defecto:* `/var/www/html`

* **ErrorLog**: Archivo de registro (bitácora) donde se almacenan los errores.
  * *Ubicación:* `#sites-enabled/000-default.conf`
  * *Valor por defecto:* `${APACHE_LOG_DIR}/error.log`  
    *(Nota: `APACHE_LOG_DIR` está definida en `/etc/apache2/envvars`, ej. `export APACHE_LOG_DIR=/var/log/apache2`)*

* **CustomLog**: Archivo de registro de accesos.
  * *Ubicación:* `#sites-enabled/000-default.conf`
  * *Valor por defecto:* `${APACHE_LOG_DIR}/access.log combined`

* **ServerRoot**: Directorio principal donde está alojado el servidor y su configuración.
  * *Ubicación:* `#apache2.conf`
  * *Valor por defecto:* `/etc/apache2`

---

### Directivas de control de la conexión

* **Timeout**: Cantidad de tiempo que el servidor esperará a que ocurran determinados eventos antes de cerrar una petición.
  * *Ubicación:* `#apache2.conf`
  * *Valor por defecto:* `60` (o `300` en versiones muy antiguas)

* **KeepAlive**: Permite que se puedan enviar múltiples peticiones sobre la misma conexión TCP.
  * *Ubicación:* `#apache2.conf`
  * *Valor por defecto:* `On`

* **MaxKeepAliveRequests**: Limita el número de peticiones permitidas por conexión persistente.
  * *Ubicación:* `#apache2.conf`
  * *Valor por defecto:* `100`

* **KeepAliveTimeout**: Tiempo que el servidor esperará peticiones subsiguientes en conexiones persistentes.
  * *Ubicación:* `#apache2.conf`
  * *Valor por defecto:* `5`

---

### Otras

* **LogLevel**: Indica el nivel de detalle (verbosidad) de los mensajes registrados en el ErrorLog.
  * *Ubicación:* `#apache2.conf`
  * *Valor por defecto:* `warn`

* **LogFormat**: Define el formato del fichero de bitácora asignándole un apodo (nickname).
  * *Ubicación:* `#apache2.conf`
  ```apache
  LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
  LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
  LogFormat "%h %l %u %t \"%r\" %>s %O" common
  LogFormat "%{Referer}i -> %U" referer
  LogFormat "%{User-agent}i" agent
