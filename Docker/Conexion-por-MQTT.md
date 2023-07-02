# Ejercicio: Conexión por medio de Mosquitto.

## Requisitos. 

Para el ejercicio realizado a continuación, se hizo uso del repositorio proporcionado a continuación.

- [Servidor IoT básico con docker compose](https://github.com/codigo-iot/servidor-IoT-basico-docker-compose/tree/main)

Para ello, es necesario seguir paso por paso las instrucciones de dicho contenedor.

### Limitantes
El servidor no está configurado bajo logicas de producción.


## Instrucciones.

1. Una vez instalado Docker y clonado el repositorio antes compartido, se deberá seguir las instrucciones del Servidor.
2. Hecho esto, se comprobará el estado de Docker con el siguiente comando.

    ```
    docker  ps -a
    ```

    - En el caso de que los contenedores de docker no estén levantados, se deberá realizar el siguiente comando:

    ```
    docker compose up -d
    ```

3. Usando el [id_contenedor] que nos arroje el comando **docker ps -a**. deberás realizar el comando para suscribirte a un tema:

    ```
    docker exec -it [id-contenedor] mosquitto_sub -h [Dirección-IP] -t [tema-Mqtt]
    ```

4. En el caso de la publicación de mensajes, se abrirá otra terminal con el mismo tema al que se suscribió, añadiendo **-m** y entre parentesis, el mensaje que se reflejará a la terminal a la que se esta suscrito.

    ```
    docker exec -it [id-contenedor] mosquitto_pub -h [Dirección-IP] -t [tema-Mqtt] -m "Hola, esta es una prueba"
    ```

5. Para cerrar la suscripción de Mosquitto solo se debe presionar la tecla Ctrl + C.

# Resultados.

![](https://github.com/elizabeth-arevalo/Ejercicios-Codigo-IoT/blob/main/img/mqtt-sub01.png)

![](https://github.com/elizabeth-arevalo/Ejercicios-Codigo-IoT/blob/main/img/mqtt-pub01.png)

![](https://github.com/elizabeth-arevalo/Ejercicios-Codigo-IoT/blob/main/img/mqtt-sub02.png)