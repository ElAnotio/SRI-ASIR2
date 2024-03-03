## Actividad 5: 

**Lleva a cabo al menos tres de los ejemplos mostrados en el módulo y documentalo en tu repositorio incluyendo capturas de pantalla.**

### Ejemplo 1: Despliegue de la aplicación guestbook

Primero, crearemos un archivo compose: 

```
nano docker-compose.yml
```
Y escribiremos el siguiente contenido:

```
version: '3.1'
services:
  app:
    container_name: guestbook
    image: iesgn/guestbook
    restart: always
    environment:
      REDIS_SERVER: redis
    ports:
      - 8080:5000
  db:
    container_name: redis
    image: redis
    restart: always
    command: redis-server --appendonly yes
    volumes:
      - redis:/data
volumes:
  redis:
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/70c37499-360a-490a-9922-1bc93efe3ad7)

Ejecutaremos el compose para que añada los contenedores:

```
docker compose up -d
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/364b5628-e722-4d65-942a-b6e9dd48c3fa)

Para listar los contenedores usaremos:

```
docker compose ps
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/2ddf6f6a-0553-451c-b989-867bd24f7c9d)

Para parar los contenedores:

```
docker compose stop
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/054201b7-4a13-4720-af47-25d159bef61f)

Para eliminar el escenario:

```
docker compose down
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/bd8bcc91-1f3e-4a0b-9dff-8d6893da95a7)

### Ejemplo 2: Despliegue de la aplicación Temperaturas

Primero, crearemos un archivo compose: 

```
nano docker-compose.yml
```
Y escribiremos el siguiente contenido:

```
version: '3.1'
services:
  frontend:
    container_name: temperaturas-frontend
    image: iesgn/temperaturas_frontend
    restart: always
    ports:
      - 8081:3000
    environment:
      TEMP_SERVER: temperaturas-backend:5000
    depends_on:
      - backend
  backend:
    container_name: temperaturas-backend
    image: iesgn/temperaturas_backend
    restart: always
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/b837e90a-30d4-4754-80b1-154f3e276981)

Levantaremos el escenario con:

```
docker compose up -d
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/15086477-4cb1-4187-8a11-f20d173007d8)

Para listar los contenedores usaremos:

```
docker compose ps
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/aeacf461-afb3-4cd9-bea0-a8df160939bf)

### Ejemplo 3: Despliegue de WordPress + Mariadb

Primero, crearemos un archivo compose: 

```
nano docker-compose.yml
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/9d92ffe0-9d87-4d1b-b116-4ab58e4b0fdd)

Levantaremos el escenario con:

```
docker compose up -d
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/df4a7c25-ff24-4289-bdbc-5491125d21b2)

Para listar los contenedores usaremos:

```
docker compose ps
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/4e1dce19-b0f8-4a74-b660-b1b6ffb49acb)



