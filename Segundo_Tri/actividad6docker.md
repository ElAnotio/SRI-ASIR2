## Actividad 6: Creación de imágenes Docker

### Ejemplo 1: Construcción de imágenes con una página estática

Crearemos esta estructura de directorio:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/652b1d3a-72ed-49e3-b16e-16c31f9547ee)

Y añadiremos al dockerfile el siguiente contenido:

```
# syntax=docker/dockerfile:1
FROM debian:stable-slim
RUN apt-get update && apt-get install -y apache2 && apt-get clean && rm -rf /var/lib/apt/lists/*
WORKDIR /var/www/html/
COPY public_html .
EXPOSE 80
CMD apache2ctl -D FOREGROUND
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/5a2bfc6c-b89d-44c7-ac7d-2b92eea5fb74)

Para crear la imagen ejecutamos:

```
docker build -t antonio/ejemplo1:v1 .
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/1d0a75d9-385f-421d-8f43-a9fb5fdf1d7a)

Comprobamos que la imagen se ha creado:

```
docker images
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/0425c8cb-3515-4da5-b311-56b7173d3e8f)

Ejecutaremos la imagen para crear un contenedor:

```
docker run -d -p 80:80 --name ejemplo1 antonio/ejemplo1:v1
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/e3f8026b-2f31-4a3c-946e-6d0ea064ab7c)

Si hemos creado en el public_html una pequeña prueba, cuando lo ejecutes, deberá aparecerte:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/d87d7112-fc7b-478d-bec1-1ff5066e07de)

### Ejemplo 2: Construcción de imágenes con una una aplicación PHP

Vamos a tener el fichero Dockerfile y un directorio, llamado app con nuestra aplicación.

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/bdea4991-1a59-4b77-9ecc-046b7f0ee673)

Añadiremos el siguiente contenido al dockerfile:

```
# syntax=docker/dockerfile:1
FROM debian:stable-slim
RUN apt-get update && apt-get install -y apache2 libapache2-mod-php7.4 php7.4 && apt-get clean && rm -rf /var/lib/apt/lists/*
COPY app /var/www/html/
RUN rm /var/www/html/index.html
EXPOSE 80
CMD apache2ctl -D FOREGROUND
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/c9d421a2-6781-47dc-ac71-b49156d4afa8)

Para crear la imagen ejecutamos:

```
docker build -t antonio/ejemplo2:v1 .
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/39722449-1bdd-412c-9094-efa80f4b8a65)

Comprobaremos que nos ha creado la imagen:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/adc97062-ac3d-4e04-a1d3-cc2632bf5886)

Crearemos el contenedor de docker:

```
docker run -d -p 80:80 --name ejemplo2 antonio/ejemplo2:v1
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/27c416d3-c05d-4e96-82eb-e20d6b3f6520)

Y si todo ha salido correcto nos aparecerá:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/a373e9c5-ceab-4ddc-bc53-4c8acd433462)

### Ejemplo 3: Construcción de imágenes con una una aplicación Python

Vamos a tener el fichero Dockerfile y un directorio, llamado app con nuestra aplicación.

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/ff0b063e-cd46-4991-8649-a66e7298821c)

Añadiremos el siguiente contenido al dockerfile:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/68460401-e25c-41b2-8d5f-9d9e40a74185)

Para crear la imagen ejecutamos:

```
docker build -t antonio/ejemplo3:v1 .
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/3b123100-4ae5-4e0c-b90b-b527263b0417)

Crearemos el contenedor de docker:

```
docker run -d -p 80:80 --name ejemplo3 antonio/ejemplo3:v1
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/15406efc-8844-4a29-aeba-b0da54cff0b8)

Y si todo ha salido correcto nos aparecerá:
















