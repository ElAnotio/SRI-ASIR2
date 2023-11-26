# Proyecto 1º Trimestre
## Pasos del proyecto

### **Paso 1: Instalación de Apache**

Empezamos instalando el servicio Apache, primero ded todo, para instalarlo, utilizamos el comando:
**apt install apache2**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/1f4dc23a-b88c-4684-a2bf-53bab4b9504d)

**También tenemos que instalar una base de datos para previamente subir al wordpress**
Abre el terminal de MySQL escribiendo el siguiente comando:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/eaedb805-720d-4300-9c24-770753e3cef3)

Para establecer una contraseña para el usuario root utlizamos:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/d9146a39-b913-43c9-952d-c414fa72f5cd)

Utiliza el siguiente comando para crear una base de datos de WordPress:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/10b3e1db-f084-401f-8f50-04df2142fbc1)

Ahora, crearemos una cuenta de usuario MySQL para operar en la nueva base de datos de WordPress. Utilizaremos WordPressDB como nombre de la base de datos y UsuarioWordPress como nombre de usuario. Para crear un nuevo usuario y otorgar privilegios usa el siguiente comando:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/361f0cad-ded3-4970-a007-aef4810ad58e)

**A continuación, tendremos que instalar PHP**

**apt install php libapache2-mod-php php-mysql**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/2d2cd361-bc61-4327-a4b0-959cc65ab125)

### **Paso 2: Activar dominios**

Crearemos una carpeta con los nombres de nuestros dominios:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/8d5912fd-6d10-4e44-92ef-ae359c216993)

A continuación, asigne la propiedad del directorio con la variable de entorno $USER, que hará referencia a su usuario de sistema actual:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/8e1b665e-6905-4563-8305-bcf7711c6849)

Luego, abra un nuevo archivo de configuración en el directorio sites-available de Apache usando el editor de línea de comandos que prefiera. En este caso, utilizaremos nano:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/ebe6db15-87df-422d-9b5f-ff6a6ccc705f)

De esta manera, se creará un nuevo archivo en blanco. Pegue la siguiente configuración:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/35651e47-0431-4c3b-85a6-ca9ba0daa09f)

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/c6f7d1ab-274b-4f0a-92a0-a9b1986da684)

Ahora, puede usar a2ensite para habilitar el nuevo host virtual:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/170c40c0-5a55-4289-8f71-fccf9b1d841a)

Por último, vuelva a cargar Apache para que estos cambios surtan efecto:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/a67237ba-bf64-4dc5-a605-78aa9bdfa76d)


### **Paso 3: Instalar Wordpress**

A continuación, para instalar wordpress, empezaremos por crear un archivo de wordpress.conf, con el comando **nano /etc/apache2/sites-available/centro-intranet.conf**
![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/91108090-e914-41b4-86c8-48df8b97862e)


Escribiremos el siguiente texto:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/1bda2316-b9a9-48f4-955f-bdcfa1346fb6)


Crearemos una carpeta con el comando **mkdir /var/www/centro.intranet**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/f4f2472a-802d-4c14-9222-275533a554de)


Ahora, activa el mod_rewrite para utilizar la función de permalink o enlace permanente de WordPress:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/b09f9c5b-18be-454f-96a2-5b30c06bf1fb)


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

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/c0b8bf38-061f-4da1-9c81-71ceb7c431bf)


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

### **Paso 4: Python bajo Apache**

Para habilitar mod_wsgi en Apache, basta con instalar el paquete libapache2-mod-wsgi-py3:
**sudo apt-get install libapache2-mod-wsgi-py3**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/bc8afa70-3629-4058-97dc-c9904683f17e)

Crear la estructura de directorios para nuestra aplicación
**mkdir /home/linux/curso-python/trunk/python-web**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/0cebe20d-4d90-4b4b-9514-aafd303e6a16)

Dentro de este directorio, vamos a dividir su arquitectura en dos partes:

1- Destinada al almacenaje de nuestra aplicación Python pura (será un directorio privado, no servido).

2- Destinada a servir la aplicación (directorio público servido) en el cuál solo almacenaremos archivos estáticos.

**mkdir /var/www/departamentos.centro.intranet/trunk/python-web/mypythonapp**
**mkdir /var/www/departametos.centro.intranet/trunk/python-web/public_html**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/c59eb5d0-89eb-4a4d-99dd-78b33303a53f)


Dentro de nuestro directorio mypythonapp, almacenaremos entonces, todos los módulos y paquetes de nuestra aplicación Python, mientras que en public_html, estarán todos los archivos estáticos y será el único directorio al que se pueda acceder mediante el navegador Web.

Aprovecharemos este paso, para crear una carpeta, destinada a almacenar los logs de errores y accesos a nuestra Web App:

**mkdir /var/www/departamentos.centro.intranet/trunk/python-web/logs**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/ef639ee6-acdc-43af-ac11-3dad9b6876d0)


**Crear un controlador para la aplicación:**
Todas las peticiones realizadas por el usuario (es decir, las URI a las cuáles el usuario acceda por el navegador), serán manejadas por un único archivo, que estará almacenado en nuestro directorio mypythonapp.

**echo '# -*- coding: utf-8 -*-' > mypythonapp/controller.py**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/9c24d096-eb9e-4637-aef7-ac27d85da6d8)

