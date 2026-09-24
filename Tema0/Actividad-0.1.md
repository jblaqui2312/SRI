# Respuestas de la Actividad Web

## 1. ¿Quién, dónde y cuándo se crea el primer servidor web?
* **Quién:** Tim Berners-Lee.
* **Dónde:** En el CERN (Consejo Europeo para la Investigación Nuclear, en Suiza).
* **Cuándo:** En 1990 (ejecutándose en un ordenador NeXT).

---

## 2. ¿Qué es la pila de protocolos usados por HTTP?
HTTP opera sobre la pila de protocolos **TCP/IP**, donde cada capa cumple una función específica:
* **Capa de Aplicación:** HTTP / HTTPS (maneja los datos de la aplicación web).
* **Capa de Transporte:** TCP (asegura una transmisión de datos fiable y ordenada).
* **Capa de Red:** IP (encamina los paquetes de datos por la red).
* **Capa de Enlace / Física:** Se encarga de la transmisión física a través de cables o Wi-Fi.

---

## 3. ¿Componentes de una URL?
Una URL (Localizador Uniforme de Recursos) se compone de los siguientes elementos:
* **Esquema / Protocolo:** Indica cómo comunicarse (ej. `http://` o `https://`).
* **Autoridad (Usuario y Contraseña):** Opcional, para autenticación básica.
* **Host / Dominio:** El nombre del servidor o dirección IP (ej. `www.ejemplo.com`).
* **Puerto:** El puerto de red (por defecto 80 para HTTP y 443 para HTTPS).
* **Ruta (Path):** La ubicación exacta del archivo o recurso en el servidor (ej. `/docs/index.html`).
* **Parámetros / Consulta (Query):** Variables enviadas al servidor (ej. `?id=123&filtro=activo`).
* **Fragmento / Ancla:** Apunta a una sección específica dentro de la página (ej. `#seccion2`).

---

## 4. ¿Pasos en la recuperación de una página web mediante HTTP?
1. **Resolución DNS:** El navegador traduce el nombre de dominio (ej. `google.com`) en una dirección IP numérica.
2. **Conexión TCP:** El cliente establece un canal de comunicación con el servidor mediante el protocolo TCP (Handshake de 3 vías).
3. **Negociación TLS/SSL (si es HTTPS):** Se establece una capa de cifrado segura para proteger los datos.
4. **Petición HTTP (Request):** El navegador envía una solicitud al servidor pidiendo un recurso específico (método `GET`, cabeceras, etc.).
5. **Respuesta HTTP (Response):** El servidor procesa la petición y responde con un código de estado (ej. `200 OK`), las cabeceras y el cuerpo del documento (HTML, imágenes, etc.).
6. **Renderizado:** El navegador interpreta el código recibido y dibuja la página web en pantalla para el usuario.

---

## 5. Diferencia entre páginas dinámicas y estáticas
* **Páginas estáticas:** Su contenido es fijo. El servidor devuelve el archivo HTML, CSS o imagen exactamente igual a como está almacenado en el disco, sin importar quién lo solicite.
* **Páginas dinámicas:** Su contenido se genera "al vuelo". El servidor ejecuta un script (usando tecnologías como PHP, Python, Node.js, etc.) y consulta bases de datos para construir la página personalizada antes de enviarla al cliente.

---

## 6. ¿Cómo usar telnet para acceder a un servidor web?
Para interactuar manualmente con un servidor web utilizando Telnet:
1. Abrir la terminal del sistema e introducir el comando de conexión al puerto 80:
   `telnet <nombre_de_servidor_o_ip> 80`
2. Una vez conectado, enviar una petición HTTP básica introduciendo lo siguiente:
   `GET / HTTP/1.1`
   `Host: <nombre_de_servidor>`
3. Presionar **Enter dos veces** para enviar la petición y ver la respuesta HTML del servidor web.
