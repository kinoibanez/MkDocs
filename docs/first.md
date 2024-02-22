# 5.4-Dockerizar
Este documento git es para la práctica que tenemos que Dockerizar y crear archivos de dockerfile para el juego 2048.


# Docker file para UBUNTU

    ```

    FROM ubuntu:23.04

    #Hay que instalar APACHE2 para ubuntu

    #Hay que poner un cmd para ubuntu

    LABEL author="Joaquin Gonzalez IAW"

    #En el run podemos poner la continuidad de los comadnos con ; o &&
    #rm -rf /var/lib/apt/lists/* --> Borrará todos los archivos cuando hacemos el update

    RUN apt update \
        && apt install git -y \
        && apt install apache2 -y \
        && rm -rf /var/lib/apt/lists/*

    #Podemos tener dos capas diferentes para poder reutilizar cada "CAPA" de una manera diferente.
    RUN git clone https://github.com/josejuansanchez/2048.git /app \
        && mv /app/* /var/www/html \
        && rm -rf /app 

    #Para ejecutar la docker run -d -p 80:80 2048

    CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND" ]
    ```

# Docker File NGINX

    ```

    FROM nginx:23.04

    #Hay que instalar NGINX para ubuntu

    #Hay que poner un cmd para ubuntu

    LABEL author="Joaquin Gonzalez IAW"

    #En el run podemos poner la continuidad de los comadnos con ; o &&
    #rm -rf /var/lib/apt/lists/* --> Borrará todos los archivos cuando hacemos el update

    RUN apt update \
        && apt install git -y \
        && apt install nginx -y \ 
        && rm -rf /var/lib/apt/lists/*

    #Podemos tener dos capas diferentes para poder reutilizar cada "CAPA" de una manera diferente.
    RUN git clone https://github.com/josejuansanchez/2048.git /app \
        && mv /app/* /usr/share/nginx/html \
        && rm -rf /app 

    #Para ejecutar la docker run -d -p 80:80 2048
    ```