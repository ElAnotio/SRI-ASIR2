## Actividad 3: Directivas Básicas:

**1. Busca información sobre las siguientes directivas y el valor que toman por defecto y el lugar donde se encuentra definida.**

### **Directivas de identificación**

**ServerName:** Esta directiva se utiliza para especificar el nombre de host del servidor que se utiliza para el acceso en red. Es importante configurar este parámetro, especialmente si se ejecutan múltiples sitios web en un mismo servidor.

Valor por defecto: No hay un valor predeterminado, es necesario configurarlo explícitamente.

Lugar donde se define: Puede definirse en el archivo de configuración principal de Apache

**ServerAdmin:** Esta directiva se utiliza para especificar la dirección de correo electrónico del administrador del servidor. Se utiliza principalmente para los mensajes de error generados por el servidor web, como páginas de error 500.

Valor por defecto: No hay un valor predeterminado, debe ser configurado explícitamente.

Lugar donde se define: Al igual que ServerName, puede definirse en el archivo de configuración principal de Apache, en archivos de configuración adicionales o dentro de archivos de virtual hosts.

**ServerTokens:** La directiva ServerTokens controla qué información de identificación del servidor se incluye en la respuesta HTTP. Los valores comunes incluyen Full (que muestra información detallada sobre la versión del servidor), Prod (muestra solo el nombre del servidor) y otros valores como Minor, Major, Min, etc., que proporcionan diferentes niveles de detalle sobre la versión del servidor.

Valor por defecto: Full en versiones anteriores a Apache 2.3.6, y prod en versiones posteriores a Apache 2.3.6.

Lugar donde se define: Se establece en el archivo de configuración principal de Apache (httpd.conf) o en archivos de configuración adicionales.

### **Directivas de localización de ficheros**

**DocumentRoot:** Esta directiva especifica el directorio raíz desde el cual se sirven los archivos para un sitio web en particular. Todo el contenido web accesible a través del servidor web se encuentra dentro de este directorio.

Valor por defecto: No hay un valor por defecto establecido. Debe ser configurado para cada host virtual o para el servidor principal.

Lugar donde se define: Puede ser configurado en el archivo de configuración principal de Apache (httpd.conf) o en archivos de configuración de hosts virtuales (httpd-vhosts.conf).

**ErrorLog:**	Esta directiva define la ubicación del archivo de registro de errores del servidor. Todos los errores generados por el servidor se registran en este archivo, lo que facilita la identificación y resolución de problemas.

Valor por defecto: Depende de la configuración predeterminada del sistema o puede ser configurado explícitamente.

Lugar donde se define: Se establece en el archivo de configuración principal de Apache (httpd.conf) o en archivos de configuración adicionales.

**CustomLog:** La directiva CustomLog especifica la ubicación del archivo de registro de acceso personalizado. Todos los accesos al servidor web se registran en este archivo, lo que permite un seguimiento detallado de las solicitudes entrantes, como las direcciones IP de los clientes, las páginas solicitadas, los códigos de respuesta HTTP, entre otros detalles.

Valor por defecto: Puede ser configurado explícitamente.

Lugar donde se define: Se establece en el archivo de configuración principal de Apache (httpd.conf) o en archivos de configuración adicionales.

**ServerRoot;**	Esta directiva define el directorio base en el cual se encuentra instalado el servidor Apache. Es el punto de partida para la mayoría de las rutas de acceso en la configuración del servidor web y sirve como base para otros directorios importantes como conf/, logs/, htdocs/, etc.

Valor por defecto: Depende de la instalación de Apache, generalmente establecido al momento de la instalación.

Lugar donde se define: Se define en el archivo de inicio del script del servidor Apache (apachectl o httpd).

### **Directivas de control de la conexión**

**Timeout:** Esta directiva define el tiempo máximo que el servidor esperará para recibir una solicitud completa del cliente. Si transcurre este tiempo sin que el servidor reciba toda la solicitud, se cierra la conexión.

Valor por defecto: 300 (segundos).

Lugar donde se define: Se establece en el archivo de configuración principal de Apache (httpd.conf) o en archivos de configuración adicionales.

**KeepAlive:** La directiva KeepAlive se utiliza para habilitar o deshabilitar la funcionalidad de Keep-Alive. Cuando está habilitado, permite que múltiples solicitudes HTTP se realicen a través de la misma conexión TCP, lo que puede mejorar la velocidad de carga de la página al evitar el tiempo de establecimiento de conexión repetido.

Valor por defecto: On.

Lugar donde se define: Se establece en el archivo de configuración principal de Apache (httpd.conf) o en archivos de configuración adicionales.

**MaxKeepAliveRequests:** Define el número máximo de solicitudes HTTP permitidas a través de una conexión Keep-Alive. Una vez que se alcanza este límite, la conexión se cierra.

Valor por defecto: 100.

Lugar donde se define: Se establece en el archivo de configuración principal de Apache (httpd.conf) o en archivos de configuración adicionales.

**KeepAliveTimeout:** Esta directiva define el tiempo de espera máximo para recibir la siguiente solicitud en una conexión Keep-Alive. Si no se recibe ninguna solicitud en este tiempo, la conexión se cerrará.

Valor por defecto: 5 (segundos).

Lugar donde se define: Se establece en el archivo de configuración principal de Apache (httpd.conf) o en archivos de configuración adicionales.

### **Otras** 

**LogLevel:** La directiva LogLevel controla el nivel de verbosidad de los mensajes que se registrarán en los archivos de registro de error. Se puede establecer en diferentes niveles, como emerg, alert, crit, error, warn, notice, info, debug, según la cantidad de información que se desee registrar.

Valor por defecto: warn.

Lugar donde se define: Se establece en el archivo de configuración principal de Apache (httpd.conf) o en archivos de configuración adicionales.

**LogFormat:** Esta directiva define el formato de registro de acceso utilizado para registrar las solicitudes en el archivo de registro de acceso. Puede personalizarse para incluir diferentes campos como dirección IP, fecha y hora, solicitud HTTP, código de respuesta, entre otros.

Valor por defecto: No hay un valor predeterminado. Se debe definir explícitamente.

Lugar donde se define: Se establece en el archivo de configuración principal de Apache (httpd.conf) o en archivos de configuración adicionales.
