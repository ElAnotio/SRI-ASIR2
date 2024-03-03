## Actividad 3 

**1- Descarga la imagen de ubuntu**

```
sudo docker pull ubuntu
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/8ac12cd2-32d3-4766-9a21-79818c270756)

**2- Descarga la imagen de hello-world**

```
sudo docker pull ubuntu
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/424d97ef-e2aa-4c98-a519-698dc9fb9a6e)

**3- Descarga la imagen nginx**

```
sudo docker pull ubuntu
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/738bc0b2-63cc-4f48-87fb-f7f1416e9506)

**4- Muestra un listado de todas la imágenes**

```
sudo docker images
```
![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/de0643cd-095a-4a3f-88d8-5898c6486ae8)

**5- Ejecuta un contenedor hello-world y dale nombre “myhello1”**

```
sudo docker run --name myhello1 hello-world
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/fce1040e-6dc4-4457-97a1-52f4077542f3)

**6- Ejecuta un contenedor hello-world y dale nombre “myhello2”**

```
sudo docker run --name myhello2 hello-world
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/6dfbf67a-59da-484b-a734-e6ebb64e0312)


**7- Ejecuta un contenedor hello-world y dale nombre “myhello3”**

```
sudo docker run --name myhello3 hello-world
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/0cba3087-8b58-49a6-b272-9984e4acff88)

**8- Muestra los contenedores que se están ejecutando**

```
sudo docker ps -a
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/903caf91-7fb7-4a4f-a97d-903a7df0ed40)

**9- Para el contenedor "myhello1”**

```
sudo docker stop myhello1
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/5b0d1369-d537-471b-89e2-f7e7d48a899b)

**10- Para el contenedor "myhello2”**

```
sudo docker stop myhello2
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/f4b36484-7af6-4124-9f72-96ac5cefc5e2)

**11- Borra el contenedor “myhello1”**

```
sudo docker rm myhello1
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/41c43a8b-1638-43c7-8a40-88c74a592af9)

**12- Muestra los contenedores que se están ejecutando.**

```
sudo docker ps -a
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/c909c2bc-94ba-402c-9fca-a6964a4023ea)

**13- Borra todos los contenedores**

Para borrarlos tendremos que hacerlo desde sudo su:

```
docker stop $(docker ps -a -q)
```

```
docker rm $(docker ps -a -q)
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/3b11a639-c0c1-45e7-818d-69ece5548d71)

Si hacemos un ps -a:

```
sudo docker ps -a
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/c71150d3-2967-4def-87f0-d640f9d96d9b)


