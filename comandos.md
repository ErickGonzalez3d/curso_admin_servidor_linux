# comandos

todos los comandos de linux son archivos binarios que estan en el directorio bin 
#### pwd
#### ls -a -a  
#### ln -s  de 
link crea enlaces simbolicos
#### cd .  ..  /  ~  -  -- 
navega entre las rutas de las carpetas 
#### mv
 mueve o renombrar es como cortar y pegar con otro nombre
#### cp 
copia  rutaOrigen  rutaDestino
#### ps
 lista los procesos que se estan ejecutando 
#### mkdir
crea directorios 

#### rm  -r -R -rf  -f 
borrado de archivos 
#### rmdir 
elimina directorios vacios 
#### touch
crea archivos
#### cat
  concatena , muestra el contenido de un elemento  
* cat archivo.ejem
  crea  archivo.ejem en el directorio actual 
 
 * cat archivo1 archivo2 > archivosuma
  crea archivosuma con el contenido de archivo1 y archivo2  
 
 * cat archivo1 > archivo2 
  sobre escribe archivo2 con el contenido de archivo1
 
 * cat archivo1 >> archivo2 
  adiciona el contenido del archivo1 al archivo2 

#### ifconfig 
* muestra el estado de la red 

#### echo
  * echo 'mensaje'
  imprime en pantalla mensaje

  * echo mensaje > Archivo.txt

  mensaje escribio en archivo.txt y si no estaba creado lo crea y si ya tenia contenido lo sobreescribe
  

  * echo mensaje2 >> Archivo.txt agregara mansaje2 al contenido de archivo.txt

#### history 
muestra el historial de la linea de comandos numerada 
puedo ejecutar un comando de la historia con

   * !# <- numero de la historia  ejemplo !12
     !8  ejecuta el comando en la posición 8 de la lista
   * !in <- busca desde el ultimo hacia atras el comando que comienza por in
   * ctrl+r hace una busqueda inversa  tecleando las iniciales muestra las opciones que ya ejecute y para seleccionar la opcion y salir de ellas pulso esc y el comando estara en la linea para ejecutarse 

#### dir
muestra el nombre del directorio 

#### printenv PATH
 imprime variable de entorno mostrando todos los directorios donde buscara un ejecutable cuando yo lo ejecute 

ejemplo    `printenv PATH` en un subsistema de windows me muestra 

 /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/mnt/c/Program Files/WindowsApps/CanonicalGroupLimited.Ubuntu18.04onWindows_1804.2020.423.0_x64__79rhkp1fndgsc:/mnt/c/Windows/system32:/mnt/c/Windows:/mnt/c/Windows/System32/Wbem:/mnt/c/Windows/System32/WindowsPowerShell/v1.0/:/mnt/c/Windows/System32/OpenSSH/:/mnt/c/Program Files/Microsoft VS Code/bin:/mnt/c/Program Files/Git/cmd:/mnt/c/Program Files (x86)/QuickTime/QTSystem/:/mnt/c/Program Files/PuTTY/:/mnt/c/Users/Eyd/AppData/Local/Microsoft/WindowsApps:/mnt/c/Users/Eyd/AppData/Local/GitHubDesktop/bin:/snap/bin

 hay estan los directorios con sus rutas, separados entre si por los dos puntos ` : `  
 el sistema buscara el binario de un comando en cada una de esas carpetas en el orden que se imprimieron hasta encontrarlo y ejecutarlo 
   
 ---   
   1.Añadir una ruta de un archivo ejecutable a las variables de entorno
      
      cuando creo un programa en un archivo lo ejecuto con ./programa
      pero los programas que creamos por defecto no tienen permiso de ejecución 

 #### which
para buscar donde se encuentra un archivo ejecutable , muestra la ruta completa 

#### find 
encuentra el archivo en el directorio especificandole donde buscar, funciona como un filtro, si conozco donde buscar por ejemplo un binario estara en /bin  los archivos   estaran en /etc 

find /  buscara en la carpeta raiz en todo el disco duro carpetas y archivos, seria tardado
find /etc  buscara dentro del directorio etc 
find /etc -name "crontab" buscara carpetas y archivos con nombre crontab
find /etc -name "cron*" todos los  que comienzan por cron
file /etc -type f -name "cron*"  solo busca los tipo f files que comienzen por cron 

#  estructura de archivos 

## tipos directorios 

#### directorios compartibles 
pueden acceder varios usuarios desde diferentes equipos ya sean locales o remotos como  var/mail , home, opt, etc

#### directorios No compartibles 
accesible y modificable solo por el administrador del sistema /etc, /boot, etc 

#### directorios variables 
la informción varia sin la intervención del administrador
carpetas de aplicaciones y procesos del sistema 
/var/log/syslog, /var/mail, etc 

#### directorios estaticos 
los puede modificar el administrador y los otros usuarios los pueden ver 
guardan configuraciones de aplicaciones o del sistema que hallamos establecido 
Son aquellos directorios que contienen archivos que solo pueden ser modificados con la intervención del administrador del sistema. Algunos ejemplos de directorios estáticos son: /etc/password, /etc/shadow, /usr, /opt, /etc, /boot, /bin, /sbin, etc

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

### /sbin
similar a bin, guarda archivos binarios ejecutables pero la diferencia es que estos son binarios del sistema operativo y con ellos puedo gestionar el sistema en si y los de bin gestionan las aplicaciones en el sistema. 
la diferencia esta en la profundidad de los comando no es lo mismo un comando para copiar y pegar que uno que cambie la configuracion de la red por ejemplo el segundo es mas profundo y se guarda en sbin

### /SElinux 
seguridad para linux, en ella se guardan los programas que gestionan la seguridad del sistema 

