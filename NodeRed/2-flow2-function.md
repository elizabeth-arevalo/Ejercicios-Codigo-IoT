# Introducción.

 El segundo ejercicio que realizarás en Node-Red consiste en darle un formato legible para humanos al timestamp utilizando un nodo function para mostrar la fecha en la sección debug. Partiremos del resultado del ejercicio [Marca de tiempo con nodos inject y Debug](https://github.com/elizabeth-arevalo/Ejercicios-Codigo-IoT/blob/main/NodeRed/timestamp-con-NR.md) en Docker.

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
7. Tener instalado los [nodos Dashboard](https://github.com/elizabeth-arevalo/Ejercicios-Codigo-IoT/blob/main/NodeRed/timestamp-con-NR.md)


## [Flow 2: Nodo Function](https://edu.codigoiot.com/mod/lesson/view.php?id=3896&pageid=3821)

1. Entrar a [localhost:1880](http://localhost:1880)
2. Exportar el flow 1 haciendo clic en:
    
    ~~~
    Menu > Exportar > Current Flow > JSON > formatted > download.
    ~~~ 
    - Opcional, tomarlo del [repositorio.](https://github.com/elizabeth-arevalo/Ejercicios-Codigo-IoT/blob/main/NodeRed/Flows/flow1.json)
3. Importar el flow 1 haciendo clic en: 

    ~~~
    Menu > Importar > Seleccionar un archivo para importar > Importar > Importar una copia
    ~~~

4. Configurar el nodo function haciendo doble clic sobre el.

5. Agregar el codigo del [ejemplo ](https://edu.codigoiot.com/mod/lesson/view.php?id=3896&pageid=3824) a la pestaña On Message:
```
// Lo que está después de "//" son comentarios 
// Crea un objeto Date a partir del msg.payload enviado por timestamp 
var date = new Date(msg.payload); 
// Cambia el payload para que sea una fecha con formato 
msg.payload = date.toString(); 
// Regresa el mensaje para que se envíe al siguiente nodo  
return msg;
```

6. Activar el nodo Debug y asegurarse de que el nodo inject este lanzando mensajes cada 5 segundos.
7. Hacer clic en Deploy.

## [Flow 3: Panel de control con Nodos Dashboard](https://edu.codigoiot.com/mod/lesson/view.php?id=3897)

### Requisitos
Contar con los nodos dashboard

### Instrucciones

1. Duplicar el flow 2 con las mecanicas de exportar e importar
2. Renombrar el flow a Flow 3
3. Agregar el nodo texto
4. Crear una pestaña en la sección Dashboard
5. Crear un grupo
6. Configurar el nodo texto para que se visualice en el grupo recien creado
7. Hacer clic en Deploy y consultar el [Dashboard](http://localhost:1880/ui)



## Referencias

- [NodeRed 2022](https://edu.codigoiot.com/course/view.php?id=278)

- [NodeRed](https://nodered.org/)

- [NodeRed en Docker](https://nodered.org/docs/getting-started/docker)

- Documentación de [NodeRed](https://nodered.org/docs/user-guide/nodes)

- Documentacion [toString](https://nodejs.org/api/buffer.html#buftostringencoding-start-end)

## Notas

- El icono azul en los nodos indica que esos nodos no estan desplegados
- Formas de poner texto en codigo en markdown
- Para desactivar un flow hacer clic en la pestaña del flow, hacer clic en el boton disable, clic en done y clic en deploy
- Para cambiar el nombre de un flow hacer doble clic en la pestaña y cambiar el nombre
- Los nodos con un triangulo anaranjado no están configurados


## Resultados
- Flow 2: Ejercicio Nodo Function.

![](https://github.com/elizabeth-arevalo/Ejercicios-Codigo-IoT/blob/main/img/flow2-1.png)

![](https://github.com/elizabeth-arevalo/Ejercicios-Codigo-IoT/blob/main/img/flow2-2.png)

- Flow 3: Panel de control con nodos Dashboard.

![](https://github.com/elizabeth-arevalo/Ejercicios-Codigo-IoT/blob/main/img/flow3-1.png)

![](https://github.com/elizabeth-arevalo/Ejercicios-Codigo-IoT/blob/main/img/flow3-2.png)

![](https://github.com/elizabeth-arevalo/Ejercicios-Codigo-IoT/blob/main/img/flow3-3.png)
