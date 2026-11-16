# Actividad #2

Busca información sobre las siguientes directivas. Indica para qué se usan y escribe un ejemplo que hayas encontrado.

---

### `<IfModule>`
Es una sección en la que escribimos directivas condicionadas por la presencia de un módulo.

* **Enlace:** https://httpd.apache.org/docs/2.4/mod/core.html#ifmodule

```apache
# /etc/apache2/ports.conf
<IfModule ssl_module>
    Listen 443
</IfModule>
```

---

### `LoadModule`
Carga un módulo Apache.

* **Enlace:** https://httpd.apache.org/docs/2.4/mod/mod_so.html#loadmodule

```apache
# /etc/apache2/mods-enabled/alias.load
LoadModule alias_module /usr/lib/apache2/modules/mod_alias.so
```

---

### `Include`
Permite la inclusión de archivos de configuración.

* **Enlace:** https://httpd.apache.org/docs/2.4/mod/core.html#include

```apache
# /etc/apache2/apache2.conf
Include ports.conf
```

---

### `<Directory>`
Se utilizan para incluir directivas que afectarán a un directorio y los subdirectorios incluidos en él.

* **Enlace:** https://httpd.apache.org/docs/2.4/mod/core.html#directory

```apache
# /etc/apache2/apache2.conf
<Directory/>
    Options FollowSymLinks
    AllowOverride None
    Require all denied
</Directory>
```

---

### `<Files>`
Se usan para incluir directivas que afectará a un fichero o grupo de ficheros (usando caracteres comodín).

* **Enlace:** https://httpd.apache.org/docs/2.4/mod/core.html#files

```apache
# /etc/apache2/apache2.conf
<FilesMatch "^\.ht">
    Require all denied
</FilesMatch>
```

---

### `<Location>`
Se utilizan para incluir directivas que afectarán a una URL.

* **Enlace:** https://httpd.apache.org/docs/2.4/mod/core.html#location

```apache
# /etc/apache2/mods-enabled/status.conf
<Location /server-status>
    SetHandler server-status
    Require local
    #Require ip 192.0.2.0/24
</Location>
```

---

### `<VirtualHost>`
Se utilizan para incluir directivas que afectarán a un servidor virtual.

* **Enlace:** https://httpd.apache.org/docs/2.4/mod/core.html#virtualhost

```apache
# /etc/apache2/sites-enabled/000-default.conf
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/html
</VirtualHost>
```

---

### ¿Qué son los ficheros `.htaccess`?
Proporcionan un mecanismo para hacer cambios en la configuración por directorios.

* **Enlace:** https://httpd.apache.org/docs/2.4/howto/htaccess.html
