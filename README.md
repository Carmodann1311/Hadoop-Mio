# Hadoop-Mio
ejemplos de hadoop 
#PRE REQUISITOS
Tener instalado docker Desktop 
##Levantar contenedor 
ejecutar lo siguiente [docker-compuse up -d]
verificamos si se estan los contenedores ejecutandose [docker ps]
para entrar en nuestro contedor usamos [docker exec -it namenode bash]
##Estructura para carpetas de archivos de entrada 
entramos al nodo maestro  [docker exec -it namenode bash]
luego ejecutamos [hdfs dfs -1s /]
creamos la carpeta con [hdfs dfs -mkdir -p /user/root/]
verificamos [hdfs dfs -1s /user/]
##EJEMPLOS
#CREDITOS https://gist.github.com/jsdario/6d6c69398cb0c73111e49f1218960f79#file-el_quijote-txt 
