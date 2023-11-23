# Proyecto 1º Trimestre
## Pasos del proyecto

**Paso 1: Instalación de Apache**

Empezamos instalando el servicio Apache, en ejercicios anteriores ya se muestra como se instala, saltaremos todos estos pasos y subiré una captura con todo instalado:

![](imag_proyecto/1.png)

**También tenemos que instalar una base de datos para previamente subir al wordpress**
Abre el terminal de MySQL escribiendo el siguiente comando:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/eaedb805-720d-4300-9c24-770753e3cef3)

Para establecer una contraseña para el usuario root utlizamos:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/d9146a39-b913-43c9-952d-c414fa72f5cd)

Utiliza el siguiente comando para crear una base de datos de WordPress:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/10b3e1db-f084-401f-8f50-04df2142fbc1)

Ahora, crearemos una cuenta de usuario MySQL para operar en la nueva base de datos de WordPress. Utilizaremos WordPressDB como nombre de la base de datos y UsuarioWordPress como nombre de usuario. Para crear un nuevo usuario y otorgar privilegios usa el siguiente comando:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/361f0cad-ded3-4970-a007-aef4810ad58e)

**Paso 2: Activar dominios**

Para usar los dominios requeridos por la práctica, nos debemos ir al archivo hosts que se encuentra en la carpeta /etc, mediamente el comando nano /etc/hosts vamos a editar el documento para añadir los 2 dominios:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/94a7548c-244e-4df8-a41b-6c76825e8353)

**Paso 3: Instalar Wordpress**

A continuación, para instalar wordpress, empezaremos por crear un archivo de wordpress.conf, con el comando **nano /etc/apache2/sites-available/wordpress.conf**
![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/46a327e7-450b-426d-a51e-424067573171)

Escribiremos el siguiente texto:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/9017e531-2433-407f-b77e-a684815102cd)

Crearemos una carpeta con el comando **mkdir /var/www/wordpress**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/fb830386-516a-4c53-9445-b65cb31524ed)

Ahora, activa el mod_rewrite para utilizar la función de permalink o enlace permanente de WordPress:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/13d3dc2e-3acd-4d5e-820f-b27f56ea3c41)

Tendremos que reiniciar el servidor web Apache utilizando el siguiente comando:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/c7fb828f-1657-4018-be94-de03dc3de4ff)

El siguiente paso es cambiar la directiva ServerName en el archivo /etc/apache2/apache2.conf. Abre el archivo con este comando: 

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/277f29f3-5edb-4755-aa6a-1e72f4cf8506)

Tendrás que configurar la directiva ServerName con la dirección IP o el nombre del servidor añadiendo la siguiente línea al archivo /etc/apache2/apache2.conf: 

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/f2b917ed-0d5d-49d4-9f3e-980f340ed994)

**Ahora pasaremos a instalar wordpress**
Primero, instala el paquete wget en tu VPS:
![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/d36f9c9c-defc-4ebd-9033-faa15563222b)

A continuación, utiliza el comando wget seguido del enlace de descarga de WordPress:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/feaf4dca-520a-4584-97ee-5bb3dd14a6eb)

Una vez que hayas descargado el archivo comprimido, instala la utilidad de descompresión utilizando estos comandos:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/375bdb70-2173-4007-9b1f-bf4412144489)

Ahora tendrás que mover el archivo al directorio correcto antes de descomprimirlo. Utiliza el comando:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/5a1e8d7e-2115-4daf-a26a-afa586ea5c6a)

A continuación, navega hasta el directorio y descomprime el archivo utilizando estos comandos:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/d42aa997-11ad-467a-b878-bf9fbe92e330)

Después, utiliza el siguiente comando para mover el directorio:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/368720a7-9f8e-46b0-b766-cd40a9451b5a)

El último paso es eliminar index.html. Utiliza el siguiente comando:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/a37b1cb7-0caa-4ea6-895a-8dfd9e268c3c)

Una vez hecho esto, reinicia Apache utilizando estos comandos:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/d4c31a95-607f-436f-a310-25c881f2adea)

Primero, selecciona un idioma para WordPress y haz clic en Continuar.

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/67e742a6-e2f1-412d-a2ff-4bda7cae4318)

Aparecerá un mensaje de Bienvenida a WordPress:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/6aee3867-8c74-4945-9a39-a392350bd141)

Luego te llevará a la página principal de configuración:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/75239642-f115-4716-b47c-391d096551f4)

Después, tendrás que introducir más información:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/50bdcd5b-1bfa-4501-852c-5d673a985c59)

Una vez instalado, procederemos a poder editar nuestra pagina:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/8ddfde10-adf5-4e30-9d8b-c7a23b6c1340)

**Paso 4: Python bajo Apache**

Para habilitar mod_wsgi en Apache, basta con instalar el paquete libapache2-mod-wsgi-py3:
**sudo apt-get install libapache2-mod-wsgi-py3**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/bc8afa70-3629-4058-97dc-c9904683f17e)

Crear la estructura de directorios para nuestra aplicación
**mkdir /home/linux/curso-python/trunk/python-web**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/0cebe20d-4d90-4b4b-9514-aafd303e6a16)

Dentro de este directorio, vamos a dividir su arquitectura en dos partes:

1- Destinada al almacenaje de nuestra aplicación Python pura (será un directorio privado, no servido).

2- Destinada a servir la aplicación (directorio público servido) en el cuál solo almacenaremos archivos estáticos.

**mkdir /home/yo/curso-python/trunk/python-web/mypythonapp**
**mkdir /home/yo/curso-python/trunk/python-web/public_html**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/3c1c9733-931c-40c9-a289-1aabc90ff46d)

Dentro de nuestro directorio mypythonapp, almacenaremos entonces, todos los módulos y paquetes de nuestra aplicación Python, mientras que en public_html, estarán todos los archivos estáticos y será el único directorio al que se pueda acceder mediante el navegador Web.

Aprovecharemos este paso, para crear una carpeta, destinada a almacenar los logs de errores y accesos a nuestra Web App:

**mkdir /home/linux/curso-python/trunk/python-web/logs**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/07dacd85-b48a-4972-b228-465cb686bea2)

**Crear un controlador para la aplicación:**
Todas las peticiones realizadas por el usuario (es decir, las URI a las cuáles el usuario acceda por el navegador), serán manejadas por un único archivo, que estará almacenado en nuestro directorio mypythonapp.

**echo '# -*- coding: utf-8 -*-' > mypythonapp/controller.py**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/0789fad5-4267-40d5-a1ed-1e74e9cb8b83)

Ahora, editaremos el archivo creado .py con la siguiente información:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/83608d0f-e2a3-4dbb-a1fc-64cd7d17b5f4)

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/9e654339-d22a-4da2-9939-d1f6b67d00a3)

















