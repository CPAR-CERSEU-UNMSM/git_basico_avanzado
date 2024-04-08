# Clase 2. Introducción al sistema de control de versiones GIT

## Control de versiones

Sistema que hace seguimiento a cada modificación o cambio en un código, algoritmo, servidor de IT, website, documento. Un ejemplo de control de versiones es **GIT** o **google docs**.

<img src="./Figures_teaching/Pasted image 20240309233350.png" alt="drawing" width="400"/>

## Esquema básico de un sistema GIT

Git consiste en uno o varios **repositorios locales** y **remotos**. Los **repositorios locales** son personales y los tenemos en nuestra computadora personal por ejemplo. El trabajo aquí puede ser offline pero debe estar sincronizado al repositorio remoto. El o los **repositorios remotos** contienen el estado del arte o la versión actualizada del repositorio y están guardados en la nube en plataformas como *GitLab*, *GitHub* o *Bitbucket*.

<img src="./Figures_teaching/Pasted image 20240309233852.png" alt="drawing" width="700"/>

## Locaciones de GIT

Para manejar GIT, hay algunos componentes importantes que debemos conocer y nos permitirán entender mejor cómo funciona GIT. 
- El primer elemento es el llamado **working tree**, es el ambiente donde nosotros trabajamos y tenemos los archivos que vamos a guardar mediante el comando _commit_. 
- Una vez que tenemos idea de lo que vamos a guardar, pasamos al **área de preparación** que incluye todos los archivos a ser incluidos en el _commit_. Por ejemplo, algunas veces modificamos dos archivos que están relacionados y los queremos guardar juntos, entonces pensaremos en un commit que incluya los dos archivos y no dos commits por separado. 
- Luego, todos los commits de un proyecto se almacenan en el **repositorio local** que está en nuestra computadora local y estos tres elementos forman parte del **área personal** del proyecto.
- Finalmente, el almacenamiento final del proyecto se realiza en la nube o algún **repositorio remoto** como **GitLab** o **GitHub** que se considera que contiene el proyecto completo y es nuestra fuente de consulta del proyecto en caso se necesite de una referencia. La idea es tener nuestros repositorios, local y global, sincronizados.

<img src="./Figures_teaching/Pasted image 20240309234800.png" alt="drawing" width="700"/>

## Comandos claves en git

1. `git init`: crea nuestro repositorio
2. `git status`: muestra el status del repositorio. Nos permite observar qué cambios se han realizado, qué nuevos archivos no están siendo parte del sistema de control, etc
3. `git add .`: añade todos los archivos que hayan tenido cambios durante nuestra sesión de trabajo al área de preparación
4. `git commit`: crea un foto instantánea de nuestro repositorio en un momento específico. Con un commit, nosotros guardamos la historia del repositorio. Lo ideal es hacer commits de lo que uno quiera guardar y de manera frecuente
5. `git push`: guardar lo creado/modificado en el repositorio local hacia el repositorio global. El repositorio global almacena nuestro trabajo en la nube y es como el repositorio de referencia. Los proveedores de repositorios globales son: GitLab, GitHub, Bitbucket, entre otros
6. `git pull`: actualizar el repositorio local con respecto al global
7. `git reset --hard`:  elimina todo los cambios que no hayan pasado por un commit. En el marco de este curso, vamos a usarlo en caso hagamos cambios en el repositorio remoto del curso y no tengamos derechos de autoría del mismo

## Ejercicio 1. Mi primer repositorio en GitHub

En este ejercicio aprenderemos los pasos básicos del sistema de control de versiones GIT.

1. Verificar si se tiene instalado GIT. Para ello, ir a la línea de comando (**Ctrl + Alt + T**) en su sistema operativo y escribir: `git --version`

<img src="./Figures_teaching/Pasted image 20240311001742.png" alt="drawing" width="400"/>

2. En caso no esté instalado, usar el comando `sudo apt install git`
3. Una vez que se tiene GIT instalado, crear una carpeta dónde se desee almacenar el projecto con la función `mkdir proyecto1`
4. Con el comando `cd proyecto_1` ir a la carpeta proyecto 1
5. En la línea de comando `git status` (muestra el status del repositorio). **¿Qué observamos y por qué pasa eso?**
6. En la misma línea de comando, escribir el comando `git init` (crea nuestro repositorio). El repositorio local que toma el nombre de tu carpeta *proyecto1*. Al hacer estamos creando automáticamente elementos importantes de un sistema GIT. **¿Podrías nombrar qué elementos estamos creando?**
7. Revisar el estado del nuevo repositorio GIT usando el comando `git status`. **¿Qué observamos?** **¿Está el repositorio al día?**
8. Luego, usando la función `touch test1` vamos a crear el documento test1
9. Abrir el documento test1 con la función `nano test1` y colocar `Mi nombre es XXXXX`. Guardar el contenido con la combinación **Ctrl + o**

<img src="./Figures_teaching/Pasted image 20240311112052.png" alt="drawing" width="400"/>

