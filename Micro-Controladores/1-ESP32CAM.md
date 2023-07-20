# Introducción. 

A continuación, se mostrará paso a paso la configuración del micro-controlador ESP32-CAM. Se realizará la configuración del IDE de Arduino.

Para esto, es necesario configurar el gestor de tarjetas, añadir las tarjetas ESPRESSIF, añadir drivers, seleccionar las características del micro-controlador y configurar Python.

# Objetivo.

Realizar la configuración del IDE de Arduino para poder cargar programas al ESP32-CAM.

# Requisitos.

- Módulo ESP32-CAM.
    - Tipo AI-Thinker.
    - Procesador ESP32-S a 240MHZ y 4MB ROM.
- Cámara módelo OV2640.
- Programador FTDI o convertidor TTL-USB equivalente.
- Protoboard.
- Cables Jumper.
- SO Ubuntu 20.04 o superior.
- IDE Arduino 1.8.1 o superior para Linux.
- Git para Linux.
- Conexión a Internet.

## Configuración del IDE de Arduino.

### Instrucciones.

1. Instalar la IDE de Arduino.
    - Descargar la IDE más reciente, seleccionando la opción de acuerdo al SO del sitio web de [Arduino.](https://www.arduino.cc/en/software)
    - Una vez descargado, se abrirá una terminal donde se encuentra el archivo .AppImage descargado.
    - Se le darán permisos de ejecución con el siguiente comando:

    ~~~
    chmod u=x arduino...AppImage
    ~~~

    - Se puede comprobar sus permisos con el siguiente comando para confirmarlo :

    ~~~
    ls -l
    ~~~

2. Ejecutar la IDE de Arduino.
    - Este programa se puede ejecutar de dos formas:
    1. Dando clic dos veces en el programa.
    2. Ejecutando el siguiente comando.
    ~~~
    ./arduino...AppImage
    ~~~
    - Este paso puede tardar un poco dependiendo del HW del equipo en el que se esté ejecutando.

    - Si aparece un error porque no encuentra FUSE, ejecutar los siguientes comandos:

    ~~~
    sudo add-apt-repository universe
    sudo apt install libfuse2
    ~~~


3. Una vez el programa esta abierto, se debe abrir la pestaña File > Preferences (o por defecto acceder con las teclas Ctrl + ,) 
4. En el cuadro de diálogo que aparece, pega la siguiente URL en la sección Additional Boards Manager.

~~~
https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_dev_index.json
~~~

5. Dar clic en el Boards Manager que esta en el menú horizontal, ahí se buscará el paquete **esp32** 

## Configuración de los drivers para ESP32-CAM.

### Instrucciones.

Una vez realizada la instalación del paquete, es necesario configurar los drivers para el micro-controlador.

1. Agregar el usuario personal al grupo "dialout" para que tenga privilegios de Super Usuario sin acceder al usuario root o sudo.
    ~~~
    sudo usermod -a -G dialout $USER
    ~~~
    - Nota: el comando usermod permite modificar al usuario, mientras que -aG le da todos los privilegios y lo añade a un grupo, mientras que $USER es una variable global donde se almacena tu usuario.
2. Verificar si el usuario está en el grupo con el siguiente comando:
    ~~~
    groups
    ~~~
3. Correr los siguientes comandos en terminal:
~~~
wget https://bootstrap.pypa.io/get-pip.py
sudo apt-get install python3-distutils
sudo apt-get install python3-apt
sudo python3 get-pip.py
sudo pip3 install pyserial
mkdir -p ~/Arduino/hardware/espressif
cd ~/Arduino/hardware/espressif
git clone https://github.com/espressif/arduino-esp32.git esp32
cd esp32
git submodule update --init --recursive
cd tools
python3 get.py

~~~

Nota: Es importante correr todos los comandos uno por uno en el orden indicado.

## Resultados.

![](https://github.com/elizabeth-arevalo/Ejercicios-Codigo-IoT/blob/main/img/esp32-1.png)