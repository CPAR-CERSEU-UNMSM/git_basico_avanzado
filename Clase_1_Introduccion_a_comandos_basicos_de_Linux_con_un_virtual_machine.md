# Clase 1. Introducción a comandos básicos de Linux con una máquina virtual

El sistema operativo en el cual vamos a trabajar es Linux. En caso no se tenga Linux como sistema operativo, vamos a instalar una máquina virtual (**Virtual Machine**) basada en la distribución Ubuntu. Primero debemos instalar **VirtualBox Manager**. Para ello, ir a la siguiente web de [virtual box](https://www.virtualbox.org/wiki/Downloads) y descargar el instalador segun el sistema operativo que se tenga (Windows o MacOS):

<img src="./Figures_teaching/Pasted image 20240310223840.png" alt="drawing" width="800"/>

Luego de descargar el instalador, ejecutarlo y usar las instrucciones por defecto. 

<img src="./Figures_teaching/Pasted image 20240310223959.png" alt="drawing" width="100"/>

Una vez instalada la aplicación, accedemos al **VirtualBox Manager** dónde podemos organizar diferentes máquinas virtuales. 

<img src="./Figures_teaching/Pasted image 20240310224335.png" alt="drawing" width="800"/>

Por el momento no tenemos todavía ninguna máquina virtual, y en consecuencia tampoco Ubuntu como sistema operativo Linux. Para tener una máquina virtual, tenemos que crear algo denominado *Imagen vdi* que tiene la configuración de nuestro sistema operativo Ubuntu. Nosotros podemos descargar cada elemento o dependencia por separado, pero también podemos instalar *Imágenes* ya predeterminadas y ajustarlas a nuestras necesidades. Esa será nuestra siguiente acción.  Para ello iremos a la siguiente web [osboxes](https://www.osboxes.org/ubuntu/#ubuntu-22-04-jammy-vbox) y descargamos la versión "Ubuntu 22.04 Jammy Jellyfish":

<img src="./Figures_teaching/Pasted image 20240310225509.png" alt="drawing" width="500"/>

En la opción *Info*, guardar el usuario y contraseña que nos servirá para acceder a nuestra *Imagen* una vez instalada y configurada. 

<img src="./Figures_teaching/Pasted image 20240310225558.png" alt="drawing" width="500"/>


Luego, regresamos al **VirtualBox Manager** y hacemos clic en la opción <img src="./Figures_teaching/Pasted image 20240310230541.png" alt="drawing" width="70"/>. Ahí, colocamos un nombre a nuestra *Imagen*, el tipo de sistema operativo y la versión así como se muestra en la figura:

<img src="./Figures_teaching/Pasted image 20240310230900.png" alt="drawing" width="600"/>

Luego, debemos configurar el hardware en base a nuestro hardware local disponible y a nuestros requerimientos. Para esta sesión, indicamos (alrededor de) 4 GB de memoria RAM y 4 procesadores (para poder realizar aplicaciones en paralelo). Debemos tomar en cuenta que la configuración de nuestra máquina virtual puede modificarse pero es más complejo hacerlo una vez creada. 

<img src="./Figures_teaching/Pasted image 20240310231314.png" alt="drawing" width="600"/>

Luego tenemos que definir el tamaño de nuestro disco duro virtual. El tamaño por defecto es de 25 GB, el cual es adecuado para esta sesión. Debemos tomar en cuenta que el valor que pongamos será consumido de nuestro disco duro local. 

<img src="./Figures_teaching/Pasted image 20240310232825.png" alt="drawing" width="600"/>

Luego, selecionamos la opción *Usar un hard disk existente* y en la opción <img src="./Figures_teaching/Pasted image 20240310233240.png" alt="drawing" width="50"/> añadimos la *Imagen* descargada, luego hacemos clic en *Choose*. Cómo se puede observar, el espacio virtual máximo posible es de 500 GB, pero el espacio real ocupado es de apenas 8 GB (aproximádamente). Luego hacer clic en *Next* y luego *Finish*:

<img src="./Figures_teaching/Pasted image 20240310233341.png" alt="drawing" width="600"/>

La configuración resumida de nuestra *Imagen* (máquina virtual) es la siguiente:

<img src="./Figures_teaching/Pasted image 20240310233956.png" alt="drawing" width="800"/>

Para utilizar la máquina virtual, hacemos doble clic en <img src="./Figures_teaching/Pasted image 20240310234930.png" alt="drawing" width="150"/>. Una vez que haya inicializado Ubuntu, colocamos la contraseña de usuario que guardamos antes. 

<img src="./Figures_teaching/Pasted image 20240310235610.png" alt="drawing" width="800"/>

Una vez dentro, tenemos una ventana muy similar a una ventana de Windows con las aplicaciones básicas instaladas como Mozilla Firefox, Libre Office, etc. Para poder interactuar con el sistema, usamos la combinación **Ctrl + Alt + T** para abrir la consola. 

<img src="./Figures_teaching/Pasted image 20240311000205.png" alt="drawing" width="800"/>

Para esta sesión, hay algunas aplicaciones que necesitamos. Por ejemplo, el compilador para C++ llamado **g++** y el sistema de control de versiones llamado **git**. Si probamos cualquiera de estos en la línea de comando, nos arrojará un error. Esto debido a que estas aplicaciones no están instaladas.

<img src="./Figures_teaching/Pasted image 20240311000549.png" alt="drawing" width="800"/>

Para instalar estas aplicaciones, primero vamos a usar el comando `sudo apt update` para poder actualizar la lista de repositorios de dónde Ubuntu instalará los programas o aplicaciones que necesitemos. `sudo` significa **super user** y `apt` es el software manager para la instalación de software. 

Para poder instalar el compilador, usamos el comando `sudo apt install build-essential`. La instalación exitosa se puede comprobar de la siguiente manera:

<img src="./Figures_teaching/Pasted image 20240311001617.png" alt="drawing" width="800"/>

Para instalar git, usamos el comando `sudo apt install git`. La instalación exitosa se puede comprobar de la siguiente manera:

<img src="./Figures_teaching/Pasted image 20240311001742.png" alt="drawing" width="600"/>

Finalmente instalaremos **htop** (usando el comando `sudo apt install htop`) que nos permite ver el estado del sistema. Es el equivalente al control manager de Windows para ver que procesos están corriendo, el uso de los procesadores y memoria RAM, etc. Para salir, usamos la combinación **Ctrl + C**.

<img src="./Figures_teaching/Pasted image 20240311002131.png" alt="drawing" width="800"/>

### Cómo pegar y copiar de Windows to Ubuntu

Para poder realizar `git push` con el protocolo `https`, necesitamos nuestras credenciales, nombre de usuario, y token recién creados. En el caso de que nuestras credenciales se encuentren en nuestra máquina host o sistema operativo Windows, debemos encontrar una forma de copiar y pegar texto de Windows a Ubuntu y viceversa. Si probamos **Ctrl + C**  o **Ctrl + V** vamos a ver que no funciona. Por ello tenemos que seguir algunos pasos adicionales.

1. Primero iremos a la configuración de la máquina virtual, *General*, *Advanced* y revisar si las opciones de *Shared Clipboard* y *Drag and Drop* están marcadas cómo **Bidireccionales**

<img src="./Figures_teaching/Pasted image 20240324225127.png" alt="drawing" width="700"/>

2. Luego, en la opción *Storage* debemos instalar nuestro **Virtual Box Guest Additions ISO**. Éste se encuentra dentro de *Program Files/Oracle/VirtualBox*. 

<img src="./Figures_teaching/Pasted image 20240324225722.png" alt="drawing" width="700"/>

3. Luego, al abrir Ubuntu, encontraremos una nueva carpeta denominada **VBox_GAs** 

<img src="./Figures_teaching/Pasted image 20240324230342.png" alt="drawing" width="700"/>

4. Abrir esta carpeta y abrir la terminal dentro de esta carpeta. En esta carpeta, ejecutar el siguiente comando `sudo ./VBoxLinuxAdditions.run`. 
5. Finalmente, luego de reiniciar la máquina virtual, las opciones de copiar y pegar quedarán habilitadas.

### Comandos básicos en Linux

- `ls`: revisar el contenido de un directorio
- `pwd`: obtener la ruta de un directorio
- `nano [archivo]`: abrir un archivo y modificarlo
- `cd [directory-name]`: ir al directorio
- `cd ..`: ir al nivel superior (en el sistema de archivos)
- `cd -`: regresar al directorio anterior
- `mkdir [-option] [directory-name]`: crear una nueva carpeta
- `touch [-option] [file-name]`: crear un archivo nuevo
- `rmdir [-option] [directory-name]`: remover una carpeta
- `rm [-option] [file-name]`: remover un archivo
### Referencias

- https://linuxconfig.org/how-to-install-g-the-c-compiler-on-ubuntu-20-04-lts-focal-fossa-linux
- https://www.makeuseof.com/how-to-import-vdi-file-into-virtualbox/