6. Volver a revisar el estado de tu repostorio. **¿Qué observamos? ¿Ha cambiado algo con respecto al estado anterior?** Describa sus observaciones
5. Añadir el archivo al área de preparación suponiendo que ya queremos guardar esos cambios en el archivo de texto *text1.txt*. Para eso, usa el comando `git add text1.txt` (añade solo el archivo *text1.txt*) o `git add .` (añade todos los archivos creados). Ambos comandos para este caso deberían hacer lo mismo. **¿Puede explicar por qué?**
6. Luego de usar el comando `git add`, volver a revisar el estado del repositorio con `git status`. Algo ha cambiado, **¿puede explicar qué ha cambiado?** **Dentro del flujo de trabajo de git, ¿dónde se encuentra el archivo text1.txt?**. (Tip: las opciones son: working tree, área de preparación o repositorio local)
7. Empezar a escribir la historia de tu repositorio tomando una foto instantánea de este cambio. Para eso usar el comando `git commit -m "MENSAJE"`. Recuerda que mientras más explicito sea el MENSAJE, mejor será la historia del repostorio. Una vez hecho esto, verificar el status del repositorio  con `git status`. **¿Algo ha cambiado? Describa sus observaciones. ¿Están todos los componentes de git al día?**
8. Los cambios elaborados sólo se han hecho de manera local, para poder guardarlos en la nube o en un repositorio remoto, debemos crear una cuenta en [GitHub](https://github.com) o [GitLab](https://gitlab.com/users/sign_in) o [Bitbucket](https://bitbucket.org).
9. Antes de sincronizar nuestro repositorio local con el global, debemos crear un *personal token* en GitHub para que éste reconozca que somos nosotros los dueños de ambos repositorios
10. Para crear el **token**, debemos ir a la configuración de nuestra propia cuenta en GitHub

<img src="./Figures_teaching/Pasted image 20240317000532.png" alt="drawing" width="400"/>

11. Luego, en la opción *Developer settings*, buscar dentro de *Personal access tokens* la opción *Tokens (classic)*

<img src="./Figures_teaching/Pasted image 20240317000840.png" alt="drawing" width="400"/>

12. Una vez encontrada la opción, general un nuevo token y copiar el código que aparece pues este aparecerá solo una vez. Usen el token cuando sea necesario

<img src="./Figures_teaching/Pasted image 20240317001135.png" alt="drawing" width="400"/>

13. Una vez creada la cuenta, crear un repositorio remoto con el nombre *proyecto1*. Elige un repositorio en blanco (abajo un ejemplo de como luce en GitHub)

<img src="./Figures_teaching/Pasted image 20240310001819.png" alt="drawing" width="400"/>

14. Colocar el nombre, una descripción, elige hacerlo público y sin README y crear el repositorio.
15. Una vez creado, conectarlo al repositorio local siguiendo los pasos indicados en la misma web. Primero, configurar el repositorio local para conectarse al repositorio remoto:

<img src="./Figures_teaching/Pasted image 20240310001929.png" alt="drawing" width="700"/>

16. Seguir lo pasos para connectar ambos repositorios

<img src="./Figures_teaching/Pasted image 20240310001937.png" alt="drawing" width="700"/>

17. Finalmente, utilizar `git push`  para sincronizar los cambios en ambos repositorios y revisar el status con `git status`. **¿Qué diferencias hay ahora?**

### Paso alternativo en caso "git push" con https no funcione - SSH

Existen dos formas para sincronizar un repositorio remoto con un repositorio local. Hasta ahora, hemos utilizado el protocolo `https`. Alternativamente se puede utilizar el protocolo `ssh` (Secure Shell). `ssh` es un protocolo encriptado que ofrece una transferencia de información más eficiente y segura entre repositorios. El protocolo por defecto de GitHub es `https`, pero nosotros podemos usar alternativamente `ssh` del siguiente modo:

1. Primero vamos a verificar si en nuestro sistema de archivos hay un par de llaves ssh, es decir, un archivo que contiene la llave privada (`id_rsa`) y otro que contiene la llave pública (`id_rsa.pub`). Para ello, en el terminal ejecutar el comando `cd ~/.ssh` y luego con `ls -la` verificar el contenido de la carpeta ssh:

<img src="./Figures_teaching/Pasted image 20240324232929.png" alt="drawing" width="700"/>

2. Dado que en nuestro caso tales archivos no están presentes, debemos crearlos ejecutando el comando `ssh-keygen -t rsa -b 4096 -C "miemail@midominio.com"` y presionar ENTER + ENTER + ENTER (esta última acción en el teclado significa que no hay necesidad de configurar o escribir nada cuando haya preguntas o acciones para realizar): 

<img src="./Figures_teaching/Pasted image 20240324233445.png" alt="drawing" width="700"/>

3. Revisar nuevamente el contenido de la carpeta `~/.ssh`. Ahora veremos que los archivos deseados se han creado (`id_rsa` y `id_rsa.pub`). El archivo de extensión `.pub` es la llave pública, la cual que puede ser compartida.

<img src="./Figures_teaching/Pasted image 20240324233640.png" alt="drawing" width="700"/>

4. Usando el comando `cat id_rsa.pub`, abrimos el archivo y copiamos su contenido para ser guardado en la configuración de nuestra cuenta en GitHub. 

<img src="./Figures_teaching/Pasted image 20240324234024.png" alt="drawing" width="700"/>

5. Ahora nos debemos dirigir a la configuración de nuestra cuenta en GitHub:

<img src="./Figures_teaching/Pasted image 20240324231342.png" alt="drawing" width="400"/>

6. Dentro de las opciones de la configuración, ir a la opción denominada *SSH and GPG keys*. En esta opción hacer click en *New SSH key*

<img src="./Figures_teaching/Pasted image 20240324234422.png" alt="drawing" width="700"/>

7. Finalmente, se añade un nombre y se pega la clave pública:

<img src="./Figures_teaching/Pasted image 20240324234609.png" alt="drawing" width="700"/>

## Referencias:

- [https://www.atlassian.com/git/tutorials/learn-git-with-bitbucket-cloud](https://www.atlassian.com/git/tutorials/learn-git-with-bitbucket-cloud)
- [https://git-scm.com/docs](https://git-scm.com/docs)










