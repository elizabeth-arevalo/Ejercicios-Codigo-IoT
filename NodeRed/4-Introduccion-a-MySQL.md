# [Introducción a MySQL](https://edu.codigoiot.com/course/view.php?id=1001)

Para consultar el montaje de este contenedor en Docker, comparto el siguiente repositorio: 

- [Servidor IoT básico con docker compose](https://github.com/codigo-iot/servidor-IoT-basico-docker-compose/tree/main)

Para ello, es necesario seguir paso por paso las instrucciones de dicho contenedor.

### Limitantes
El servidor no está configurado bajo logicas de producción.


- Una DB es un conjunto de información
- MySQL Server es un programa que recibe querys y devuelve información de la DB

## Configurar volumenes externos en MySQL con Docker

- Detener el contenedor de MySQL

	```docker stop [id_contenedor]```
	
- Eliminar el contenedor de MySQL

	```docker rm [id_contenedor]```
	
- Eliminar la imagen de MySQL

	```
	docker images
	docker rmi [id_imagen]
	```
- Detener docker compose. Hay que entrar al directorio de compose

	```docker compose stop```
	

- Actualizar el archivo compose para que use el volumenes. Debe ser el archivo de la carpeta DockerCompose, no el del repositorio. Descomentar la linea del archivo de configuración

- Mover el archivo my.cnf al directorio del volumen asignado para la configuración de MySQL

- Levantar docker compose

	```docker compose up -d```

## Crear una Base de Datos

- Entrar a MySQL

	```
	docker exec -it [id_contenedor] mysql -p
	```

    - Con este comando, te pedirá la contraseña que estableció en el archivo my.cnf del 
- Crear base de datos

	```
	CREATE DATABASE <cursoode_db>;
	```

- Seleccionad base de datos

	```
	USE [nombre_db];
	```
	
- Crear una tabla en la DB

	```
	CREATE TABLE clima (id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY, fecha TIMESTAMP DEFAULT CURRENT_TIMESTAMP, nombre VARCHAR(248) NOT NULL, temperatura FLOAT(4,2) NOT NULL, humedad INT (6) NOT NULL);
	```

- Consultar talba

	```
	SHOW TABLES;
	```
- Describir la tabla

	```
	DESCRIBE [nombre_tabla];
	
- Agregar un dato

	```
	INSERT INTO [nombre_tabla] (columnas) VALUES (valores);
	```
	
	```
	INSERT INTO clima (nombre,temperatura,humedad) VALUES ("Eliza",27,45);
	```
	
- Consultar dato

	```
	SELECT * FROM clima;
	```
- Consulta condicional

	```
	SELECT * FROM clima WHERE id=2;
	SELECT * FROM clima WHERE temperatura=21.5;
	SELECT * FROM clima WHERE nombre="Hugo Escalpelo";
	```

## Referencias

- 10,000 horas no es fuciciente para ser un experto https://www.youtube.com/watch?v=FVK_i7arszw

- Documentación de MySQL para tipos de datos https://dev.mysql.com/doc/refman/8.0/en/integer-types.html

## Resultados.

![](https://github.com/elizabeth-arevalo/Ejercicios-Codigo-IoT/blob/main/img/mysql1-1.png)

![](https://github.com/elizabeth-arevalo/Ejercicios-Codigo-IoT/blob/main/img/mysql1-2.png)