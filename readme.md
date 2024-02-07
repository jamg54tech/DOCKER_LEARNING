#COMANDOS BASICOS DE DOCKER

docker run image_name --> descarga, en caso de que no exista, y ejecuta una imagen del docker hub

docker pull image_name ---> solo descarga una imagen del docker_hub

docker images ---> muestra las imagenes que se tienen instaladas

docker ps -----> muestra los contenedores en ejecución

docker ps te permite ver [CONTAINER_ID]

docker login ----sirve para iniciar sesion en docker

docker network create [nombre-red] --- sirve para crear una red donde corran mas de 1 contenedor


### flags disponibles de docker run
docker run
-d #indica que el contenedor debe correr en background
--network [nombre-red] --[network_alias] [alias-red] #indica al contenedor el nombre de la red donde debe correr
-v [ruta_directorio_local_a_crear]:[ruta_del_contenedor_que_va_a_leer_la_ruta_local]
-p [mipuertolocal]:[puertocontenedor] permite que las aplicaciones de dcoker que usen un puerto puedan comunicarse con el puerto de mi equipo local

docker stop [CONTAINER_ID]  ----- detiene la ejecución de un contenedor

docker exec -it [CONTAINER_ID] [comando]  ---- ejecuta un [comando] dentro del contenedor con [CONTAINER_ID]

dig [network_alias] ---- perite listar los contenedores que estan corriendo en una red con alias [network_alias]

###### ESCRIBIENDO UN DOCKER FILE

vim DockerFile

FROM nombre_imagen_fuente #Indica la imagen padre

WORKDIR /ruta #crea la ruta de trabajo que se va a generar en el contenedor

#COPY (RUTA DOCKER FILE) (RUTA DEL CONTENDOR DONDE SE VAN A COPIAR LOS ARCHIVOS DE LA CARPETA DONDE ESTA EL DOCKER FILE)
COPY . . #EL PRIMER PUNTO HACE REFERENCIA A LA CARPETA DONDE ESTÁ EL DOCKER FILE Y EL SEGUNDO PUNTO A LA CARPETA DEL WORKDIR \ruta
RUN yarn install --production #RUN INDICA UN COMANDO QUE QUEREMOS SEA EJECUTADO

CMD ["comando","parametros"] #comando que se va a correr al ejecutar la imagen en un contenedor



###### GENERAR UNA IMAGEN A PARTIR DE UN DOCKER FILE
docker build -t nombre_imagen [ruta_donde_este el docker_file]

docker build -t nombre_imagen . # ejemplo de cuando el docker file esta en la misma carpeta


##### GENERAR IMAGEN LUEGO DE HACERLE CAMBIOS

docker build -t nombre_imagen:[tag] [ruta_donde_este el docker_file]
