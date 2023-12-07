
## Script 1:

Crea un script que añada un puerto de escucha en el fichero de configuración de Apache. El puerto se recibirá como parámetro en la llamada y se comprobará que no esté ya presente en el fichero de configuración
        
        #!/bin/bash
        
        # Verificar si se proporciona un puerto como argumento
        if [ -z "$1" ]; then
            echo "Uso: $0 <puerto>"
            exit 1
        fi
        
        puerto=$1
        archivo_configuracion="/etc/apache2/apache2.conf"  # Ajusta la ruta según la configuración de tu sistema
        
        # Verificar si el puerto ya está presente en el archivo de configuración
        if grep -q "Listen $puerto" "$archivo_configuracion"; then
            echo "El puerto $puerto ya está presente en el archivo de configuración."
        else
            # Añadir el puerto al archivo de configuración
            echo "Listen $puerto" | sudo tee -a "$archivo_configuracion" > /dev/null
            # Reiniciar Apache para aplicar los cambios
            sudo systemctl restart apache2  # Ajusta el comando según la gestión de servicios de tu sistema
            echo "Se ha añadido el puerto $puerto al archivo de configuración de Apache y se reinició Apache."
        fi
