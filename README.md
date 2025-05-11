# Examen-3
Examen 3 telematica 

PASO A PASO: Desplegar juego Buscaminas en HTML usando Docker en una instancia Ubuntu

# 1. CONECTARSE A LA INSTANCIA SSH

### ssh -i "llave.pem" ubuntu@ip-publica-instancia

Esto establece una conexion remota con tu servidor.

--------------------------------

# 2. ACTUALIZAR EL SISTEMA

### sudo apt-get update
### sudo apt-get upgrade -y

Actualiza la lista de paquetes y los instala.

------------------------

# 3. INSTALAR DOCKER

### sudo apt-get install docker.io -y
### sudo systemctl start docker
### sudo systemctl enable docker

Instala Docker y lo deja activo permanentemente.

------------------

# 4. CREAR CARPETA DEL PROYECTO

### mkdir busca-minas
### cd busca-minas

Crea una carpeta para trabajar y se ubica dentro de ella.

-----------------------------

# 5. CREAR EL DOCKERFILE

### nano Dockerfile

Dentro del Dockerfile, escribe lo siguiente:

FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html

Guarda el archivo con Ctrl + S y sal con Ctrl + X.

----------------------

# 6. CREAR EL ARCHIVO HTML

### sudo nano index.html

Pega aqui el HTML de tu juego Buscaminas. Guarda y cierra.

### El juego estara hecho con HTML y JavaScript, y ademas usara el servidor Web Nginx para poder correr el juego.
Usara especificamente Nginx alpine, que es una versión ligera del servidor Nginx como base.

------------------------

# 7. CONSTRUIR LA IMAGEN DOCKER

### sudo docker build -t busca-minas-html .

Construye la imagen con nombre "busca-minas-html" basada en tu Dockerfile.

-----------------------------

# 8. EJECUTAR EL CONTENEDOR

### sudo docker run -d -p 80:80 --restart unless-stopped --name snake-game snake-game

La parte de "--restart unless-stopped" reinicia el contenedor automaticamente si se cae,
osea que cada que apagues la instancia y quieras volver a iniciar el busca minas, solo tendras que encender la intancia y se activara automaticamente.

Ejecuta el contenedor en segundo plano y lo expone al puerto 80.

-------------------------

# RESULTADO FINAL

Puedes abrir un navegador y visitar: http://[IP-PuBLICA-DE-TU-SERVIDOR]
Ahi veras el juego Buscaminas en funcionamiento.

---------------

