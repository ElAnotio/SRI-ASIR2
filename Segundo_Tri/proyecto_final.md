# Proyecto Final 2º Trimestre: Servidor Alojamiento Web --> Antonio Rosado

**Se pide las instalación, configuración y puesta en marcha de un servidor que ofrezca servicio de alojamiento web configurable:**

## Paso 1: Instalación de servicios:

Ahora procederemos a instalar todos los servicios que necesitaremos (no todos los servicios, pero los necesarios por el momento) 

Usaremos el comando:

**sudo apt install apache2 php mysql-server phpmyadmin openssh-server python3**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/d431f8be-fed3-4711-9e3e-6493fd390ce7)

### Alojamiento a páginas web tanto estáticas como dinámicas con “php”

Después de instalar php, tendremos que instalar algunos plugins para el servicio, usaremos:

**sudo apt install php-fpm php-mysql**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/db893f49-8deb-46a1-8404-38011f7eae97)

Creamos el directorio para el dominio de la siguiente manera:

**sudo mkdir /var/www/antonioserver**

A continuación, asigne la propiedad del directorio con la variable de entorno $USER:

**sudo chown -R $USER:$USER /var/www/your_domain**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/f70e606b-7a64-4bc3-8f25-c7baf171bd55)

Luego, abra un nuevo archivo de configuración en el directorio sites-available de Apache:

**sudo nano /etc/apache2/sites-available/antonioserver.conf**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/e1490565-e408-41ec-acff-e4526ba79be8)

Pondremos la siguiente configuración:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/bbc85081-d184-4c3f-af8a-c982b1dc2fae)

Ahora, puede usar a2ensite para habilitar el nuevo host virtual:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/4e4cdc58-13e7-4174-901f-0bc95e13610e)

Puede ser conveniente deshabilitar el sitio web predeterminado:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/b27e8d84-80c9-40cf-bc15-7f60073a0117)

Después de probar toda la configuración, cambiaremos el orden para que coga los index.php primero:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/22a38326-0d2c-404e-9e01-dd4034496963)

Despues podemos comprobar que nos coge un index.php creado manualmente por nosotros:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/e1908399-8d26-4746-b905-29fb3621345d)

### Configuración usuario MYSQL y PHPMYADMIN

Usaremos la siguiente configuración para crear un usuario y una base de datos con sus respectivos privilegios:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/ef1102b3-a9eb-46e2-86b1-e990875b3e80)

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/7d7c7351-a9b4-4528-ac01-9224fcba2107)

Si accedemos a phpmyadmin con los siguientes datos, debemos acceder:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/bd47a0a0-20ff-45a2-9af4-c5e2da0938e6)

A continuación, instalaremos los siguientes servicios:

**BIND9:**

Primero, instalaremos el servicio BIND9:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/3826ac43-7603-4ab5-af3f-50a46d2b49f5)

Ahora, editaremos el archivo de opciones de bind:

```
sudo nano /etc/bind/named.conf.options
```

Ahora pondremos la direccion que va a utilizar nuestro dominio marisma.local

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/c93cefae-7fcc-4745-9c7b-8e77822e3b67)

Ahora crearemos la zona directa y la zona inversa de nuestro dominio:

```
sudo nano /etc/bind/named.conf.local
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/bd3e4fc2-e053-4a17-95c4-6fb66dc83d7f)

Ahora, utilizaremos el siguiente comando para comprobar que la sixtaxis funciona correctamente:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/911b26be-1b0c-4abd-8b32-5a482e7a7d78)

Ahora, crearemos una carpeta para las zonas y crearemos el archivo copiando el db.local

```
sudo cp /etc/bind/db.local /etc/bind/zones/db.marisma.local
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/5c564575-b41d-4ec2-917f-f4045490b603)

Haremos lo mismo con la zona indirecta y quedará la carpeta de esta manera:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/a3cdc5be-a673-4eb1-8958-0e85dec6bc51)

El archivo de configuracion de la zona directa pondremos lo siguiente:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/010e8c11-9232-4273-82f2-f93e5f461558)

Y en la inversa:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/f5499f42-e948-479a-8966-93c36d383e16)

Una vez hecho todo, restableceremos bind9 para que se apliquen los cambios:

```
sudo systemctl restart bind9
```

**PROFTPD**:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/0884909d-c075-4daf-a4c3-43b188181f5a)

**Configura filezilla para usar una conexión TLS y comprueba que funciona correctamente.**

Primero, iremos al archivo **proftpd.conf** y desmarcaremos el comentacio de incluir tls.conf

```
sudo nano /etc/proftpd/proftpd.conf
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/a2707828-86b8-4ad5-970d-b28ee5f13432)

Después nos iremos a modules.conf y desmarcaremos las siguientes lineas:

```
sudo nano /etc/proftpd/modules.conf
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/3f2dcb20-2651-4e18-9ca7-49dfd655c2fb)

Después instalaremos el siguiente servicio:

```
sudo apt isntall proftpd-mod-crypto
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/41df62fe-c307-4700-8646-2dbaa7c1d431)

Después de instalarlo, editaremos el archivo tls.conf y desmarcamos los siguientes enunciados:

```
sudo nano /etc/proftpd/tls.conf
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/0b6d0641-a540-402b-b7ef-5a516498bbf6)

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/4e0093dc-b320-4a01-805c-d9292ac70468)

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/00f0f097-842e-4e59-b496-1b38885455a5)

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/8c2dbf68-e27d-4111-9158-4f7913b2ce59)

Una vez desmarcados, reiniciamos el servicio proftpd

```
sudo systemctl restart proftpd
```

