## Actividad 2: Docker 

**Parte 1:**

**1- Ejecuta la imagen "hello-world"**

Ejecutaremos la imagen con el siguiente comando:

```
docker run hello-world
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/667da268-a538-42e7-a5fe-6ca44a89458c)

 
**2- Muestra las imágenes Docker instaladas**

Para mirar las imagenes instaladas usaremos:

```
sudo docker images
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/d30cd4b4-4f8c-407c-ae57-8cf20bcc5ff5)

 
**3- Muestra los contenedores Docker**

Para mostrar los contenedores usaremos: 

```
sudo docker ps -a
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/a9e3d037-7615-4abc-a743-c05499b95401)

**Parte 2:** 

**1- Edita el fichero Dockerfile**

Siguiendo la guia, clonaremos un repositorio que nos cree una carpeta:

```
git clone https://github.com/docker/getting-started.git
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/cee25007-9743-4074-a088-6dc671cc3e42)

Ahora entraremos en la ruta de la carpeta ejecutando los siguientes comandos:

```
cd getting-started
```

```
touch Dockerfile
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/f0c3bf5b-21e7-4a8a-be5c-4d1c26fbb21e)

Y editaremos el archivo añadiendo lo siguiente:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/aa614bbe-8ca5-403b-9047-74fa5a19406c)


**2- Construye el contenedor**

Construiremos el contenedor utilizando docker build:

```
docker build -t getting-started .
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/90388ed3-8e1e-40ee-acf1-a6fe888acee4)


**3- Ejecútalo**

Lo ejecutaremos usando:

```
docker run -dp 127.0.0.1:3000:3000 getting-started
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/dd0c0fc3-1cbc-41b3-b08f-25cb79d10688)

**4- Create una cuenta en hub.docker.com**

Crearemos una cuenta en docker hub, en otra asignatura ya tuve que crear una cuenta, usaré la misma para subir la imagen:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/ea530312-49f2-4aa5-ab06-3d96ddb6c89d)


**5- Publícalo**

Primero iniciaremos sesion usando:

```
sudo docker login
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/529e7ce0-fa42-4988-9898-015f47119961)

Le añadiremos un tag:

```
docker tag getting-started elanotio/imagen-getting
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/5a388da2-13cc-48a7-be8f-d5cdca451819)

Ahora la subiremos con:

```
docker push elanotio/imagen-getting
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/73f8fcb9-a7f6-4648-8c78-d854ff09e709)

Si nos vamos a nuestra cuenta, comprobaremos que está subida:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/ce72b0aa-6cdb-4f38-8799-591132de03cd)





