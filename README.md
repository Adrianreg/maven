# Instalación de Maven en el SO
### Respositorio dedicado a la documentación de la instalación de OpenJdk en Ubuntu

Para instalar Java en Ubuntu desde repositorios lo primero que debemos hacer es actualizar el sistema, usando “sudo apt-get update”.

 <p align="center">
<img width=55% src="https://i.imgur.com/5Doa0vy.png">
 </p>
 
Una vez el sistema se haya actualizado, procedemos a instalar la versión por defecto de Java usando “ sudo apt-get install default-jdk”, que en este caso sería la versión 11 (en mi caso ya la tenía instalada).
 
 <p align="center">
<img width=55% src="https://i.imgur.com/YMmQMFi.png">
 </p>
 
Ahora, para comprobar que Java está instalado usamos “java -version” que nos indicará la versión actual en el SO.

 
 <p align="center">
<img width=55% src="https://i.imgur.com/YGYC3Vj.png">
 </p>
 
Ahora bien, si lo que queremos es instalar una versión concreta, podemos hacerlo de la siguiente forma. En el caso de querer instalar la 11 usamos el comando “sudo apt install openjdk-11-jdk”, si quisiéramos la 9 usamos “sudo apt install openjdk-9-jdk” y para la 8 “sudo apt install openjdk-8-jdk”. Como ya tenía la 11, yo probé a instalar la 9 y la 8, obteniendo los siguientes resultados:
 
 <p align="center">
<img width=55% src="https://i.imgur.com/TYkL0wj.png">
 </p>
 
 <p align="center">
<img width=55% src="https://i.imgur.com/ITv0N2g.png">
 </p>
 
La versión 9 no pudo ser encontrada, pero ya tenía la 11 y la 8. Sin embargo, si yo hubiera querido usar la versión 8 no habría podido, porque al usar “java -version” descubrí que el sistema utiliza automáticamente la 11. 
 
 <p align="center">
<img width=55% src="https://i.imgur.com/kJ9ObAD.png">
 </p>
 
 Entonces utilicé el comando “ls /usr/lib/jvm” para verificar si se habían descargado las diferentes versiones de OpenJdk. 
 
 <p align="center">
<img width=55% src="https://i.imgur.com/2EhpXEE.png">
 </p>
 
 Al confirmar que tenía descargadas las diferentes versiones, y queriendo usar la versión 8 en vez de la 11, usé “nano /etc/profile.d” para abrir un fichero en el que copiar el siguiente código:

“# Java version
JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
export JAVA_HOME
export JRE_HOME
export PATH”

Así definí las variables de entorno. 

 
 <p align="center">
<img width=55% src="https://i.imgur.com/Yq5hcTL.png">
 </p>
 
Una vez creado y guardado el fichero, solo quedaba seleccionar la versión 8 para ser usada en vez de la 11 a través de “sudo update-alternatives --config java” y seleccionando la opción deseada. 
 
 <p align="center">
<img width=55% src="https://i.imgur.com/TxuszYT.png">
 </p>
 
