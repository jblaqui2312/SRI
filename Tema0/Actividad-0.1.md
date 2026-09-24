# Respuestas de la Actividad Web

## 1. ¿Quién, dónde y cuándo se crea el primer servidor web?
* **Quién:** Tim Berners-Lee.
* **Dónde:** En el CERN (Suiza).
* **Cuándo:** En 1990, funcionando en un ordenador NeXT.

---

## 2. ¿Qué es la pila de protocolos usados por http?
HTTP funciona apoyándose en la pila de protocolos TCP/IP, donde cada capa tiene su función:
* **Capa de Aplicación:** HTTP o HTTPS, maneja los datos de la web.
* **Capa de Transporte:** TCP, asegura que los datos lleguen bien y en orden.
* **Capa de Red:** IP, se encarga de llevar los paquetes por la red.
* **Capa de Enlace / Física:** Es la conexión física, como los cables o el Wi-Fi.

---

## 3. ¿Componentes de una URL?
Una URL se forma con las siguientes partes:
* **Esquema o protocolo:** Indica cómo nos conectamos, por ejemplo http o https.
* **Autoridad:** Usuario y contraseña (si se necesitan).
* **Host o dominio:** El nombre o IP del servidor, como www.ejemplo.com.
* **Puerto:** El puerto por el que se entra, por defecto el 80 para HTTP y el 443 para HTTPS.
* **Ruta:** La ubicación exacta del archivo en el servidor.
* **Parámetros:** Datos o variables que se mandan al servidor.
* **Fragmento:** Un ancla para ir a una zona concreta de la página.

---

## 4. ¿Pasos en la recuperación de una página web mediante HTTP?
1. **Resolución DNS:** El navegador busca la IP correspondiente al nombre de la página.
2. **Conexión TCP:** Se crea el canal de comunicación con el servidor.
3. **Negociación TLS/SSL:** Si la web es segura (HTTPS), se cifra la conexión.
4. **Petición HTTP:** El navegador pide el archivo o recurso que quiere ver.
5. **Respuesta HTTP:** El servidor contesta enviando el código de estado y el contenido (HTML, imágenes...).
6. **Renderizado:** El navegador lee toda esa información y la muestra visualmente en la pantalla.

---

## 5. Diferencia entre páginas dinámicas y estáticas
* **Páginas estáticas:** Su contenido siempre es el mismo. El servidor devuelve el archivo tal cual está guardado en el disco.
* **Páginas dinámicas:** El contenido se crea en el momento. El servidor ejecuta un programa o consulta una base de datos para armar la página a medida antes de enviarla.

---

## 6. ¿Cómo usar telnet para acceder a un servidor web?
Para entrar a un servidor web usando telnet:
1. Abres la terminal y escribes el comando para conectarte al puerto 80 del servidor.
2. Cuando estés dentro, escribes la petición HTTP básica con el método GET y el Host correspondiente.
3. Pulsas Enter dos veces para enviar la orden y verás la respuesta en código HTML que te devuelve el servidor.
