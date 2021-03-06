﻿COMENZANDO LA AVENTURA

Hemos creado una nueva VM por lo que no tenemos instalado ninguno de los programas necesarios para la actividad (Java, Apache, Tomcat, SSH ni MariaDB). Por ello esta guía no solo va a comprobar cada paso, sino que es una guía completa de instalación desde 0 de todos estos programas. ¡Vamos a ello!

JAVA INSTALACIÓN

Verificamos que no tenemos instalado JAVA empleando para ello el comando ***java --version***

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.001.png)

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.002.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.002.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.003.png)

Nos comunica que no esta instalado pero que podemos hacer uso de alguno de sus comandos para poder hacerlo. Seguimos el primero de ellos y comenzamos la descarga, no sin antes introducir nuestra contraseña, como siempre ocurre ¿o no? Efectivamente, habrá uno de los programas que no nos solicite la contraseña. Algo, en el ámbito de la seguridad poco acertado, por lo que tendremos que crear algunos “corta-pasos” a los posibles “mal intencionados” pero para eso hay que esperar a llegar a él.

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.004.png)

Una vez instalado comprobamos la versión que tenemos

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.005.png)

Ya tenemos Java instalado, fácil ¿verdad? Vayamos ahora con el segundo en la lista “Apache”

APACHE INSTALACIÓN

Como hemos hecho anteriormente, recurrimos al comando ***sudo apt install*** pero ahora con apache2

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.006.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.007.png)

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.008.png)

Y una vez finalizado el proceso, comprobamos la versión instalada

APACHE COMPROBACIÓN

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.009.png)

Antes de probar Apache, es necesario modificar la configuración del firewall para permitir el acceso externo a los puertos web predeterminados. Esto lo haremos suponiendo que tengamos configurado un [firewall como UFW]( t ) configurado para restringir el acceso al servidor.

Durante la instalación, Apache se registra con UFW y proporciona algunos perfiles de aplicación que se pueden usar para habilitar o deshabilitar el acceso a Apache a través del firewall.

Vamos a poder enumerar estos perfiles escribiendo ***sudo ufw app list***

Puerto 80

Puerto 80 y 443

Puerto 443

Puerto 443![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.014.png)

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.015.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.016.png)Vamos a permitir el acceso sólo a puertos 80 (aun no hemos conf. SSH) y comprobamos

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.017.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.018.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.019.png)

Nótese la diferencia cuando hemos instalado posteriormente SSH

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.020.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.021.png)



![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.022.png)Verificamos el funcionamiento escribiendo ***sudo systemctl status apache2***

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.023.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.024.png)

Como vemos sale activo pero la mejor manera de probar esto es solicitar una página de Apache.** Podremos acceder a ella a través de la dirección IP para confirmar que el software se ejecuta correctamente. Si no conoces la dirección IP, se puede obtener escribiendo en la terminal (Ctrl+Alt+T)

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.025.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.026.png)

Con el comando ***hostname -I*** se nos mostrará algunas direcciones locales separadas por espacios (10.0.2.15 es nuestro caso) Podemos probar cada una en el navegador web para determinar si funcionan. Estas nos deben permitir ver la página web predeterminada de Ubuntu 20.04 Apache. Veamos si la comprobación sale correctamente:

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.027.png)

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.028.png)

Parece que todo funciona como debe, vamos ahora a por Tomcat, que es algo más complicado que estos dos últimos procesos.

TOMCAT, UN PASO MÁS ALLÁ

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.029.png)El primer paso es instalar el paquete OPEN JDK en Ubuntu

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.030.png)

Ahora crearemos un usuario y grupo de sistema con el directorio de inicio con /opt/tomcat

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.031.png)

Para comprobar que se ha creado, intento crearlo de nuevo y me devuelve esto

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.032.png)

Ya puedo avanzar un poco mas. Vamos a instalar el paquete y utilizaremos wget y unzip para extraer el archivo

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.033.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.034.png)

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.035.png)

Nos movemos al directorio /tmp con el comando /cd delante

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.036.png)

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.037.png)Y desde aquí vamos a extraer el archivo (con unzip)  y llevarlo al directorio /opt/tomcat

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.038.png)

Aquí vemos como lo llevamos al directorio. Cuidado con los espacios entre / / que si no dará fallo

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.039.png)

Para tener controladas mejor las versiones y las instalaciones, vamos a crear un “enlace ficticio” que va a apuntar al directorio donde está instalado tomcat

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.040.png)

Ahora el usuario creado, recordemos que es “pamela”, necesita poder acceder al directorio de tomcat

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.041.png)

Y vamos a hacer que los script dentro del directorio sean ejecutables, usaremos ***chmod***  porque es el encargado de administrar los permisos de los archivos y carpetas

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.042.png)

Para ejecutar Tomcat como servicio tenemos que crear un nuevo archivo que se llamara tomcat.service y lo guardaremos en el directorio /etc/systemd/system

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.043.png)

Vamos a ver que todo está donde debe

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.044.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.045.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.046.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.047.png)

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.048.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.049.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.050.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.051.png)

**[Unit]**

***Description=<descrición del unit>***

Una descripción del servicio que se muestra al consultar el status del servicio.

***After=<units>***

Define el orden en el cual los unist se inician. El unit se inicia sólo después de que los units especificados en esta línea estén activos. La diferencia con *Require* es que *After* no activa ![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.052.png)explícitamente los units indicados aquí. La opción **Before** tiene la funcionalidad opuesta a *After*.

