# Ejercicios_Linux

Listar todos los archivos del directorio bin.

ls /bin

Listar todos los archivos del directorio tmp.

ls /tmp

Listar todos los archivos del directorio etc que empiecen por t en orden inverso.

ls -dr /etc/t*

Listar todos los archivos del directorio dev que empiecen por tty y tengan 5 caracteres.

ls /dev/tty??

Listar todos los archivos del directorio dev que empiecen por tty y acaben en 1,2,3 ó 4.

ls /dev/tty*[1-4]

Listar todos los archivos del directorio dev que empiecen por t y acaben en C1.

ls /dev/t*C1

Listar todos los archivos, incluidos los ocultos, del directorio raíz.

ls -a /

Listar todos los archivos del directorio etc que no empiecen por t.

ls -d /etc/[^t]*

Listar todos los archivos del directorio usr y sus subdirectorios.

ls -R /usr

Cambiarse al directorio tmp, crear directorio PRUEBA.

cd /tmp 
mkdir PRUEBA

Verificar que el directorio actual ha cambiado.

 pwd

Mostrar el día y la hora actual.

DATE

Con un solo comando posicionarse en el directorio $HOME.

 cd /HOME

Verificar que se está en él.

 pwd

Listar todos los ficheros del directorio HOME mostrando su número de inodo.

 ls -i

Borrar todos los archivos y directorios visibles de vuestro directorio PRUEBA.

