# Práctica NGINX - Sistemas informáticos

En esta práctica veremos como crear un servidor con el software "Nginx" y configurar 2 virtual hosts para alojar dos páginas con diferentes subdominios.
Dichas páginas las obtendremos en la página "One-html-page-challenge".

## Instalación de Nginx

Simplemente, deberemos ejecutar el comando `sudo apt install nginx`.
Como resultado, tendremos Nginx instalado y ejecutándose.

La carpeta dónde se localiza será: `/etc/nginx`
El contenido de la carpeta será el siguiente.

![imagen](https://user-images.githubusercontent.com/95173613/166676429-be1f16ee-10f8-4fc9-a634-44f8d2a3a44d.png)

## Elección de las dos webs 

Para este ejercicio, como he indiciado en la introducción, se nos propone elegir dos proyectos del "One-html-page-challenge". 

#### Elección 1
[Analog clock](https://github.com/Metroxe/one-html-page-challenge/blob/master/entries/clock.html)

![imagen](https://user-images.githubusercontent.com/95173613/166811872-0e0ca34d-f2b2-460f-ae79-5042081be077.png)

Es un reloj simple pero muy bien diseñado que puede cambiar entre modo día y modo noche.

#### Elección 2
[Bits Rain](https://github.com/Metroxe/one-html-page-challenge/blob/master/entries/bits-rain.html).

![imagen](https://user-images.githubusercontent.com/95173613/166812048-34dccd74-3cdf-40a1-99f5-0d138f1157be.png)

Simplemente bit rain, todo informático tiene el deber de saber qué es y disfrutarlo.

## Configuración de Nginx

En el enunciado se nos solicita que con virtual hosts creemos dos subdominios, uno para cada página html que elijamos. Los dos subdominios que voy a definir son *primero* y *segundo* tal que el resultado sea `primero.jordi.com` y `segundo.jordi.com`

Para conseguir esto tendremos que realizar algunos cambios a la configuración predeterminada.

En la ruta `/etc/nginx` entraremos en `sites-available`. El archivo *default* es el ejemplo y referencia que tenemos de la configuración de virtual hosts. 

El default, como vemos a continuación, es dónde apunta el host de manera predeterminada.

Para crar los nuevos sitios web, debemos hacer `sudo cp default primero.jordi.com` y `sudo cp default segundo.jordi.com`. Ahora en `/etc/nginx/sites-available` tendremos tres archivos, el default y nuestros 2 archivos para la configuración de subdominios.

Con el comando `sudo nano primero.jordi.com` entraremos a la configuración del primer archivo:

![imagen](https://user-images.githubusercontent.com/95173613/166828684-5007eac8-3765-401e-8a99-bfc7c4d9135b.png)

Y cuando acabemos con el primero, deberemos proceder con el segundo, en este caso `sudo nano segundo.jordi.com`:

![imagen](https://user-images.githubusercontent.com/95173613/166829094-7de75c11-c365-4b95-8a9c-38b46abadc90.png)



