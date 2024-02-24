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

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/3826ac43-7603-4ab5-af3f-50a46d2b49f5)

**VSFTPD**:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/0884909d-c075-4daf-a4c3-43b188181f5a)


**POSTFIX, IMAP Y POP3:**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/da334e76-c194-4a49-a24b-cc6e3bb61ca9)

Terminaremos de configurarlo seleccionando en la panatalla 


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

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/fb7e0074-fb9d-4667-bf8b-559ae72b4dd3)

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/0306224d-4394-42ec-8eb1-8049d9090c63)


