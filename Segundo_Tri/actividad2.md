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

```
sudo nano /etc/apache2/sites-available/informatica.marisma.local.conf
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/2e846330-e0b7-4232-a567-6a13973bec4c)

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/b3a83dae-1c40-423d-8e9e-4d94c0001651)


### Actividad 6:
Modifica el fichero de zona del DNS para que resuelva adecuadamente

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/4be4bf41-434a-43e4-9891-5225e5600add)

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/14ba025b-f08d-4757-9b34-f55d37bae729)

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/c4a334e8-ca23-4be1-83d5-d1267cd06bb6)

### Comprobación  

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/4bd6b6d0-31c9-47bb-b3b8-0ee7411e19e2)

