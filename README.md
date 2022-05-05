# Práctica NGINX - Sistemas informáticos

En esta práctica veremos como crear un servidor con el software "Nginx" y configurar 2 virtual hosts para alojar dos páginas con diferentes subdominios.
Dichas páginas las obtendremos en la página "One-html-page-challenge".

## Índice
[1. Instalación de Nginx](https://github.com/Jordiop/sistemas_nginx/edit/main/README.md#instalaci%C3%B3n-de-nginx)

[2. Configuración de Nginx](https://github.com/Jordiop/sistemas_nginx/edit/main/README.md#configuraci%C3%B3n-de-nginx)

[3. Elección de las web](https://github.com/Jordiop/sistemas_nginx/edit/main/README.md#configuraci%C3%B3n-de-nginx)

[4. Configuración de las web](https://github.com/Jordiop/sistemas_nginx/edit/main/README.md#configuraci%C3%B3n-de-las-dos-web)

[5. Configuración de hosts](https://github.com/Jordiop/sistemas_nginx/edit/main/README.md#configuraci%C3%B3n-de-hosts)

[6. Resultado final](https://github.com/Jordiop/sistemas_nginx/edit/main/README.md#resultado-final)

## Instalación de Nginx

Simplemente, deberemos ejecutar el comando `sudo apt install nginx`.
Como resultado, tendremos Nginx instalado y ejecutándose.

La carpeta dónde se localiza será: `/etc/nginx`
El contenido de la carpeta será el siguiente.

![imagen](https://user-images.githubusercontent.com/95173613/166676429-be1f16ee-10f8-4fc9-a634-44f8d2a3a44d.png)

## Configuración de Nginx

En el enunciado se nos solicita que con virtual hosts creemos dos subdominios, uno para cada página html que elijamos. Los dos subdominios que voy a definir son *primero* y *segundo* tal que el resultado sea `primero.jordi.com` y `segundo.jordi.com`

Para conseguir esto tendremos que realizar algunos cambios a la configuración predeterminada.

En la ruta `/etc/nginx` entraremos en `sites-available`. El archivo *default* es el ejemplo y referencia que tenemos de la configuración de virtual hosts. 

El default, como vemos a continuación, es dónde apunta el host de manera predeterminada.

![imagen](https://user-images.githubusercontent.com/95173613/166829228-f5ccf9f6-1575-4e1d-a36d-e8f1a246b904.png)

Para crar los nuevos sitios web, debemos hacer `sudo cp default primero.jordi.com` y `sudo cp default segundo.jordi.com`. Ahora en `/etc/nginx/sites-available` tendremos tres archivos, el default y nuestros 2 archivos para la configuración de subdominios.

Con el comando `sudo nano primero.jordi.com` entraremos a la configuración del primer archivo:

![imagen](https://user-images.githubusercontent.com/95173613/166828684-5007eac8-3765-401e-8a99-bfc7c4d9135b.png)

Y cuando acabemos con el primero, deberemos proceder con el segundo, en este caso `sudo nano segundo.jordi.com`:

![imagen](https://user-images.githubusercontent.com/95173613/166829094-7de75c11-c365-4b95-8a9c-38b46abadc90.png)

Después de esto, debemos "decirle" a Nginx que tiene dos web disponibles. Para ello vamos a usar links simbólicos que apunten a las webs correspondientes.

En `/etc/nginx/sites-enabled` realizaremos los dos siguientes comandos: 

`sudo ln -s ../sites-available/primero.jordi.com`
`sudo ln -s ../sites-available/segundo.jordi.com`

Como resultado obtendremos dos links simbólicos para que Nginx sea redirigido a nuestros archivos de configuración web sin tener que moverlos.

![imagen](https://user-images.githubusercontent.com/95173613/166909557-612428c6-644d-4c4a-8ebc-04c98b75c763.png)

## Elección de las dos web

Para este ejercicio, como he indiciado en la introducción, se nos propone elegir dos proyectos del "One-html-page-challenge". 

#### Elección 1
[Analog clock](https://github.com/Metroxe/one-html-page-challenge/blob/master/entries/clock.html)

![imagen](https://user-images.githubusercontent.com/95173613/166811872-0e0ca34d-f2b2-460f-ae79-5042081be077.png)

Es un reloj simple pero muy bien diseñado que puede cambiar entre modo día y modo noche.

#### Elección 2
[Bits Rain](https://github.com/Metroxe/one-html-page-challenge/blob/master/entries/bits-rain.html).

![imagen](https://user-images.githubusercontent.com/95173613/166812048-34dccd74-3cdf-40a1-99f5-0d138f1157be.png)

Simplemente bit rain, todo informático tiene el deber de saber qué es y disfrutarlo.

## Configuración de las dos web

Ahora, el directorio que deberemos usar es `/var/www`. Ahí, crearemos las carpetas *primero* para `primero.jordi.com` y *segundo* para `segundo.jordi.com`. El resultado quedará tal que así. 

![imagen](https://user-images.githubusercontent.com/95173613/166830515-7f958065-ed3f-445c-882d-53dcb0095f0a.png)

Dentro de primero, guardaremos nuestro html con la página deseada con el nombre index. Para ello, crearemos el achivo con `sudo nano`, escribir o copiar el html dentro y guardarlo como index.html

![imagen](https://user-images.githubusercontent.com/95173613/166830880-ab3bc336-5c56-4c7f-b6b4-51411ca58274.png)

Dentro de segundo, realizaremos el mismo proceso pero con el html que queramos para el segundo subdominio.

![imagen](https://user-images.githubusercontent.com/95173613/166830941-2c7d83c3-a9f0-4c6f-9d41-8571c48b5cb8.png)

Acabaremos con el contenido tal que, la carpeta primero tendrá un archivo de nombre index.html y la carpeta segundo también tendrá un archivo de nombre index.html. 

## Configuración de hosts

Para finalizar, deberemos de tocar el archivo hosts para que cuando pongamos `primero.jordi.com` y `segundo.jordi.com` nos muestre la página correspondiente.

El archivo hosts está en `/etc` y lo editaremos con `sudo nano hosts`.

Añadiremos la siguiente línea `127.0.0.1  primero.jordi.com segundo.jordi.com`

Con el siguiente resultado

![imagen](https://user-images.githubusercontent.com/95173613/166831545-87396977-3547-42f9-8570-d64a0eeb669c.png)

## Resultado final

#### primero.jordi.com

![imagen](https://user-images.githubusercontent.com/95173613/166831654-666742d9-ad3d-4d91-96c6-f31a3ae82b33.png)

#### segundo.jordi.com

![imagen](https://user-images.githubusercontent.com/95173613/166831770-36ceb5f9-7757-48af-b8c7-39682ebf0834.png)

