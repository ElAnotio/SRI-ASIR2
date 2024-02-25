## Actividad 6: ProFTPd - TLS

### Actividad 1: 

**Instala filezilla**

Usaremos el comando 
```
sudo apt install filezilla 
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/2fed77f0-0f9c-40b5-b0f3-920392014b73)

### Actividad 2: 

**Configura filezilla para usar una conexión TLS y comprueba que funciona correctamente.**

Primero, iremos al archivo **proftpd.conf** y desmarcaremos el comentacio de incluir tls.conf

```
sudo nano /etc/proftpd/proftpd.conf
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/a2707828-86b8-4ad5-970d-b28ee5f13432)

Después nos iremos a modules.conf y desmarcaremos las siguientes lineas:

```
sudo nano /etc/proftpd/modules.conf
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/3f2dcb20-2651-4e18-9ca7-49dfd655c2fb)

Después instalaremos el siguiente servicio:

```
sudo apt isntall proftpd-mod-crypto
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/41df62fe-c307-4700-8646-2dbaa7c1d431)

Después de instalarlo, editaremos el archivo tls.conf y desmarcamos los siguientes enunciados:

```
sudo nano /etc/proftpd/tls.conf
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/0b6d0641-a540-402b-b7ef-5a516498bbf6)

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/4e0093dc-b320-4a01-805c-d9292ac70468)

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/00f0f097-842e-4e59-b496-1b38885455a5)

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/8c2dbf68-e27d-4111-9158-4f7913b2ce59)

Una vez desmarcados, reiniciamos el servicio proftpd

```
sudo systemctl restart proftpd
```

Después de reiniciar, usaremos el comando para general un certificado de seguridad, cogeremos el comando de tls.conf 

```
sudo nano /etc/proftpd/tls.conf
```

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/db7d1d47-2b73-4fdd-ae36-528ff9522de5)

Lo usaremos y contestaremos a las preguntas:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/cc9d4671-7364-41b4-beae-57fd6aae88fe)

Después conectaremos con el filezilla con la siguiente configuración:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/8db1f349-756e-48e9-96ad-65f31657b646)

Si comprobamos toda la configuración, nos aparecerá el certificado creado anteriormente y tendremos hecho nuestra comunicacion con TLS:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/404e6ab6-d3fd-4825-ad22-7d90acf54096)

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/4120607c-007e-4918-aa36-64793f092bcf)

