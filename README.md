# Hadoop-Mio
ejemplos de hadoop 
# PRE REQUISITOS
Tener instalado docker Desktop 
## Levantar contenedor
ejecutar lo siguiente [docker-compuse up -d]
verificamos si se estan los contenedores ejecutandose [docker ps]
para entrar en nuestro contedor usamos [docker exec -it namenode bash]
## Estructura para carpetas de archivos de entrada 
entramos al nodo maestro  [docker exec -it namenode bash]
luego ejecutamos [hdfs dfs -1s /]
creamos la carpeta con [hdfs dfs -mkdir -p /user/root/]
verificamos [hdfs dfs -1s /user/]
## EJEMPLOS
## CREDITOS https://gist.github.com/jsdario/6d6c69398cb0c73111e49f1218960f79#file-el_quijote-txt 
# Descargar un script de ejemplo MapReduce
https://repo1.maven.org/maven2/org/apache/hadoop/hadoop-mapreduce-examples/2.7.1/
descargar [hadoop-mapreduce-examples-2.7.1-sources.jar ]
mover archivo [hadoop-mapreduce-examples-2.7.1-sources.jar] a la misma carpeta  docker-hadoop.
descargar y descomprimir [el_quijote.txt] a la misma carpeta docker-hadoop.
## Copiar los archivos .jar y .txt al contenedor
usar estos comandos para los archvios 
[docker cp hadoop-mapreduce-examples-2.7.1-sources.jar namenode:/tmp]
[docker cp el_quijote.txt namenode:/tmp ]
## crear carpeta de entrada a contenedor
[docker exec -it namenode bash]
luego [
hdfs dfs -mkdir /user/root/input_contador] 
## copiar archivo txt
[cd /tmp]
luego [hdfs dfs -put el_quijote.txt /user/root/input_contador]
por ultimo usar este comando
[
hadoop jar hadoop-mapreduce-examples-2.7.1-sources.jar org.apache.hadoop.examples.WordCount input_contador output_contador]
ver resuñtado
[hdfs dfs -cat /user/root/output_contador/*]
comprovar
[hdfs dfs -ls /user/root/output_contador]
## guardar el contador
[
hdfs dfs -cat /user/root/output_contador/part-r-00000 > /tmp/quijote_wc.txt]
luego
[ exit]
y luego
[docker cp namenode:/tmp/quijote_wc.txt .]
## resultado
el archivo quijote_wc.txt que se encuentra en la carpeta docker-hadoop.
## ejemplo de temperaturas
descargar archivo y descomprima 
https://github.com/Rkrahul04/Maximum_Temp_Calculation_mapreduce/blob/master/Dataset%20-%20Calculate%20Maximum%20Temperature/Temperature
mover el archivo [Temperature.txt] a la misma carpeta docker-hadoop.
## Copiar los archivos .jar y .txt al contenedor
si ya tienes [hadoop-mapreduce-examples-2.7.1-sources.jar] salta ese paso
el archivo [Temperature.txt] usar [docker cp Temperature.txt namenode:/tmp]
## crea la carpeta de entrada dentro del contenedor
[docker exec -it namenode bash]
[hdfs dfs -mkdir /user/root/input_temperaturas]
## Ejecutar MapReduce
[
hadoop jar hadoop-mapreduce-examples-2.7.1-sources.jar org.apache.hadoop.examples.SecondarySort input_temperaturas output_temperaturas]
resultado
[hdfs dfs -cat /user/root/output_temperaturas/*]
comprobar
[hdfs dfs -ls /user/root/output_temperaturas]
ejecutar 
[
hdfs dfs -cat /user/root/output_temperaturas/part-r-00000 > /tmp/temperaturas_ordenadas.txt]
luego [exit] y luego [docker cp namenode:/tmp/temperaturas_ordenadas.txt .]
## ejemplo de sudoku