Después de reiniciar, usaremos el comando para general un certificado de seguridad, cogeremos el comando de tls.conf 

```
sudo nano /etc/proftpd/tls.conf
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/db7d1d47-2b73-4fdd-ae36-528ff9522de5)

Lo usaremos y contestaremos a las preguntas:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/cc9d4671-7364-41b4-beae-57fd6aae88fe)

Después conectaremos con el filezilla con la siguiente configuración:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/8db1f349-756e-48e9-96ad-65f31657b646)

Si comprobamos toda la configuración, nos aparecerá el certificado creado anteriormente y tendremos hecho nuestra comunicacion con TLS:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/404e6ab6-d3fd-4825-ad22-7d90acf54096)

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/4120607c-007e-4918-aa36-64793f092bcf)


**POSTFIX, IMAP Y POP3:**

Primero, instalaremos POSTFIX y procedemos a su configuracion:

```
sudo apt-get install postfix
```

Haremos click en sitio de internet:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/46502096-d6a5-4416-8905-32f5fd0cb2bc)

Luego configuraremos el sitio mail:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/e9b50da4-300e-4245-b9fd-33d5f7f83ccb)

Esperaremos a que termina de instalar y ya lo tendremos configurado.

Comprobaremos que funciona utilizando 

```
sudo systemctl status postfix
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/f871a942-c1f2-4496-858b-7cbfbf94b2fd)

Para instalar IMAP Y POP3 utilizaremos:

```
sudo apt install dovecot-imapd dovecot-pop3d
```
![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/31dba36b-b396-4047-bdec-7ea23de81b57)

Reiniciaremos dovecot por si acaso:

```
sudo systemctl restart dovecot
```
Ahora editaremos el archivo dovecot.conf

```
nano /etc/dovecot/dovecot.conf
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/6e2e4e49-c43f-47d8-868a-16e784dcf059)

Añadiremos la siguiente linea:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/ea0b1758-e1ab-4074-9eb9-c7986b17fd7b)



## Paso 2: Creacion del script

Para crear el script, usaremos el sudo nano y crearemos un **script.sh**

Utilizaremos el siguiente contenido:
```
#!/bin/bash

# Datos requeridos
sitio_web="ejemplo.com"
usuario_ftp="ftp_user"
usuario_ssh="ssh_user"
subdominio="subdominio.ejemplo.com"
base_datos="basedatos"
usuario_mysql="mysql_user"

# Crear usuario y directorio para alojamiento web
sudo useradd -m -d /home/$sitio_web -s /bin/bash $sitio_web
sudo mkdir /var/www/$sitio_web
sudo chown $sitio_web:$sitio_web /var/www/$sitio_web

# Configurar host virtual en Apache
sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/$sitio_web.conf
sudo sed -i "s/ServerAdmin webmaster@localhost/ServerAdmin admin@$sitio_web/g" /etc/apache2/sites-available/$sitio_web.conf
sudo sed -i "s/DocumentRoot \/var\/www\/html/DocumentRoot \/var\/www\/$sitio_web/g" /etc/apache2/sites-available/$sitio_web.conf
sudo sed -i "s/<Directory \/var\/www\/>/Directory \/var\/www\/$sitio_web>/g" /etc/apache2/sites-available/$sitio_web.conf
sudo a2ensite $sitio_web.conf
sudo systemctl reload apache2

# Crear usuario del sistema para FTP, SSH, etc.
sudo useradd -m -s /bin/bash $usuario_ftp
sudo usermod -aG www-data $usuario_ftp  # Agregar usuario FTP al grupo de Apache para tener acceso al directorio del sitio web
sudo passwd $usuario_ftp  # Establecer la contraseña para el usuario FTP

sudo useradd -m -s /bin/bash $usuario_ssh
sudo passwd $usuario_ssh  # Establecer la contraseña para el usuario SSH

# Crear subdominio en servidor DNS
sudo bash -c "echo '127.0.0.1 $subdominio' >> /etc/hosts"
sudo bash -c "echo 'zone \"$subdominio\" {
  type master;
  file \"$subdominio.zone\";
};' >> /etc/bind/named.conf.local"

sudo touch /var/lib/bind/$subdominio.zone
sudo bash -c "echo '$subdominio. IN SOA ns.$subdominio. root.$subdominio. (
  2024020201; Serial
  3600; Refresh
  1800; Retry
  604800; Expire
  86400 ); Minimum TTL
$subdominio. IN NS ns.$subdominio.
ns.$subdominio. IN A 127.0.0.1
$subdominio. IN MX 10 mail.$subdominio.
mail.$subdominio. IN A 127.0.0.1
www.$subdominio. IN CNAME $subdominio.
ftp.$subdominio. IN CNAME $subdominio.
smtp.$subdominio. IN CNAME $subdominio.
pop.$subdominio. IN CNAME $subdominio.
imap.$subdominio. IN CNAME $subdominio.
' >> /var/lib/bind/$subdominio.zone"

sudo systemctl restart bind9

### Crear base de datos y usuario MySQL
sudo mysql -e "CREATE DATABASE $base_datos;"
sudo mysql -e "CREATE USER '$usuario_mysql'@'localhost' IDENTIFIED BY 'password';"
sudo mysql -e "GRANT ALL PRIVILEGES ON $base_datos.* TO '$usuario_mysql'@'localhost';"
sudo mysql -e "FLUSH PRIVILEGES;"

### Habilitar la ejecución de aplicaciones Python con el servidor web
sudo apt install libapache2-mod-wsgi-py3
sudo a2enmod wsgi
sudo systemctl restart apache2

echo "Script completado."
```


