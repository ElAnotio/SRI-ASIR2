## Actividad 5: Directiva Directory

**1.Crea un directorio llamado "dir1" y otro llamado "dir2"**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/0a28506d-f1dd-4bc1-b999-b8d9bd2f194b)
	
**2.Explica qué diferencia existe entre ambos.:**

    <Directory /var/www/example1>
    Order Deny,Allow
    Deny from All
    Allow from 192.168.1.100
    </Directory>
    
    <Directory /var/www/example1>
    Order Allow,Deny
    Deny from All
    Allow from 192.168.1.100
    </Directory>

En el caso de Order Deny,Allow:

La regla Deny from All niega el acceso a todos por defecto.
La regla Allow from 192.168.1.100 posteriormente permite específicamente el acceso solo desde la dirección IP 192.168.1.100.
En el caso de Order Allow,Deny:

Aunque la regla Deny from All intenta negar el acceso a todos, la regla Allow from 192.168.1.100 se evalúa primero, permitiendo explícitamente el acceso desde la dirección IP 192.168.1.100. Esto anula la regla Deny.
		
**3. Para dir1**
  **a. Permite el acceso de las peticiones provenientes de 10.3.0.100**

  **b. Permite el acceso desde "marisma.intranet"**

  **c. Permite el acceso desde cualquier subdominio de "marisma.intranet"**

  **d. Permite el acceso de las peticiones provenientes de "10.3.0.100" con máscara "255.255.0.0"**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/54418325-4ef4-4e77-802e-dd9492ef02a8)

La directiva Require ip permite el acceso desde una dirección IP específica.

La directiva Require host permite el acceso desde un nombre de host.

La notación Require host .marisma.intranet con un punto delante permite el acceso desde cualquier subdominio de marisma.intranet.

La notación Require ip 10.3.0.100/255.255.0.0 especifica la máscara de red junto con la dirección IP para permitir un rango de direcciones IP.


**4. Modifica la configuración de forma que el acceso a dir1:**
  **a. Se permita a "marisma.intranet" y no se permita desde 10.3.0.101"**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/43322164-4e33-4bfb-a92e-39eff51dac33)

La directiva Require not ip niega el acceso desde una dirección IP específica.
 
**5. Modifica la configuración de forma que el acceso a dir2:**
  **a.Se permita a "10.3.0.100/8" y no a "marisma.intranet"**

![image](https://github.com/ElAnotio/SRI-ASIR2/assets/122453991/38d70efd-6d0d-4ed3-b673-c7e36276f093)

  
