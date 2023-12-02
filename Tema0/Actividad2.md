## Actividad 2: Configuración Básica de Apache

**1.Apache utilizará el puerto 81 además del 80**

El comando para editar esta directiva será /etc/apache2/ports.conf

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/6bc1d1f8-9057-438c-9516-7b244b4dba8c)

Pondremos un Listen 81 para que coja también ese puerto

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/3ee4f973-f7f2-4dfe-8853-ba05e24b796b)
	
**2.Añadir el dominio “marisma.intranet” en el fichero “hosts”**

La ruta será la siguiente: /etc/apache2/hosts

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/6eca8c28-b555-482f-b43a-ced3d78ada44)

Añadiremos el dominio en el fichero:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/37898087-5282-40d4-8a08-311d4a0fded8)
	
**3.Cambia la directiva “ServerTokens” para mostrar el nombre del producto.**

La directiva se encuentra: /etc/apache2/conf-available/security.conf

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/e50699b2-275e-4bfe-b59c-ab87a0e4fbf0)

Cambiamos la directiva a Prod:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/da0a6b56-3cc6-4116-8f12-d09b0da51922)

**4.Haz que se visualice el pie de página de Apache en tu navegador**

Si todo ha salido bien, nos saldrá en alguna página que no existe lo siguiente:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/8531d318-9eb8-4c03-8f71-c9985b12ecd6)
	
**5.Crea un directorio “prueba” y otro directorio “prueba2”. Incluye un par de páginas en cada una de ellas.**

Las creamos con el comando mkdir:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/ee9f75cf-4239-460d-8597-855897fd6b20)

Y creamos las páginas con nano:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/8dfe79ce-9acd-4624-a61c-44db86111c37)

**6.Redirecciona el contenido de la carpeta “prueba” hacia “prueba2”**

Nos dirigimos a /etc/apache2/apache2.conf

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/4e838211-d77c-43c0-b637-50a8d5c5feb8)

Y añadimos una linea para el redirect de prueba a prueba2:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/73d63be1-0ccf-4455-95bc-787c0138e0de)
	
**7.Es posible redireccionar tan solo una página en lugar de toda la carpeta. Pruébalo.**

Simplemente en el mismo documento, tendremos que poner en la direccion el archivo de la pagina:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/c825c403-5bcb-4da9-81ec-66900d10378f)

**8.Usa la directiva userdir**

La directiva se encuentra aquí:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/e5335332-592f-4d02-8278-573d65d31856)

**8.Usa la directiva alias para redireccionar a una carpeta dentro del directorio de usuario.**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/7c259d98-6709-41a1-a816-76df9e6478ef)

**9.¿Para qué sirve la directiva Options y dónde aparece. Comprueba si apache indexa los directorios. Si es así, ¿cómo lo desactivamos?**

La directiva Options en Apache se utiliza para controlar diversas características y funcionalidades a nivel del servidor o del directorio. Puede afectar cómo Apache maneja ciertos aspectos de la solicitud, como la posibilidad de seguir enlaces simbólicos (FollowSymLinks), permitir o restringir ejecución de scripts (ExecCGI), permitir o restringir la visualización del contenido de un directorio (Indexes), entre otras opciones.

Para desactivar la indexación de directorios, simplemente elimina la opción Indexes o cámbiala a Options -Indexes:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/aecdadbe-505c-4503-87f9-171e67465054)



