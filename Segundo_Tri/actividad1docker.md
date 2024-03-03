Instalación y configuración de servicio docker.

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
sudo apt-get install docker-ce
```

Por ultimo, comprobaremos con un status que todo funciona:

```
sudo systemctl status docker
```

