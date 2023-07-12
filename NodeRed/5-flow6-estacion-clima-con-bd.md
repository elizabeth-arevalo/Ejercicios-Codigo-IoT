# Estación climátiica - Historico

## Requisitos previos

1. Obtener una cuenta gratuita de OpenWeatherMap.org

2. Obtener una API Key

3. [Construir la solicitud API](https://openweathermap.org/api/one-call-3#data)

https://api.openweathermap.org/data/3.0/onecall?lat={lat}&lon={lon}&units={units}


## Introdución.

Continuando con el Flow 4, se implementará una base de datos [MySQL](https://github.com/elizabeth-arevalo/Ejercicios-Codigo-IoT/blob/main/NodeRed/4-Introduccion-a-MySQL.md) de nuestro contenedor Docker, misma base de datos que se realizó anteriormente.

Para consultar el montaje de este contenedor en Docker, comparto el siguiente repositorio: 

- [Servidor IoT básico con docker compose](https://github.com/codigo-iot/servidor-IoT-basico-docker-compose/tree/main)

Para ello, es necesario seguir paso por paso las instrucciones de dicho contenedor.

### Limitantes
El servidor no está configurado bajo logicas de producción.

lat= 19.432694
lon= -99.133472

### Requisitos

- Tener funcionando [NodeRed.](http://localhost:1880)
- Servidor IoT básico con [docker compose.](https://github.com/codigo-iot/servidor-IoT-basico-docker-compose/tree/main)
- Tener funcionando MySQL. 

## Instrucciones.

1. Clonar el repositorio
	- Con github desktop hacer clic en el boton repositorios
	- Clic en add
	- Clic en clonar repositorio
	- Seleccionar URL
	- https://github.com/codigo-iot/flow6-clima-api-docker-compose-mysql.git

2. Importar el flow

    - Asegurarse de que los contenedores funcionan

	```
	docker start $(docker ps -a -q)
	```
	
3. Crear en MySQL un usuario con acceso publico

    - Entrar a la terminal de MySQL

	```
	docker exec -it [id_contenedor] mysql -p
	```
	
    - Crear el usuario con acceso público

	```
	CREATE USER 'usuario'@'%' IDENTIFIED BY 'password';
	GRANT ALL PRIVILEGES ON *.* TO 'usuario'@'%';
	```
	
4. Configurar el flow recien importado

    - Nodo MQTT Local debe estar conectado al broker local y que la salida sea string

    - Configurar la interfaz de los nodos dashboard
        
    - El nodo injet de la sección API debe funcionar cada minot

    - Cofigurar correctamente la solicitud API del nodo http request

        - [API KEY](https://api.openweathermap.org/data/2.5/weather?lat=19.432380&lon=-99.133329&appid=a0f4e98d1a27e3c4b7b53aab05fa9d75&units=metric)

    - Colocar la solicitud API en el campo URL del nodo httprequest

5. Asegurarse de que los nodos MQTT de la seccion Enviador y Escuchador usan el broker público. 
    
    - Tema: codigoIoT/mqtt/climaAPI
    - Server: 52.57.47.134

6. Configurar el nodo JSON público para que indique usuario y ciudad

7. Instalar y configurar el nodo MySQL

    ~~~
    Nodos: node-red-node-mysql

    Host: mysql
    user:  usuario publico
    password: contraseña
    database: cursoIoT
    ~~~


## Referencias.

- [NodeRed 2022](https://edu.codigoiot.com/course/view.php?id=278)

- [NodeRed](https://nodered.org/)

- [NodeRed en Docker](https://nodered.org/docs/getting-started/docker)

- Documentación de [NodeRed](https://nodered.org/docs/user-guide/nodes)

- Documentacion [toString](https://nodejs.org/api/buffer.html#buftostringencoding-start-end)

## Resultados

