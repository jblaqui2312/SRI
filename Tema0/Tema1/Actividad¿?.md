# Activity #4: ProFTPd - FTP privado y anónimo

Lee el punto 2.2 y 2.3 del tema 4 antes de realizar los ejercicios.

### Enlaces
* [ProFTPd Doc. Index](http://www.proftpd.org/docs/howto/index.html)
* [ProFTPd Directives](http://www.proftpd.org/docs/directives/index.html)
* [Module mod_core - Directory](http://www.proftpd.org/docs/modules/mod_core.html#Directory)
* [Module mod_core - Limit](http://www.proftpd.org/docs/modules/mod_core.html#Limit)
* [ProFTPd example configuration - Anonymous](http://www.proftpd.org/docs/configs/anonymous.conf)

--- ![Descripción de la imagen]()

## Actividades

### Pasos previos

Instalamos Proftpd

![Descripción de la imagen](<img width="1083" height="551" alt="image" src="https://github.com/user-attachments/assets/86817c28-6d53-44f5-90d6-dda5bfa698d9" />
)

### 1. Configura proftpd para que los usuarios accedan al directorio `/home/ftp` (puedes usar DefaultChdir). ¿Cual es la diferencia entre DefaultRoot y DefaultChdir?

Primero entramos en esta carpeta

![Descripción de la imagen](<img width="1084" height="580" alt="image" src="https://github.com/user-attachments/assets/80bc067c-450d-4fe6-bb22-31d903c5d7ed" />)

```apache
DefaultChdir /home/ftp
```
![Descripción de la imagen](<img width="1091" height="584" alt="image" src="https://github.com/user-attachments/assets/f3ded5ac-49bc-441a-b718-008922aef014" />
)

Guardamos y salimos del archivo

-DefaultChdir: Define el directorio de trabajo inicial en el que se posiciona el usuario justo después de autenticarse, pero le permite navegar hacia otros directorios del sistema si los permisos del sistema operativo lo permiten.

-DefaultRoot: Actúa como una jaula de seguridad (chroot), limitando la raíz virtual del usuario a esa ruta específica e impidiendo por completo que pueda salir de ella o navegar hacia directorios superiores.

### 2. Prohibir subir o eliminar archivos en la carpeta ftp

Para asegurar que los usuarios no puedan escribir, subir (STOR, APPE) ni borrar (DELE, RMD) contenido dentro de la carpeta, debes restringir el permiso WRITE mediante un bloque <Directory>:

```
Apache
<Directory /home/ftp>
    <Limit WRITE>
        DenyAll
    </Limit>
</Directory>
```
![Descripción de la imagen]()


### 3. Configurar el acceso de usuario anónimo

Para habilitar el acceso anónimo apuntando al directorio /home/ftp, utiliza un bloque <Anonymous>:

```
Apache
<Anonymous /home/ftp>
    User ftp
    Group nogroup
    UserAlias anonymous ftp
    
    # Opcional: permite iniciar sesión sin contraseña estricta de correo electrónico
    AnonRequirePassword off

    <Limit LOGIN>
        AllowAll
    </Limit>
</Anonymous>
```

![Descripción de la imagen]()

### 4. Permitir escritura al usuario anónimo solo desde la red 10.6.0.x

Para cumplir con esta condición, debes configurar las reglas de control de acceso (Order, Allow, Deny) dentro del límite de escritura (WRITE) exclusivo del bloque anónimo:

```
Apache
<Anonymous /home/ftp>
    User ftp
    Group nogroup
    UserAlias anonymous ftp

    # Configuración por defecto para lectura/navegación
    <Limit READ>
        AllowAll
    </Limit>

    # Permitir escritura exclusivamente a la red 10.6.0.x y denegarla al resto
    <Limit WRITE>
        Order allow,deny
        Allow from 10.6.0.
        Deny from all
    </Limit>
</Anonymous>
```

![Descripción de la imagen]()



































