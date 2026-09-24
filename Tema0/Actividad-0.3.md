# Actividad 0.3 - Práctica Telnet y HTTP

En esta práctica hemos aprendido a comunicarnos de forma manual con un servidor web utilizando el comando `telnet` y el protocolo HTTP, simulando lo que hace un navegador por debajo.

---

## 1. Activación de Telnet (en caso de usar Windows)
Si estás en Windows 10 u 11, antes de nada hay que activar la característica de Telnet desde el panel de control o mediante comandos, ya que viene desactivada por defecto.

---

## 2. Petición GET básica con Telnet
Nos conectamos al servidor indicando la dirección y el puerto 80. Una vez dentro, enviamos el método HTTP y el Host correspondiente (dando dos veces Enter al final).

* **Comando de conexión:**
  `telnet www.profesordeinformatica.com 80`
  *(O usando localhost para pruebas locales)*
  
![Imagen](/Imagenes/Telnet-Part2.PNG)

* **Petición enviada:**
  ```text
  GET / HTTP/1.1
  Host: [www.profesordeinformatica.com](https://www.profesordeinformatica.com)

![Imagen](/Imagenes/Telnet.PNG)
