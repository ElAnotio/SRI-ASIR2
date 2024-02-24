## Actividad 4: ProFTPd privado y anónimo

##Actividades:

1- Configura proftpd para que los usuarios accedan al directorio /home/ftp (puedes usar DefaultChdir). ¿Cual es la diferencia entre DefaultRoot y DefaultChdir?

2- No se permitirá subir ni eliminar nada de la carpeta ftp

3- Configura el acceso mediante usuario anónimo

4- Permite que el usuario anónimo pueda escribir si accede desde la red 10.6.0.x

### Instalación de servicios:

Primero antes que nada, tendremos que instalar los servicios:

**ProFtpd**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/8ee99d42-e10c-430a-9162-642f4574c7f8)

Verificamos que proftpd está en ejecución:


![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/d28c775d-f116-42db-ae2f-ca8d6fdc527e)


**BIND9:**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/405a8bbc-a871-4ed4-911a-eb0288a414c5)

### Configurar archivo Proftpd:

**sudo nano /etc/proftpd/proftpd.conf**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/4dc74ce3-0e37-4e77-9d64-9441af23a3cb)

Lo editaremos de la siguiente forma según dicta el ejercicio:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/766b8028-56ff-4acb-a656-c968229f7f5c)

Luego reinicia el servicio para aplicar los cambios:

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/4fc85255-124f-4495-adb3-9570abdf37ff)