Ahora, editaremos el archivo creado .py con la siguiente información:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/3e5338bd-4e71-4cc8-8662-ec4657dda08d)

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/30a2e073-bd39-444f-b36c-f6a2d90c23e1)

**Configurar el VirtualHost:**

Mientras que el DocumentRoot de nuestro sitio Web, será la carpeta pública, public_html, una variable del VirtualHost, será la encargada de redirigir todas las peticiones públicas del usuario, hacia nuestro front controller.

**sudo nano /etc/apache2/sites-available/departamentos.centro.intranet.conf**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/2b36bce3-9f40-4606-9ff4-0da29a7ad47b)

Una vez configurado nuestro VirtualHost, habilitamos el sitio web: 
**sudo a2ensite python-web**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/9e415df9-ba40-4735-ad43-d9a38e629fe8)

Recargamos Apache:
**sudo service apache2 reload**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/98a88e7b-b4d3-4c7d-9792-8637139c361d)

Habilitamos el sitio en nuestro host:
**sudo nano /etc/hosts** y allí agregamos la siguiente línea: 127.0.0.1 python-web

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/0b2106e3-e265-428d-b9ef-5531cf359e87)

Ahora, para comprobar que funcione, insertamos en la url la dirección puesta, o el nombre de dominio que le hemos asignado:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/a305b6d0-fe7a-4fd0-8332-1eb2f1d3730d)

### **Paso 4: Proteger el acceso a python con una autenticación:**

Instalaremos una utilidad llamada htpasswd, que forma parte del paquete apache2-utils para administrar los nombres de usuarios y contraseñas con acceso a contenido restringido.

**sudo apt-get install apache2-utils**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/5ca5501c-d6f4-4a19-b2d4-fca444194bd0)

Crearemos el primer usuario de la siguiente manera (sustituya `first_username por el nombre de usuario que elija):

**sudo htpasswd -c /etc/apache2/.htpasswd first_username**
Se le solicitará proporcionar y confirmar una contraseña para el usuario:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/8409e6dd-a8b4-4479-8662-514e197427ef)

Abra el archivo host virtual al que quiera añadir una restricción con un editor de texto como nano:


![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/23a61c6d-f412-4ec4-a549-b24699dd61e2)

En este paso, añada las siguientes líneas:

      AuthType Basic
      AuthName "Restricted Content"
      AuthUserFile /etc/apache2/.htpasswd
      Require valid-user


![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/a7d2df3b-d11b-409b-afd1-8d54aa216099)

Si actualizas, te saldrá el login en python:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/9ea71033-7133-4f86-8060-ef2d154ce204)

## **Paso 5: Instalar e implementar Awstat:**

El comando de instalación sería:
**sudo apt install awstats**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/2dcf9ed4-eda1-4b81-8e69-5269e23bfcb0)


Después creamos un archivo de configuración y editarlo:

**nano /etc/apache2/conf-available/awstats.conf**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/e246fbce-620e-4881-bd59-d775f689e50d)


En la configuración, pondremos lo siguiente:

ScriptAlias /awstats/ /usr/lib/cgi-bin/
Alias /awstats-icon/ /usr/share/awstats/icon/
Alias /awstatsclasses/ /usr/share/java/awstats/
 
<Directory "/usr/lib/cgi-bin/">
    Options None
    AllowOverride None
    <IfModule mod_authz_core.c>
        # Apache 2.4
        Require host 192.168.0.0/24
    </IfModule>
    <IfModule !mod_authz_core.c>
        # Apache 2.2
        Order allow,deny
        Allow from 192.168.0.0/24
        Allow from ::1
    </IfModule>
</Directory>

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/4505d37b-39bb-4416-8855-a381a66591b5)

Una vez escrito las directivas del archivo, utilizaremos dos comandos para habilitar la configuración:

**sudo a2enmod cgi**

**sudo a2enconf awstats** 

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/a6c1568a-c8f9-480a-9393-3ef011457cd2)

Y acto seguido recargamos apache2:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/1b67cc5f-8d10-4384-8d81-6e1085d88f42)

Siguiendo con los pasos:

**sudo cp /etc/awstats/awstats.conf /etc/awstats/awstats.departamento-centro-intranet.conf**

**sudo nano /etc/awstats/awstats.departamento-centro-intranet.conf** 

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/7f48a59e-4fd5-4d80-98b9-e265bd71a0cf)

Dentro de ese archivo, editaremos las siguientes variables:
	
LogFile="/var/www/departamentos.centro.intranet/trunk/python-web/log/access.log"

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/40c9ae31-46ce-4af8-9847-2a3a141b01e8)


SiteDomain="departamentos.centro.intranet"

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/6f0735db-9c50-47a8-9f82-8adce58d3e2b)

HostAliases="departamentos.centro.intranet localhost 127.0.1.1"

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/8fa6b90f-2aa1-407e-836c-ddcdc0a219e5)


A continuación, ejecutaremos el comando para actualizar el archivo:

**sudo /usr/lib/cgi-bin/awstats.pl -config=python-web -update**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/1129383e-b009-4c76-8236-c2412062e8c1)

Una vez ejecutado, si ponemos: http://departamentos.centro.intranet/awstats/awstats.pl?config=departamentos.centro.intranet.net

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/34d8c636-5817-49bf-868a-53cb2d33f492)






























