## Trabajo Docker: Creación de contenedor.

**Creación mediante mediante Docker de un contenedor DNS y al menos un contenedor que actuará como servidor (web, mysql, ssh,...) Se configurará la red, volúmenes y scripts necesarios para ponerlos en marcha.**

### Paso 1: Instalación y configuración de servicio docker.

Empezaremos paso a paso por los comandos que tienes que seguir:

```
sudo apt update
```

```
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
```

```
sudo apt install docker-ce
```

Por ultimo, comprobaremos con un status que todo funciona:

```
sudo systemctl status docker
```

### Descarga de imagenes

Empezaremos descargando la de DNS, pondremos el comando:

```
sudo docker pull ubuntu/dns
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/b5935bd2-40ca-4455-b617-51e4b29f55b1)

Y luego con la de nginx:

```
sudo docker pull nginx
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/294ffa62-c20c-4c13-a5fd-1f108354f74b)

## Creación de docker-compose

```
version: '3'

services:
  dns:
    image: ubuntu/bind9
    container_name: dns_container
    enviroment:
      - BIND9_USER=root
    ports:
      - "55:53/udp"
      - "55:53/tcp"
    volumes:
      - ./config:/etc/bind
      - ./cache:/var/cache/bind
      - ./records:/var/lib/bind
    networks:
      - docker0
    restart: unless-stopped

  web_server:
    image: nginx
    container_name: web_container
    ports:
      - "8080:80"
    networks:
      - docker0
    volumes:
      - /home/linux/webfiles:/usr/share/nginx/html

networks:
  docker0:
    driver: bridge
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/0945a8ed-df68-4fc7-8d39-af82345b27dd)

**Para dns:**

Crearemos una estructura de carpetas para que funcione el dominio:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/6cfe4b16-8813-477f-9c06-02d059d8a868)

Dentro de config, tendremos los archivos para la configuración del dominio:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/75674d55-9a8f-4566-a1fe-76acc1c9f71c)

Tendremos la siguiente configuración:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/3f389d7f-c33f-4290-9090-a4d1e3306fbb)

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/c5341f84-00c3-45ed-849b-0d49c62bb93b)

### Ejecutar el docker-compose:

```
sudo docker-compose -f docker-compose-dns.yml up -d
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/d739b827-d826-421d-8e4b-1e5f956c6bdb)

Nos ha creado los contenedores perfectamente, los comprobaremos con:

```
sudo docker ps -a
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/79c3be39-9b08-48a5-a623-ac9d9d2a5833)

Para comprobar que funciona, nos iremos a nuestro dominio, con el puerto de nginx y nos aparecerá:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/012abac9-3ca8-4734-b369-2c739e9a2e02)

### Errores en la práctica:

Todo ha salido a la perfección, el unico inconveniente es que a la hora de resolver el dominio, no es capaz de encontrar nada, ya sea con dig, o nslookup:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/d09bd200-6f2e-4a65-9dc8-3ed7535a16f0)

He probado con:
- Añadir al archivo hosts.
- Editar el archivo resolved.conf.
- Acceder desde la máquina del contenedor y ejecutar los comandos necesarios para instalar tanto nslookup, nano, etc.
- Cambiar varias directivas del propio docker-compose.
- Cambiar el puerto por si da conflicto.
- Cambiar de imagen de bind9 a algunas del propio docker hub.
- Cambiar las ip de los ficheros tanto de las máquinas del contenedor al de mi máquina.





