# Trabajo sobre Nginx y Haproxy
### Por Adrián Gabriel Gámez López

##Nginx

Nginx (engine x) es un servidor web modular de código abierto desarrollado por el ruso Igor Sysoev en 2004.
Está programado para hacer las funciones de:
* Acelerador de aplicaciones y contenidos.
* Servidoe proxy inverso para servicios HTTP, TCP, UCP o como peoxy de correo IMAP o POP3.
* Cifrado de datos seguros (TLS).
* Gestor ancho de banda.
* Balanceador de carga.
* Streaming de video.

NGINX está diseñado para ofrecer un bajo uso de memoria y alta concurrencia.
Ya que en lugar de crear nuevos procesos para cada solicitud web, NGINX usa un enfoque asincrónico basado en eventos donde las solicitudes se manejan en un solo hilo.

Un proceso maestro mantiene los procesos de trabajo, y son estos lo que hacen el procesamiento real y al ser asíncrono, cada solicitud se ejecuta por el proceso de trabajo de forma concurrente sin bloquear otras solicitudes.

Este software es soportado por una gran variedad de sistemas operativos, incluyendo variantes de UNIX / Linux, Mac OS o Windows.

La instalación del servicio es muy simple, desde lineas de comandos en distribuciones Linux, basta con unos simples comandos, e incluso desde otras distibuciones es tan fácil como seguir el instalador pasao a paso.

Para el desarrollo de la configuración en esta práctica me centraré en la parte dedicada a Linux.

##Configuración Nginx:
La configuración de un servidor web básico se puede encontrar en el fichero /etc/nginx/ dentro del archivo se modifican las diferentes funciones generales del servidor como:
* El ususario que ejecuta el servidor.
* El número de procesos del servidor, ligados a los núcleos de la CPU.
* El proceso maestro del servidor.
* La ruta dónde se guardarán los ficheros de log.
* La multiconexión.
* La configuración http.

Al final de este fichero, dentro del bloque http, podemos ver una línea por defecto llamada “include /etc/nginx/sites-enabled/*”. Esta línea indica al servidor que debe cargar las configuraciones específicas de diferentes archivos y directorios, a fin de poder funcionar como “servidores virtuales” y permitir habilitar y deshabilitar configuraciones fácilmente sin tener que borrarlas.

Así si editamos el archivo anterior vamos a poder encontrar, entre otras funciones:
* El puerto de escucha, que por defecto es el 80.
* El directorio dónde se almacena la web.
* El fichero por defecto para acceder a la web, en principio es index.html.
* El comportamineto en caso de error 404.
* La configuración de un servidor "virtual".
* Y la configuración HTTPS.

![I_1](../imagenes/Imagenes_1.png)
![I_2](../imagenes/Imagenes_2.png)