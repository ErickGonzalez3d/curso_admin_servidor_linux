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

### directorio /lost&found
se guardan archivos temporales para recuperacioón del sistema , pero na hace milagros por esa razón debemos hacer backup de sistema periodicamente,  esta carpeta esta protegida contra lectura y escritura, solo el super usuario puede acceder a ella y aun asi si se entrara en ella estaria vacia porque el contenido lo gestiona el sistema, por ejemplo cuando el sistema recupera un archivo corrupto 

### /media 
esta la unidad de CDrom del equipo si tiene  en este directorio se guardan las unidades consideradas mas externas 

### /mnt 
de mount o montaje , almacena los discos, las unidades usb y todo dispositivo que esten en un punto de entrada de la maquina discos externos, CDROM aadicionales, etc. estara en esta carpeta y se les asigna una letra para gestionarla en la maquina

### /opt 
de optianal  se guardan las aplicaciones que no son nativas de nuestra distribucion de linux cada distro tiene paquetes oficiales y estas se guardaran en /bin, si instalamos un programa cualquiera estaran en /opt.
 

### /proc 
de procesor o procesador, aca estara listados todos los procesos que esta ejecutando en procesador.
En linux cada proceso tiene una ID y esa ID tambien tiene el nombre de el programa que se esta ejecutando, el contenido de este directorio es temporal y se gestiona como si fueran carpetas y archivos pero son una virtualización de los mismos, no serviria de nada copiar y crear directorios en /proc porque todo su contenido es temporal 

### /root 
carpeta super usuario. Este usuario no esta en home, si no que tiene su carpeta en la raíz y tiene todos los permisos, si intentaramos entrar el sistema no nos permitiria, solo si estamos en la sesión como super usuarios, es mala practica trabajar como super usuarios, por seguridad el usuario comun invoca permisos de superUsuario cuando es necesario.

### /run  
archivos temporales, esta carpeta no es oficial y anteriormente estaba dentro del directorio /var, pero se separo de /var porque aveces en un servidor se necesita que /var este en un discoduro diferente para mejorar el rendimiento, pero los archivos temporales necesarios para la ejecución de programas quedaban fuera del disco primario.  
/run es una propuesta de algunas distribuciones para solucionar este problema 


## subsitema grafico

instalar un servidor x para que mananeja el entorno grafico en windows subsistema ubuntu
descargamos https://sourceforge.net/projects/xming/

lo instalamos como administrador y ejecutamos 

si ejecutamos desde la terminal una aplicación grafica aun genera error porque necesitamos indicale a linux en que ventana o display queremos que se muestre 

ejecutamos el comando `export  DISPLAY=:0` siendo 0 el numero de la pantalla por defecto que usa el servidor xming 

ya podemos ejecutar aplicaciones graficas de linux desde ubuntu subsistema
