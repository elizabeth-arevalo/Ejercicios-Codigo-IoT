# Introducción.

En el siguiente ejercicio, se realizará un timestamp con los nodos proporcionados por NodeRed en Docker.

Para consultar el montaje de dicho contenedor, comparto el siguiente repositorio: 

- [Servidor IoT básico con docker compose](https://github.com/codigo-iot/servidor-IoT-basico-docker-compose/tree/main)

Para ello, es necesario seguir paso por paso las instrucciones de dicho contenedor.

### Limitantes
El servidor no está configurado bajo logicas de producción.

## Requisitos

1. Tener instalado NodeRed por Docker
2. Comprobar que NodeRed esté funcionando
	- netstat -an | grep 1880
3. Comprobar que docker esté corriendo
	- sudo systemctl status docker
4. Comprobar el estado de los contenedores
	- docker container ls -a
	Alternativemente:
	- docker ps -a
5. Arrancar todos los contedores
	- docker start $(docker ps -a -q)
6. Abrir NodeRed
	- http://localhost:1880

## Instalación de nodos dashboard.

1. Entrar a NodeRed
2. Abrir Manage Palette, mismo que se encuentra en el menú de hamburguesa
3. Seleccionar la pestaña install
4. Buscar la palabra "dashsboard"
    - Instalar los nodos node-red-dashboard

# Ejercicio 1. Timestamp con NodeRed

https://edu.codigoiot.com/mod/lesson/view.php?id=3895&forceview=1

1. Asegurarse que el contenedor funciona con volumenes

    - Comprobar que el archivo compose usa volumenes para la carpeta /data del contenedor de nodeRed
    - Detener el contenedor de NodeRed 
    ```
    docker stop [id_contenedor]
    ```
    - Borrar el contenedor docker rm [id_contenedor]
    - Detener compose con el comando: 
    ```
    docker compose down
    ```
    - Correr el archivo compose con los cambios de volumenes 
    ```
    sudo docker compose up -d
    ```
        Desde el directorio donde se encuentra el archivo YAML

2. Agregar un nodo inject
3. Agregar nodo debug
4. Hacer clic en deploy
5. Ir a la pestaña debug

## Referencias

- [NodeRed 2022](https://edu.codigoiot.com/course/view.php?id=278)

- [NodeRed](https://nodered.org/)

- [NodeRed Docker](https://nodered.org/docs/getting-started/docker)

- [Documentación de NodeRed](https://nodered.org/docs/user-guide/nodes)

# Resultados

![](https://github.com/elizabeth-arevalo/Ejercicios-Codigo-IoT/blob/main/img/timestamp01.png)

![](https://github.com/elizabeth-arevalo/Ejercicios-Codigo-IoT/blob/main/img/timestamp02.png)