***Requires=<units>***

Configuras las dependencias sobre otras units. Los units listados aquí serán activados junto con este unit. Si alguno de los units requeridos falla en el arranque, este unit tampoco se activa.

***Wants=<units>***

Activa los units indicados aquí. Wants configura dependencias de manera más débil que Require. Si alguno de los units indicados por Wants no se inician correctamente no tienen ningún efecto en el estado de este unit. Wants es la manera recomendada para establecer dependencias personalizadas.

**Conflicts=<units>**

Configura dependencias negativas, es decir, es un opuesto a *Requires*. El servicio no se inicia si el servicio indicado en esta línea está activo.

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.053.png)

**[Service]**

***TimeoutStartSec=<n>***

Tiempo tras el cuál, si el servicio no ha arrancado, se considera fallo y se detiene.

***ExecStart=<ejecutable>***

comando a ejecutar.

***Type=<opción>***

Configura el tipo de arranque del procesos de la unidad la cual afecta a la funcionalidad ExecStart. Las opciones son:

- simple – Es el valor por defecto. El proceso arrancado con ExecStart es el proceso principal del servicio. Este proceso se arranca inmediatamente. El proceso no debe desencadenar otros procesos que requieran ejecución en el algún orden. No utilizar este tipo si otros servicios necesitan ejecutarse en orden con él.
- forking – El proceso iniciado con ExecStart genera un proceso hijo que se convierte en el proceso principal del servicio. Se sale del proceso padre cuando el arranque se completa. El uso de esta opción es importante cuando ejecutamos un script que a su vez ejecuta otros procesos. Sin la opción forking estos subprocesos podrían salir inesperadamente al concluir el proceso principal.
- oneshot – Similar a simple, pero se sale del proceso  antes de que se arranquen los subsiguientes units. Es útil para la ejecución de scripts que hacen un trabajo sencillo y luego salen. Con la opción RemainAfterExit=yes systemd considerará su proceso como activo después de que el proceso haya salido.
- dbus – Similar a simple, pero los subsiguientes units sólo son arrancados después de que el proceso principal adquiera un nombre D-Bus.
- ![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.054.png)notify – Similar a simple, pero los subsiguientes units sólo son arrancados después de que un mensaje de notificación se haya enviado mediante una función sd\_notify().
- idle – Similar a simple, la ejecución actual del binario del servicio se retrasa hasta que todos los trabajos se terminan, lo que evita la mezcla de la salida de estados con las salidas de los servicios por la Shell.

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.055.png)

**[Install]**

*WantedBy=multi-user.target*

Indica el target al que pertenece este unit. Esto provoca que el comando systemctl enable <servicio>.service cree los enlaces simbólicos necesarios dentro del target multi-user.target.wants sin necesidad de hacerlo manualmente.

Lo que se consigue con esto es que el servicio se ejecute automáticamente al arrancar el target.

Ahora nos queda verificar el servicio. Iniciamos con el comando ***systemctl start tomcat,*** verificamos estado con ***status tomcat***


![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.056.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.057.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.058.png)

Ahora hacemos que se inicie Tomcat automáticamente con el inicio

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.059.png)

FIREWALL accesos

Si tienes instalado un firewall y quieres acceder a Tomcat desde el exterior a tu red local, tenemos que habilitar el puerto 8080, para ello usaremos el comando ***ufw allow 8080***

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.060.png)

CONFIGURANDO TOMCAT WEB MANAGER INTERFACE

Ahora que tenemos Tomcat 9 instalado en nuestro Ubuntu, el siguiente paso es **crear un usuario que tenga acceso a la interfaz de administración web**. Los usuarios de Tomcat y sus roles se definen en el archivo *tomcat-users.xml*

Vamos a abrir el archivo (recuerdo que si no tienes instalado ***vim*** puedes hacerlo con el comando sudo apt-get install vim) ***sudo vim /opt/tomcat/latest/conf/tomcat-users.xml***

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.061.png)

Para agregar un nuevo usuario que pueda acceder a la interfaz web de tomcat (*manager-gui y admin-gui*) necesitamos **definir el usuario al final del archivo tomcat-users.xml** 

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.062.png)

Verificamos que el usuario ha sido creado en el doc

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.063.png)

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.064.png)

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.065.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.066.png)

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.067.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.068.png)

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.069.png)

De forma predeterminada, **la interfaz de administración web de Tomcat está configurada para permitir el acceso solo desde el host local**. Si necesitas acceder a la interfaz web desde una IP remota abre los siguientes archivos y comenta o elimina las líneas marcadas en las capturas:

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.070.png)

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.071.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.072.png)

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.073.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.074.png)

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.075.png)![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.076.png)

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.077.png)

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.078.png)

Ahora toca probar la instalación. Para ello abrimos el navegador e indicamos nuestra ip y el puerto 8080.

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.079.png)

Pinchamos en Manager APP o en Host Manager y nos aparece la siguiente pantalla

![](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.080.png)

Ingresamos el usuario y la contraseña y accedemos al panel 

![administrador de aplicaciones de tomcat 9](Aspose.Words.f472b39d-a76b-44dd-b60a-234f2117c185.081.png "administrador de aplicaciones de tomcat 9")

Y al gestor de la máquina virtual de Tomcat

