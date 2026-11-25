Previamente se recomienda leer:
http://www.rexegg.com/regex-quickstart.html
http://www.regexr.com/
http://iie.fing.edu.uy/~vagonbar/unixbas/expreg.htm

# Lleva a cabo los problemas planteados en la web:
http://regexone.com

![Descripción de la imagen](https://github.com/user-attachments/assets/00e35808-afcb-4ffd-b61e-1d89aaafd12b)
![Descripción de la imagen](https://github.com/user-attachments/assets/38024dce-f11b-43fd-8d19-30dc3b28b6a0)
![Descripción de la imagen](https://github.com/user-attachments/assets/523a5951-96cb-4791-bc58-4ec39f6fce7c)
![Descripción de la imagen](https://github.com/user-attachments/assets/c0ce923b-d80a-43bd-9c90-479844fc1f86)
![Descripción de la imagen](https://github.com/user-attachments/assets/1f443712-d616-4f19-8f48-a498b0c936d9)
![Descripción de la imagen](https://github.com/user-attachments/assets/e96e6cc2-7c40-4eed-93db-750fb02f5a8d)
![Descripción de la imagen](https://github.com/user-attachments/assets/2d5b9053-9ca9-43b0-865d-7439a4a363ae)
![Descripción de la imagen](https://github.com/user-attachments/assets/2ca67603-2a76-4dff-8161-132be73fd000)
![Descripción de la imagen](https://github.com/user-attachments/assets/1bedefa6-a207-44a8-9e2f-b1f5deefd79d)
![Descripción de la imagen](https://github.com/user-attachments/assets/10cc5654-5dc2-4d44-8ff9-346dfeeea3ee)
![Descripción de la imagen](https://github.com/user-attachments/assets/e987a8ea-986c-48db-b307-265b982b777c)
![Descripción de la imagen](https://github.com/user-attachments/assets/75a15bc2-aad6-4226-af83-6ea79757b74a)
![Descripción de la imagen](https://github.com/user-attachments/assets/4f51c0f7-1e7e-4835-89df-329242d6f16a)
![Descripción de la imagen](https://github.com/user-attachments/assets/fcb756dd-7b8b-42dc-a837-bc05ba91a20f)
![Descripción de la imagen](https://github.com/user-attachments/assets/580d1fa0-e6a6-41d3-90fe-122336c52269)


## Escribe las expresiones regulares para los siguientes supuestos:

Directorios en /www/ de 3 dígitos:/^\/www\/\d{3}\/?$/

Ficheros (.gif, .jpeg, .jpg, .png):/^.*\.(gif|jpe?g|png)$/i

Redirección de GIF a JPEG:RedirectMatch 301 (.*)\.gif$ [http://otroservidor.com/$1.jpeg](http://otroservidor.com/$1.jpeg)

Números enteros y decimales:/^[+-]?\d+(\.\d+)?$/

Teléfono americano (123-123-1234):/^\d{3}-\d{3}-\d{4}$/

Palabras (incluye acentos/eñes):/\b[a-zñáéíóúü]+\b/i

Códigos de color hexadecimal (24 o 32 bits):/^#[\da-f]{6}([\da-f]{2})?$/i

Palabras de 4 letras:/\b[a-zñáéíóúü]{4}\b/i

Entero sin signo:/^\d+$/

Entero con signo:/^[+-]\d+$/

Números reales:/^[+-]?\d+(\.\d+)?$/

Reales con exponente:/^[+-]?\d+(\.\d+)?([eE][+-]?\d+)?$/

Correo electrónico:/^[\w._%+-]+@[\w.-]+\.[a-z]{2,}$/i

Números del 0 al 255:/^(?:\d|[1-9]\d|1\d\d|2[0-4]\d|25[0-5])$/


