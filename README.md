# Practica03_Compilacion-del-karnel-de-Linux
Practica 03 de la materia de Sistemas Operativos 2
# Tutorial:  Compilacion del Kernel de Linux
### Creado por:
* Benjamin Hoyos Herrera 
* Angel Yedid Nacif Mena
* Carlos Abraham Martines Zamora
* Genaro Gonzales Lozada  
Practica 03 de la materia de Sistemas Operativos 2  


## 1.¿Cómo hacer un respaldo de una máquina virtual? y ¿cómo levantar ese respaldo? (En VirtualBox)    
* Este punto es importante tenerlo en cuenta ya que siempre es bueno tener un respaldo de nuestras maquinas virtuales cuando hacemos un cambio mayor como el que vamos a hacer, ya que no sabemos que vaya a pasar o tal vez ocurra un error y ya no funcione mas la maquina vitrual y tengamos que levantar una desde cero, es mejor, por buena costumbre y para ahorrarnos el trabajo de crear una nueva maquina virtual tener un respaldo.
* Para ello haremos los siguientes pasos:

    1. En una ventana abierta de virtual box seleccionar nuetra maquina virtual a respaldar, despues das click a file -> Export Appliance o ```Ctrl + E```      
    ![1_0](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/1_0.png)    
    2. Como vemos la maquina virtual esta seleccionada, pero si no lo esta seleccionala y da click a ```Next```    
    ![1_1](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/1_1.png)    
    3. Seleccionas el formato y el luegar donde vas a guardar el back up y das next ```Next```    
    ![1_2](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/1_2.png)    
    4. En el apartado de NAME, cambiamos el nombre si es necesario y damos click a ```Export```    
    ![1_3](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/1_3.png)    

    Listo ya tienes un respaldo de tu maquina virtual!!

* Ahora bien para usar/levantar el respaldo creado, los pasos a seguir son los siguientes:
    1. En una ventana abierta de virtual box seleccionar nuetra maquina virtual a respaldar, despues das click a file -> Import Appliance o ```Ctrl + I```      
    ![1_4](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/1_4.png)    
    2. Buscamos la ubicacion de nuestro respaldo y damos click a ```Next```    
    ![1_5](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/1_5.png)    
    3. Si queremos podemos cambiar el nombre que va a tener el respaldo o lo podemos dejar asi y damos click a ```Import```    
    ![1_6](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/1_6.png)    

    Listo ya tenemos un respaldo de nuestra maquina virtual!!
    ![1_7](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/1_7.png)


## 2.Explicar la nomenclatura del kernel.
* Para poder explicar la nomenclatura de la version del kernel que tenemos tenemos que usar el siguente comando que es   ```uname -r``` para solo ver la version, o ```uname -a``` para tener la informacion completa    
![Explicacion_kernelversion](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/2_0.png)
* La explicacion de la nomemclatura es la siguiente:
    - A. Es el numero de la version del kernel 
    - B. Es el numero de la version actual o sub-version del kernel, es como la version de la version del kernel, si la version es par es estable si es impar significa que es inestable
    - C. Es el numero de las revisiones menores que tiene el kernel, este numero cambia cuando se agregan nuevas caracteristicas al kernel
    - D. Es el numero de correcciones que ha tenido el kernel   
* Como nota el kernel que tenemos en nuestra maquina virtual es este:     
![2_1](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/2_1.png)


## 3.Investigar y enlistar los paquetes requeridos para la compilación y ¿cómo instalarlos desde terminal?.

* Los paquetes que necesitamos, todos se instalan con el comando ```sudo apt intall```, los paquetes que necesitamos son los siguientes:
![3_0](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/3_0.png)
![3_1](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/3_1.png)

- git
- fakeroot
- build-essential	
- ncurses-dev	
- xz-utils	
- libssl-dev	
- bc
- flex
- libelf-dev	
- bison

## 4.¿Cómo descargar una versión de kernel desde terminal?.
* Ocupamos usar el comando ```wget``` la version mas reciente a la fecha de hacer este tutorial es la version ```5.17.5```
![4_0](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/4_0.png)

* El comando completo (para que lo puedan copiar) es:    
```wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.17.5.tar.xz```    
![4_2](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/4_2.png)
En mi caso lo movi a documentos

## 5.¿Cómo extraer el código comprimido del kernel desde terminal?
* Para extraer el codigo comprimido vemos que tiene una extension particular que es ```.tar.xz``` esto nos da la pista que tenemos que usar el comando ```tar xvf```  
![5_0](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/5_0.png)  
Y ahora como podemos ver, ya tenemos la carpeta del kernel que vamos a compilar  
![5_1](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/5_1.png)  

## 6.¿Cómo configurar el kernel?
* Para configurar el Kernel hay dos formas:
    - La primera (y la que vamos a usar) es usar la configuracion que ya viene en nuestra distribucion de linux, la ventaja es que tienes todos los modulos, pero es mas tardado y hace que el kernel sea mas pesado
    - La segunda es usar el comando ```make localmodeconfig``` que es crear una configuracion en base a los dispositivos que tienes conectados, la desventaja es que no podras conectar otras cosas como lo son impresoras, entre otras cosas, pero tienes un kernel mas ligero y rapido.
* Como ya mencionamos vamos a la primera forma la cual es hacer una copia de la configuracion que ya tiene nuestra distribucion de linux, los pasos son los siguientes:
    1. En terminal, nos movemos a la carpeta que descomprimimos en el paso anterior, y escribimos el siguiente comando para copiar la configuracion existente de nuestra distro de linux:  
    ```cp -v /boot/config-$(uname -r) .config```
    2. Una vez creada la copia corremos el siguiente comando para hacer cambios en la configuracion:  
    ```make menuconfig```  
    ![6_0](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/6_0.png)  

    3. Aparecera un menu en el cual podras configurar cosas como el firmware, el sistema de ficheros, etc, cualquier cosas de la que tengas duda la puedes seleccionar usando las flechas de arriba y abajo para seleccionar y con las flecha de derecha a izquierda selecciona la opcion ```Help``` para saber mas de las opciones, si no necesitas modificar nada, selecciona ```Save``` para guardar la configuracion  
    ![6_1](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/6_1.png)  
    ![6_2](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/6_2.png)  

    4. Para salir del menu y regresar a la terminal, una vez guardados los cambios seleccionamos ```Exit``` para salir y asi terminar la configuracion  
    ![6_3](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/6_3.png)  
    ![6_4](https://github.com/Benqui/Practica03_Compilacion-del-kernel-de-Linux/blob/main/Images/6_4.png)  

    
## 7.¿Cómo compilar el código del kernel?

## 8.¿Cómo instalar módulos?

## 9.¿Cómo instalar el kernel?

## 10.¿Cómo indicarle a la computadora con cuál kernel debe iniciar?

## 11.¿Cómo verificar el cambio de kernel a partir de consola?

