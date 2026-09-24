# Diferencias y Funcionamiento de TCP y UDP

## 1. Diferencias entre UDP y TCP
* **TCP (Transmission Control Protocol):** Es un protocolo **orientado a conexión** y muy fiable. Se asegura de que los paquetes de datos lleguen completos y en el orden correcto. Si se pierde un paquete por el camino, lo solicita de nuevo, lo que lo hace un poco más lento pero completamente seguro.
* **UDP (User Datagram Protocol):** Es un protocolo **no orientado a conexión** y no fiable. Envía los datos rápidamente sin comprobar si el receptor los ha recibido o si llegan en orden. Es mucho más veloz, perfecto para situaciones donde la velocidad importa más que una pequeña pérdida de datos.

---

## 2. Aplicaciones que usan TCP
Al necesitar máxima seguridad y precisión para que no falte ningún dato, estas aplicaciones utilizan TCP:
* **HTTP / HTTPS:** Navegación por páginas web.
* **SMTP, POP e IMAP:** Envío y recepción de correo electrónico.
* **SSH:** Conexión y control remoto seguro a servidores.

---

## 3. Aplicaciones que usan UDP
Se emplean en servicios donde la prioridad es la velocidad en tiempo real y se puede tolerar la pérdida puntual de algún paquete:
* **DNS:** Consultas rápidas para traducir nombres de dominio a direcciones IP.
* **Streaming de video y audio:** Emisiones en directo o videollamadas.
* **Juegos en línea:** Para evitar retrasos en las acciones instantáneas.

---

## 4. ¿Qué capa almacena el puerto?
El puerto se almacena en la **Capa de Transporte**. Su función es identificar a qué aplicación o servicio específico va dirigido el dato dentro del equipo.

---

## 5. ¿Qué capa almacena la dirección IP?
La dirección IP se almacena en la **Capa de Red**. Se encarga del direccionamiento y de encontrar la mejor ruta para que los paquetes viajen a través de distintas redes hasta su destino.

---

## 6. ¿Qué es el three-way handshake?
Es el proceso de **intercambio de tres pasos** que realiza TCP para establecer una conexión fiable entre el cliente y el servidor antes de empezar a transmitir datos:
1. **SYN:** El cliente envía un mensaje para iniciar la conexión.
2. **SYN-ACK:** El servidor responde aceptando la petición y confirmando su estado.
3. **ACK:** El cliente confirma la respuesta del servidor y la conexión queda abierta oficialmente.
