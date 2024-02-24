## Actividad 5: ProFTPd - Virtual Host

### Actividad 1: 

Crea un directorio para el usuario virtual “informatica” en /home/ftp/informatica

```
sudo mkdir /home/ftp/informatica
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/cacc0513-f2c3-4cf9-a9d0-0b3b3fb03863)

### Actividad 2:

Cambia el propietario del directorio creado anteriormente mediante “chown” al usuario ftp

```
sudo chown ftp:ftp /home/ftp/informatica
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/a2303550-b2e6-47a1-b02a-810480009303)


### Actividad 3:

Crea un usuario virtual “informatica” mediante “ftpasswd”

```
sudo ftpasswd --passwd --file=/etc/proftpd/ftpd.passwd --name=informatica --uid=1001 --gid=1001 --home=/home/ftp/informatica --shell=/bin/false
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/0a12c172-ba61-4411-ad7b-f59224472002)

Hemos puesto de contraseña : 1234

### Actividad 4:

```
sudo nano /etc/proftpd/proftpd.conf
```

Haz los cambios necesarios en el fichero de configuración de proftpd

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/04aca9b1-de57-4711-a675-eebe3c0064c8)

### Actividad 5:

Crea un sitio virtual para “informatica.marisma.local”


### Actividad 6:
Modifica el fichero de zona del DNS para que resuelva adecuadamente

