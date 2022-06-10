# ExamneSISTEMA
## Procedimiento

En el linux si no dispone de docker destop es necesario descargar el docker compose para desplegar el web app en el docker podemos utilizar 
siguiente comando para descargarlo.

~~~
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
~~~

Cambiando el 1.29.2 si quieres otras versiones.

Para poder levantar los 3 contenedores de una sola vez necesitaremos un documento.yml con siguientes configuraciones:

![](https://github.com/ZhijunLin7/ExamneSISTEMA/blob/main/Imatges/1.1.png)

Un base de datos imagen my sql que este situados en el puerto 3308 , el voluemn ponemos una carpeta donde existe un .sql para cuando arranque el 
servidor aparezca en el base de datos, Tambien definimos el usuario su contraseña y de root.

![](https://github.com/ZhijunLin7/ExamneSISTEMA/blob/main/Imatges/1.2.png)

Una de phpmyadmin que depende de base de datos paraque pueda acceder con un interfaz visual y lo pondremos en el puerto 8081 y lo podemos acceder desde
localhost:8081.

![](https://github.com/ZhijunLin7/ExamneSISTEMA/blob/main/Imatges/1.3.png)

Finalmente uno de web tomcat que este situada en el puerto 8082 y le indicamos donde esta el .war para desplegar que depende de base de datos.

![](https://github.com/ZhijunLin7/ExamneSISTEMA/blob/main/Imatges/1.4.png)

El documento completo(Es muy importante los espacion):

![](https://github.com/ZhijunLin7/ExamneSISTEMA/blob/main/Imatges/1.5.png)

Ahora lo arrancamos con el comando:

~~~
docker-compose up -d
~~~

![](https://github.com/ZhijunLin7/ExamneSISTEMA/blob/main/Imatges/1.6.png)

Vamos al puerto 8081 para ver el phpmyadmin y logueamos con el contraseña definida en el .yml:

![](https://github.com/ZhijunLin7/ExamneSISTEMA/blob/main/Imatges/1.7.png)


Para ver el proyecto iremos al puerto 8082 pero le añadiremos el nombre de nuestro .war pues sera http://localhost:8082/LoginWebApp/:


![](https://github.com/ZhijunLin7/ExamneSISTEMA/blob/main/Imatges/1.8.png)

Comprobamos que todo funciona, crearemos un dockerfile para crear la imagen.

![](https://github.com/ZhijunLin7/ExamneSISTEMA/blob/main/Imatges/1.9.png)

Con la imagen creado podemos usar siguente comando para ponerle tag y empujarlo al Docker hub:
~~~
docker tag sis zhijunlin/examensis
~~~
~~~
docker push zhijunlin/examensis
~~~
![](https://github.com/ZhijunLin7/ExamneSISTEMA/blob/main/Imatges/1.10.png)
![](https://github.com/ZhijunLin7/ExamneSISTEMA/blob/main/Imatges/1.11.png)
Link de docker hub: https://hub.docker.com/r/zhijunlin/examensis













