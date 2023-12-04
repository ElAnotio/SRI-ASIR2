## Actividad 4: Directivas Básicas:

### Busca información sobre las siguientes directivas. Indica para que se usan y escribe un ejemplo que hayas encontrado.

**IfModule:** Esta directiva permite la configuración condicional basada en si un módulo específico de Apache está cargado o no.

Ejemplo: 

    <IfModule mod_ssl.c>
    # Configuración específica si el módulo SSL está cargado
    SSLCipherSuite HIGH:MEDIUM:!aNULL:!MD5
    SSLProtocol all -SSLv2 -SSLv3

**LoadModule:** Permite cargar módulos adicionales en el servidor Apache.

Ejemplo:

LoadModule rewrite_module modules/mod_rewrite.so
	
**Include** Permite incluir archivos de configuración adicionales dentro del archivo de configuración principal de Apache.

    Include conf/extra/httpd-vhosts.conf
	
**<Directory>** Se utiliza para aplicar configuraciones específicas a un directorio en particular en el sistema de archivos.

Ejemplo:

    <Directory "/var/www/html">
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

**<Files>** Permite aplicar configuraciones a archivos específicos.

Ejemplo: 

    <Files "example.php">
        Require all denied
    </Files>

**<Location>** Define configuraciones basadas en la URL o la ruta de acceso.

Ejemplo:

    <Location "/example">
        SetHandler cgi-script
        Options +ExecCGI
    </Location>
	
**<VirtualHost>**  Permite configurar múltiples hosts virtuales en un solo servidor.

    <VirtualHost *:80>
        ServerAdmin webmaster@example.com
        DocumentRoot /var/www/example
        ServerName example.com
        ServerAlias www.example.com
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
    </VirtualHost>

**¿Qué son los ficheros .htaccess?**

Los archivos .htaccess son archivos de configuración que permiten a los propietarios de sitios web modificar la configuración del servidor Apache a nivel de directorio sin necesidad de acceder al archivo de configuración principal. Estos archivos pueden contener directivas como redirecciones, autenticación, restricciones de acceso, configuraciones de MIME types, entre otras. Permiten una personalización flexible y específica del directorio para los sitios web que se ejecutan en un servidor Apache.
