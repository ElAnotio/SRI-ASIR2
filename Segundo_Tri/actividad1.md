## Actividad 1:

**1- ¿Qué es TLD? ¿Cómo se clasifican los dominios de nivel superior?, Pon algunos ejemplos.** 

TLD son las siglas de "Top-Level Domain" o "Dominio de Nivel Superior". Estos son los dominios de nivel más alto en la jerarquía del 
sistema de nombres de dominio (DNS). Se dividen en dos categorías principales: los TLD genéricos (gTLD) y los TLD de código de país (ccTLD).

**2- ¿Qué es FQDN?, Pon algún ejemplo de FQDN**

FQDN son las siglas de "Fully Qualified Domain Name" o "Nombre de Dominio Completo". Es un nombre de dominio que especifica su ubicación exacta en la jerarquía del DNS. Un FQDN incluye el nombre de host y 
todos los niveles de dominio en la jerarquía, desde el dominio de nivel más alto hasta el subdominio más específico.

**3- ¿Qué son los root servers? , ¿Cuántos root servers hay?, ¿Cuántos servidores raíz físicos existen y dónde se encuentran?, ¿Qué es anycast?**

Los root servers son servidores DNS que forman la base de la jerarquía del sistema de nombres de dominio. Hay 13 conjuntos de servidores raíz distribuidos en todo el mundo. Estos servidores no almacenan información sobre dominios específicos sino que responden a las consultas de DNS proporcionando información sobre los servidores de nivel superior.

Anycast:
Anycast es una técnica de enrutamiento en la que una dirección IP se asigna a varios servidores distribuidos geográficamente. Cuando se realiza una consulta a una dirección Anycast, la red dirigirá la solicitud al servidor más cercano en términos de topología de red.

**4- ¿Qué es un archivo de zona (zone file)? Indica para qué sirven los registros de un archivo de zona. Pon un ejemplo de un archivo de zona e interpreta la información almacenada**

Un archivo de zona es un archivo de texto que almacena información sobre la asociación entre nombres de dominio y direcciones IP en un servidor DNS. Contiene registros DNS que definen diversas propiedades de un dominio.
