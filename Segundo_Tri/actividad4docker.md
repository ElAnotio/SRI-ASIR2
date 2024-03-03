## Practica 4:

**Lleva a cabo al menos tres de los ejemplos mostrados en el módulo y documentalo en tu repositorio incluyendo capturas de pantalla.**

### 1º Ejemplo: Despliegue de la aplicación Guestbook

Primero descargaremos las dos imagenes propuestas:

```
docker pull iesgn/guestbook
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/bbddf081-6b6b-495a-a910-ef726d4df469)

```
docker pull redis
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/9c4cdc66-2801-45a0-8606-b9c8b126850b)

Ahora crearemos la red para meter los dos contenedores y que estén en la misma red:

```
docker network create red_guestbook
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/d7519f2c-a9b5-436f-85aa-4c00ec1f18ab)

Ahora ejecutaremos los contenedores con los siguientes parametros:

```
docker run -d --name redis --network red_guestbook -v /opt/redis:/data redis redis-server --appendonly yes
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/c010e698-0ce5-48df-b2f0-bea87e0ca49f)

```
$ docker run -d -p 80:5000 --name guestbook --network red_guestbook iesgn/guestbook
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/ed289f56-68dc-4e6d-b4fb-7b6905ade079)

Si lo ejecutamos todo, cuando pongamos en el navegador nuestra ip o localhost aparecerá lo deseado:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/8c13c910-d9b5-4b8c-a83c-cb4b8701e751)

### 2º Ejemplo: Despliegue de la aplicación Temperaturas

Para el segundo ejemplo, crearemos la red red_temperaturas:

```
docker network create red_temperaturas
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/0d35bc4a-dafa-4c4d-8e87-dc33acb77e2b)

Y ahora ejecutaremos los contenedores con frontend y backend:

```
docker run -d --name temperaturas-backend --network red_temperaturas iesgn/temperaturas_backend
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/fe74ce99-3d10-4018-ad82-f466fabae920)

```
docker run -d -p 80:3000 --name temperaturas-frontend --network red_temperaturas iesgn/temperaturas_frontend
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/fb9cc3ba-0ae9-4f25-ae70-b0cb47c862ec)

Si todo lo hemos hecho correctamente nos deberá aparecer al poner nuestra ip:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/9a8074f6-5860-4a46-b745-e2fc65b61588)