rm -rf PRUEBA/*

Crear los directorios dir1, dir2 y dir3 en el directorio PRUEBA. Dentro de dir1 crear el directorio dir11. Dentro del directorio dir3 crear el directorio dir31. Dentro del directorio dir31, crear los directorios dir311 y dir312.

touch PRUEBA/{.f_hidden1,.f_hidden2,.f_hidden3}
touch PRUEBA/{file1,file2,file3}
mkdir PRUEBA/{dir1,dir2,dir3}
mkdir PRUEBA/{ dir1,\
 dir1/dir11,\
 dir2,\
 dir3,\
 dir3/dir31,\
 dir3/dir31/dir311,\
 dir3/dir31/dir312}

Copiar el archivo /etc/motd a un archivo llamado mensaje de vuestro directorio PRUEBA.

cp /etc/motd ./PRUEBA/mensaje

Copiar mensaje en dir1, dir2 y dir3.

cd PRUEBA
cp mensaje dir1/mensaje && cp mensaje dir2/mensaje && cp mensaje dir3/mensaje

Comprobar el ejercicio anterior mediante un solo comando.

 ls -R PRUEBA

Copiar los archivos del directorio rc.d que se encuentra en /etc al directorio dir31.

 cp -r /etc/rc.d dir3

Copiar en el directorio dir311 los archivos de /bin que tengan una a como segunda letra y su nombre tenga cuatro letras.

cp -r /bin/?a?? PRUEBA/dir3/dir31/dir311

Copiar el directorio de otro usuario y sus subdirectorios debajo de dir11 (incluido el propio directorio).

sudo cp -r ../user_other PRUEBA/dir1/dir11
cp -r ../user PRUEBA/dir1/dir11

Mover el directorio dir31 y sus subdirectorios debajo de dir2.

mv PRUEBA/dir3/dir31 PRUEBA/dir2

Mostrar por pantalla los archivos ordinarios del directorio HOME y sus subdirectorios.

ls -R $HOME

Ocultar el archivo mensaje del directorio dir3.

mv PRUEBA/dir3/mensaje PRUEBA/dir3/.mensaje

Borrar los archivos y directorios de dir1, incluido el propio directorio.

rm -rf PRUEBA/dir1

Copiar al directorio dir312 los ficheros del directorio /dev que empiecen por t, acaben en una letra que vaya de la a a la b y tengan cinco letras en su nombre.

ls /dev/t???[a*b]

Borrar los archivos de dir312 que no acaben en b y tengan una q como cuarta letra.

find dir312 -type f -regex ".*???q[^b$]" -exec rm -r {} \;

Mover el directorio dir312 debajo de dir3.

mv PRUEBA/dir2/dir31/dir312 PRUEBA/dir3

Crear un enlace simbólico al directorio dir1 dentro del directorio dir3 llamado enlacedir1.

ln -s /home/usuario1/PRUEBA/dir1 PRUEBA/dir3/enlacedir1

Posicionarse en dir3 y, empleando el enlace creado en el ejercicio anterior, crear el directorio nuevo1 dentro de dir1.

cd PRUEBA/dir3 
mkdir enlacedir1/nuevo1

Utilizando el enlace creado copiar los archivos que empiecen por u del directorio /bin en directorio nuevo1.

cp -r /bin/u* enlacedir1/nuevo1/

Crear dos enlaces duros del fichero fich1, llamarlo enlace, en los directorios dir1 y dir2.

ln fich1 dir1/enlace
ln fich1 dir2/enlac

Borrar el archivo fich1 y copiar enlace en dir3.

rm fich1 
cp dir1/enlace dir3/ 
ln -s /home/usuario1/PRUEBA/dir2/enlace /home/usuario1/PRUEBA/dir1/enlafich1

Crear un enlace simbólico (llamado enlafich1) al fichero enlace de dir2 en dir1.

ln -s dir2/enlace dir1/enlafich1

Posicionarse en dir1 y, mediante el enlace creado, copiar el archivo fichl dentro de dir311.

cd dir1 dir1
cp enlafich1 ../dir2/dir31/dir311/fich1

Seguir en dir1 y, mediante el enlace creado, sacar por pantalla las líneas que tiene el archivo fich1.

dir1$ cat enlafich1

Borrar el fichero fich1 de dir2.

PRUEBA$ rm dir2/fich1

Borrar todos los archivos y directorios creados durante los ejercicios.

rm -r *

Crear el directorio dir2 y dir3 en el directorio PRUEBA ¿Cuáles son los actuales permisos del directorio dir2?

mkdir dir1 dir2

Utilizando la notación simbólica, eliminar todos los permisos de escritura (propietario, grupo, otros) del directorio dir2.

chmod = dir1

Utilizando la notación octal, eliminar el permiso de lectura del directorio dir2, al resto de los usuarios.

chmod 751 dir2

¿Cuáles son ahora los permisos asociados a dir2?

ls -la ./dir2

Crear bajo dir2, un directorio llamado dir2l.

mkdir dir2/dir21  no se puede crea

Concederse a sí mismo permiso de escritura en el directorio dir2 e intentar de nuevo el paso anterior.

chmod 200 dir1 
ls -l 
mkdir dir1/dir21 mkdir: no se puede crear el directorio «dir1/dir21»: Permiso denegado

¿Cuáles son los valores por omisión asignados a los archivos?

touch dir1/{file1,file2,file3} 
PRUEBA$ ls -l dir

Cambiar el directorio actual al directorio dir3. Imprimir su trayectoria completa para verificar el cambio.

ls  dir1  dir2  dir3 
mv dir1 dir3/ 
ls -lR
 .:  
 ./dir2:  
 ./dir2/dir21:  
 ./dir3:  
 ./dir3/dir1:

¿Cuáles son los permisos asignados en su momento a este directorio?

./dir3:

Reiniciar el ordenador.

sudo reboot

Crear cuatro nuevos directorios llamados dira, dirb, dirc, y dird bajo el directorio actual.

mkdir dira dirb dirc dird

Comprobar los permisos de acceso de los directorios recién creados para comprobar el funcionamiento del comando umask.

ls -l

Crear el fichero uno . Quitarle todos los permisos de lectura. Comprobarlo. Intentar borrar dicho fichero.

touch uno 
chmod a-r uno 
ls -l 
rm uno 
_

Quitarle todos los permisos de paso al directorio dir2 y otorgarle todos los demás.

chmod = dir2 
chmod o=rwx dir2

Crear en el directorio propio:
El directorio carpeta1 con los tres permisos para el propietario, dentro de él fich1 con lectura y escritura para todos y fich2 con lectura y escritura para el propietario y solo lectura para el resto. El directorio carpeta2 con todos los permisos para el propietario y lectura y ejecución para los del mismo grupo. Dentro file1 con lectura y escritura para el propietario y los del grupo y file2 con los mismos para el propietario y solo lectura para el grupo.

mkdir carpeta1 carpeta2 
chmod u=rwx,g=,o=   carpeta1 
chmod u=rwx,g=rx,o= carpeta2 
ls -l $ touch carpeta1/{fich1,fich2}  
chmod = carpeta1/{fich1,fich2}  
chmod o=rw         carpeta1/fich1  
ls -l carpeta1
$ touch carpeta2/{file1,file2}
chmod = carpeta2/{file1,file2} 
chmod u=rw,g=rw carpeta2/file1  
chmod u=rw,g=r  carpeta2/file2  
ls -l carpeta2

Desde otro usuario probar todas las operaciones que se pueden hacer en los ficheros y directorios creados.

su us3rlinux  
Contraseña:
## carpeta1 ##
# prueba de acceso 
us3rlinux@equipo1:/home/usuario1/PRUEBA$ cd carpeta1
bash: cd: carpeta1: Permiso denegado 
# prueba de lectura 
us3rlinux@equipo1:/home/usuario1/PRUEBA$ ls carpeta1 
ls: no se puede abrir el directorio carpeta1: Permiso denegado
## carpeta2 ## 
# prueba de acceso 
us3rlinux@equipo1:/home/usuario1/PRUEBA$ cd carpeta2 
# prueba de lectura 
us3rlinux@equipo1:/home/usuario1/PRUEBA/carpeta2$ ls -l 
total 0
 -rw-rw---- 1 usuario1 usuario1 0 2009-12-08 09:41 file1 
 -rw-r----- 1 usuario1 usuario1 0 2009-12-08 09:41 file2
 # prueba de lectura 
 us3rlinux@equipo1:/home/usuario1/PRUEBA/carpeta2$ cat file1 
 us3rlinux@equipo1:/home/usuario1/PRUEBA/carpeta2$ cat file2
 # prueba de escritura 
 us3rlinux@equipo1:/home/usuario1/PRUEBA/carpeta2$ echo 'hola' > file1 
 us3rlinux@equipo1:/home/usuario1/PRUEBA/carpeta2$ echo 'hola' > file2 
 bash: file2: Permiso denegado 
 exit
 us3rlinux@equipo1:/home/usuario1/PRUEBA$ whoami
 us3rlinux
 us3rlinux@equipo1:/home/usuario1/PRUEBA$ exit 
 exit
 usuario1@equipo1:~/PRUEBA$ whoami
 usuario1 
 usuario1@equipo1:~/PRUEBA$

Visualizar la trayectoria completa del directorio actual. Crear dos directorios llamados correo y fuentes debajo del directorio actual.

pwd /home/usuario1/PRUEBA 
mkdir correo fuentes

Posicionarse en el directorio fuentes y crear los directorios dir1, dir2, dir3.

cd fuentes 
mkdir dir1 dir2 dir3

Crear el directorio menus bajo correo sin moverse del directorio actual.

mkdir ../correo/menus

Posicionarse en el directorio HOME. Borrar los directorios que cuelgan de fuentes que acaben en un número que no sea el 1.

cd $HOME 
find PRUEBA/fuentes -type d -name "*1" -exec rm -r {} \;

Ver si existe el archivo tty2 en el directorio dev. En caso de que exista, ver su fecha de creación o actualización.

find PRUEBA/fuentes/* -type d -regex ".*[0,2,3,4,5,6,7,8,9]" -exec rm -r {} \; 
find PRUEBA/fuentes/* -type d -regex ".*[^1]" -exec rm -r {} \;

Ver los permisos que tienen los archivos que empiecen por tt del directorio /dev.

ls -l /dev/tt*

Visualizar la lista de los archivos ordinarios que están en el directorio /usr/bin.

find /usr/bin -type f

Visualizar la lista de todos los directorios que cuelgan del raíz.

ls / 
find / -maxdepth 1 -type d

Visualizar la lista de todos los ficheros que pertenezcan a root.

find / -user root -type f

Visualizar la lista de todos los ficheros .h del directorio /usr/include.



Ejecutar todos los comandos que empiecen por ls del directorio /bin.



Visualizar de qué tipo son todos y cada uno de ficheros de todo el árbol del sistema propiedad de un usuario conocido.



Crear el directorio uno en el directorio HOME con permiso de escritura y paso para el propietario, de lectura y paso para los usuarios de su mismo grupo y ningún permiso para el resto de usuarios.



Crear el directorio uno1 dentro del directorio creado en el ejercicio anterior con todos lo permisos para el usuario, ninguno para los usuarios del grupo y permiso de escritura para el resto de usuarios.



Copiar todos los ficheros propiedad de un usuario conocido que acaben en un número en el directorio menus.



Visualiza con la orden who la relación de usuarios conectados y sus terminales. Mediante la orden cat, crea un pequeño mensaje desde tu consola y redirígelo a uno de los terminales conectados..



Crea un archivo de tamaño 0



Visualiza el archivo /etc/motd, que contiene el "mensaje del día".



Utilizando de entrada la información de los usuarios conectados al sistema, guardar, ordenadas por el campo hora, las líneas correspondientes al usuario que se desee en el archivo persona.



Crear el directorio carpeta debajo del directorio PRUEBA. Quitarle todos los permisos de lectura. A continuación, buscar todos los directorios que cuelguen del directorio propio y guardarlos en el archivo direc.



Volver a realizar la segunda parte del ejercicio anterior, pero redireccionando los errores al fichero malos. Comprobar la información del fichero malos.



Añadir al fichero direc la lista de todos los ficheros ordinarios que cuelguen de /etc.



Añadir al archivo nuevalista el/los nombre/s de el/los fichero/s del directorio PRUEBA que contengan en su nombre la cadena "ai", añadiendo el posible error al fichero malos.



Sacar por pantalla únicamente el tiempo (buscar comando time) que tarda en ejecutarse el comando who.



Sacar por pantalla un listado completo (buscar comando ps) de los procesos que está realizando el usuario root.



Crear el archivo proceso con los procesos que no tienen ningún terminal asignado.



Añadir al fichero anterior la fecha actual y la trayectoria completa del directorio actual.



Sacar por pantalla el listado de todos los usuarios conectados ordenados por número de proceso asignado.



Averiguar cuál es la actividad actual del sistema. Para ello visualice un listado completo del estado de todos los procesos que se están ejecutando en el sistema.



Obtener un listado con los siguientes datos de los procesos de su shell actual.



Mostrar cuantos usuarios tiene registrados el sistema (el registro de usuarios está en el archivo /etc/passwd)



Mostrar cuántos usuarios tiene registrados el sistema y que utilizan el intérprete bash (debe aparecer al final de la línea /bin/bash o similar)



Mostrar cuantos usuarios hay conectados



Mostrar las líneas, de un archivo de texto, empiecen por L (mayúscula o minúscula)



Contar las líneas, del ejemplo anterior



Extraer los nombres de usuario (primer campo) del sistema



Extraer los nombres de usuario y el shell que utilizan (último campo)



Cambiar la fecha de creación de un archivo ya previamente creado



Calcular la firma md5 de un archivo



Modificar la firma md5 y detectar que se ha cambiado (revisión de firma)



Monitorear la ocupación de las particiones en los discos



¿Cual es el proceso que más carga el procesador?



¿Está corriendo el proceso bash?



¿Cuántos procesos que empiecen por k están corriendo?


