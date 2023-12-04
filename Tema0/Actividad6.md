## Actividad 6: Expresiones Regulares

**1. Directorios en /www/ cuyo nombre consista en tres dígitos.**

/www/\d{3}

**2. Ficheros: *.gif, *.jpeg, *.jpg, *.png**

.*\.(gif|jpeg|jpg|png)$

**3.  Escribe una directiva para redireccionar todos los GIF a ficheros JPEG en otro servidor**

RewriteEngine On
RewriteRule ^(.+)\.gif$ http://otro-servidor.com/$1.jpg [R=301,L]


**4. Ficheros cuyo nombre corresponda con números enteros y decimales**

^\d+(\.\d+)?$

**5. Números de teléfono en el formato Americano: 123-123-1234**

\d{3}-\d{3}-\d{4}

**6. Palabras**

\b[a-zA-Z]+\b

**7. Códigos hexadecimales de color de 24 o 32 bits**

Expresión Regular para 24 bits: #(?:[0-9a-fA-F]{3}){1,2}

Expresión Regular para 32 bits: #(?:[0-9a-fA-F]{4}){1,2}

**8. Palabras de 4 letras**

\b[a-zA-Z]{4}\b

**9. Número entero sin signo**

\b\d+\b

**10. Número entero con signo**

[-+]?\b\d+\b

**Números reales**

[-+]?\b\d+\.\d+\b

**11. Número reales con exponente**

[-+]?\b\d+(\.\d+)?[eE][-+]?\d+\b

**12. Email**

^(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$



**13. Números del 0 a 255**