### /srv
server  indica que programas estan ejecutandose como servicio, es parte de la especificacion de linux, pero es mas comun mover los ejecutables binarios del servidor a /bin y los datos del servidor a /var.
no se usa mucho, pero no se elimina por compatibilidad con otras distro o programas que la requieran.

### /sys 

parecido al funcionamiento de la carpeta (Device en windows) muestra los dispositivos como los ve o administra el kernel  y si entro en el directorio veremos la clasificación por dispositivos, kernel, bus, power, firware

### /tmp 

archivos temporales durante la ejecución de programas 

### /usr 
guarda los binarios del usuario o programas del usuario que solo estaran disponibles para ese solo usuario 

### /var 

guarda la información que generan varios programas dentro de este directorio se guardan backup, tmp, cache, log para registros, etc. es información que no gestionamos nosotros si no las aplicaciones.
no hay que confundir con /etc ya que /etc guarda la configuración no la información. tambien /home guarda la información del usuario pero las aplicaciones las guardan en /var 
la diferencia es mucha entre los distintos tipos de datos 


## ENLACES SIMBÓLICOS 
Son algo parecido a los accesos directos de win pero mas potentes se crean con `ln -s rutaDeCarpeta`
y se gestiona igual que la carpeta original, puedo crear documentos,borrarlos,editarlos y esos cambios estaran pasando en la carpeta original 
se elimina con rm y no con rmdir 



## subsitema grafico

instalar un servidor x para que mananeja el entorno grafico en windows subsistema ubuntu
descargamos https://sourceforge.net/projects/xming/

lo instalamos como administrador y ejecutamos 

si ejecutamos desde la terminal una aplicación grafica aun genera error porque necesitamos indicale a linux en que ventana o display queremos que se muestre 

ejecutamos el comando `export  DISPLAY=:0` siendo 0 el numero de la pantalla por defecto que usa el servidor xming 

ya podemos ejecutar aplicaciones graficas de linux desde ubuntu subsistema


## editor nano

para manipular los archivos que ya esten editados ya que la primera vez que vamos a escribir algo en un archivo lo podemos hacer con echo mensaje1 > archivo y si agregamos con echo mensaje2 >> archivo se adiciona pero para corregir mensaje1 o mensaje2 tendriamos que escribir todo de nuevo 

nano es el editor que viene preinstalado en el sistema 

   
   1. abrir el documento  nano nombre.ext

   al abrir nano en la parte baja nos muestra las acciones del editor 



## variables de entorno 
cuando ejecuto o abro un archivo estoy moviendome hacia donde esta por ejemplo si tengo un archivo 
hola_mundo.js en el directorio de usuario y quiero ejecutarlo estando fuera del directorio ejecuto 

/home/usuario/hola_mundo.js  y correra el archivo 

pero al ejecutar comando que tambien son archivos binarios que estan en /bin no usamos /bin/ls para ejecutarlo 
solo ls 

todas aquellas archivos o ejecutables que van a estar disponibles desde cualquier carpeta y desde cualquier usuario son las que estan dentro de la variable entorno 
llamada PATH 

## permisos de administrador

r -> Del inglés read, indica el permiso de lectura sobre este archivo o directorio.
w -> Del inglés write, indica el permiso de escritura sobre este archivo o directorio.
x -> Del inglés execution, indica el permiso de ejecución sobre este archivo o directorio.
El guión indica la ausencia de ese permiso.
 
drwxr-xr-x 

d directorio
- archivo 
drwx directorio permisos usuario propietario
drwxr-x directorio permisos usuario propietario y grupo
drwxr-xr-x directorio permisos usuario propietario, grupo y otros 
-rwxr-xr-x archivo permisos usuario propietario, grupo y otros 

 r =1
 w =2
rw =3
 x =4
rx =5
rw =6
rwx =7 
___
## crear un pequeño programa y agregarlo a las variables de entorno 

voy a al directorio home y creo un documento 

touch  programaprueba

nano programaprueba

edito el archivo 
echo  "hola mundo"

cat programaprueba me debe mostrar en pantalla `echo "hola mundo"` pero esto no es la ejecución solo estoy viendo el contenido

para ejecutarlo de manera local uso
             
 * `./programa`  algo incorrecto seria separar el slash. el sistema traraia de buscar un directotio y saldria un error `./ programa`

 cuando ejecuto debe salir un error de ` bash: ./programa: Permission denied` esto me indica que el programa no tiene permisos para ejecutarse pues todos los documento se crean en el sistema sin permisos de ejecución 
 
 ### cambiar los permisos de administrador 
 uso  chmod
  
 `chomod 777 programaprueba`

ahora cuando ejecute el programa desde el directorio donde se encuentra, debera imprimir en pantalla el hola mundo 

si cambiamos de directorio y ejecutamos de nuevo el programa no se ejecutara 

para que se ejecute desde cualquier directorio debere poner o exportar la ruta de la carpeta del archivo a la variable PATH


### insertando variable PATH

export PATH=$PATH:/home/erickgonzalez3d/directorioEjemplo

ahora desde cualquier lugar puedo ejecuta `programaprueba` sin el ./ al principio como un comando 

si no lo agregamos a las rutas de rastreo de PATH no se ejecutara 
___



# super usuario administrador o root 

 este es el usuario de mas alto nivel puede hacer cualquier cosa en el sistema incluso borrar archivos indispensables para el funcionamiento de la maquina, por eso es recomendable hacer solo lo obligatoriamente necesario con este usuario
 intentamos trabajar como super usuarios con el comando `su`.  en otras distribuciones de linux o unix nos pedira la contraseña y podriamos entrar pero ubuntu o ubuntu server no podremos acceder , y no es porque no se conozca la contraseña es que ubuntu  no tiene un surperadministrador por defecto 
