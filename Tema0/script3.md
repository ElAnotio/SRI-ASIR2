## Script 3:

Crea un script que nos permita crear una página web con un título, una cabecera y un mensaje

      #!/bin/bash
      
      # Verificar si se proporciona un nombre de archivo como argumento
      if [ -z "$1" ]; then
          echo "Uso: $0 <nombre_de_archivo.html>"
          exit 1
      fi
      
      nombre_archivo="$1"
      
      # Verificar si el archivo ya existe
      if [ -e "$nombre_archivo" ]; then
          echo "El archivo $nombre_archivo ya existe. Por favor, elige un nombre de archivo diferente."
          exit 1
      fi
      
      # Crear la página HTML
      cat <<EOL > "$nombre_archivo"
      <!DOCTYPE html>
      <html lang="es">
      <head>
          <title>Titulo</title>
      </head>
      <body>
      
          <header>
              <h1>Esto es el titulo</h1>
          </header>
      
          <main>
              <p>Esto es el contenido, viva pikachu</p>
          </main>
      
      </body>
      </html>
      EOL
      
      echo "Se ha creado la página web en el archivo $nombre_archivo."
