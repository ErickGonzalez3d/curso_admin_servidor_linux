## comandos

pwd
ls -a -a  
cd .  ..  
mv mueve o renombrar es como cortar y pegar con otro nombre
cp copia  rutaOrigen  rutaDestino
ps lista los procesos que se estan ejecutando 
mkdir
rm  -r -R -rf  -f 
rmdir elimina directorios vacios 
touch
cat 
ifconfig  muestra el estado de la red 
echo $nom123     mostrara la ubicación del archivo nom123
dir  muestra el nombre del directorio 


todos los comandos de linux son archivos binarios que estan en el directorio bin 


###  estructura de archivos 

## tipos directorios 

#### directorios compartibles 
pueden acceder varios usuarios desde diferentes equipos como  var/mail , home, opt, etc

#### directorios No compartibles 
accesible y modificable solo por el administrador del sistema /etc, /boot, etc 

#### directorios variables 
la informción varia sin la intervención del administrador
carpetas de aplicaciones y procesos del sistema 
/var/log/syslog, /var/mail, etc 

#### directorios estaticos 
los puede modificar el administrador y los otros usuarios los pueden ver 
guardan configuraciones de aplicaciones o del sistema que hallamos establecido 

# directorios 

### directorio raiz /

es el directorio donde se alojan todos los de primer nivel  del sistema, es la estructura principal de todos los sistemas linux por convención FHS (filesystem Herarchy standar)

          /mnt/c/.../.../..../.../.../archivo.ext 

el primer slash hace referencia al directorio raiz, seguido por directorio de primer nivel, y desde el segundo slash esta la ruta hasta el ultimo slash antes de indicar el nombre del archivo


### directorio /bin 
es un directorio estatico y compartido 
guarda todos los archivos binarios como ls comandos y ejecutables indispensables para el sistema asi como las aplicaciones y utilidades  que vengan nativas con el sistema operativo,es un directorio compartido , en este directorio no puede tener subcarpetas solo binarios 

### directorio /boot 
en este directorio se guardan los archivos para que arranque el sistema operativo  kernel o imagen de linux y grub 
se ejecuta antes del kernel inclusive 

### directorio /dev 

device o dispositivo  se encuentran los puertos, puntos de montaje  de los dispositivos como discos duros, cdrooms, unidades extraibles, todo cuanto este configurado en nuestra maquina estara almacenado hay 

### directorio /etc 
guarda las configuraciones de las aplicaciones o programas ejecutables solo las configuraciones no guardan binarios, esos estan en /bin

### directorio /home 
Almacena la carpetas por usuario que tengamos en el sistema , por defecto tendremos un directorio con el nombre de nuestro usuario. (   NO ESTARA LA CARPETA DEL SUPER USUARIO esa esta en ROOT)

### Directorio /lib  y lib64 
Librerias  = elementos comunes de la programación de varios programas, son los elementos comunes que tiene varios programas, seria logico pensar que los elementos de un programa debe estar en /etc  pero seria innecesario crear una libreria de por ejemplo de python por cada programa que requiera de este para ejecutarse, para eso existe el directorio /lib
la diferencia es que en lib64 se almacenan las librerias exclusivas de 64 bits 

### directorio /lostandfound
se guardan archivos temporales para recuperacioón del sistema 

### /media 
esta la unidad de CDrom del equipo si tiene  en este directorio se guardan las unidades consideradas mas externas 

### /mnt 
de mount o montaje , almacena los discos, las unidades usb u todo dispositivo que este en un punto de entrada estara en esta carpeta 


## subsitema grafico

instalar un servidor x para que mananeja el entorno grafico en windows subsistema ubuntu
descargamos https://sourceforge.net/projects/xming/

lo instalamos como administrador y ejecutamos 

si ejecutamos desde la terminal una aplicación grafica aun genera error porque necesitamos indicale a linux en que ventana o display queremos que se muestre 

ejecutamos el comando `export  DISPLAY=:0` siendo 0 el numero de la pantalla por defecto que usa el servidor xming 

ya podemos ejecutar aplicaciones graficas de linux desde ubuntu subsistema
