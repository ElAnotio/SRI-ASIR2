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





