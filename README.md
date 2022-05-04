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

En el enunciado se nos solicita que con virtual hosts creemos dos subdominios, uno para cada página html que elijamos.

Para conseguir esto tendremos que realizar algunos cambios a la configuración.
