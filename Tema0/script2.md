## Script 2:

Crea un script que añada un nombre de dominio y una ip al fichero host. Debemos comprobar que no existe dicho dominio

      #!/bin/bash
      
      # Verificar si se proporciona un nombre de dominio y una IP como argumentos
      if [ -z "$1" ] || [ -z "$2" ]; then
          echo "Uso: $0 <nombre_de_dominio> <ip>"
          exit 1
      fi
      
      dominio=$1
      ip=$2
      archivo_hosts="/etc/hosts"
      
      # Verificar si el dominio ya está presente en el archivo de hosts
      if grep -qE "^[[:space:]]*$ip[[:space:]]+$dominio[[:space:]]*" "$archivo_hosts"; then
          echo "El dominio $dominio ya está presente en el archivo de hosts."
          exit 1
      fi
      
      # Añadir el dominio y la IP al archivo de hosts
      echo "$ip $dominio" | sudo tee -a "$archivo_hosts" > /dev/null
      
      echo "Se ha añadido el dominio $dominio con la IP $ip al archivo de hosts."
