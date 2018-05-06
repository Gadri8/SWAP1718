# Trabajo sobre Nginx y Haproxy
### Por Adrián Gabriel Gámez López

**Nginx**

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

**Configuración Nginx:**
La configuración de un servidor web básico se puede encontrar en el fichero /etc/nginx/nginx.conf, dentro del archivo se modifican las diferentes funciones generales del servidor como:
* El ususario que ejecuta el servidor.
* El número de procesos del servidor, ligados a los núcleos de la CPU.
* El proceso maestro del servidor.
* La ruta dónde se guardarán los ficheros de log.
* La multiconexión.
* La configuración http.

![I_1](./imagenes/Imagen_1.png)

Al final de este fichero, dentro del bloque http, podemos ver una línea por defecto llamada “include /etc/nginx/sites-enabled/*”. Esta línea indica al servidor que debe cargar las configuraciones específicas de diferentes archivos y directorios, a fin de poder funcionar como “servidores virtuales” y permitir habilitar y deshabilitar configuraciones fácilmente sin tener que borrarlas.

Así si editamos el archivo anterior vamos a poder encontrar, entre otras funciones:
* El puerto de escucha, que por defecto es el 80.
* El directorio dónde se almacena la web.
* El fichero por defecto para acceder a la web, en principio es index.html.
* El comportamineto en caso de error 404.
* La configuración de un servidor "virtual".
* Y la configuración HTTPS.

![I_2](./imagenes/Imagen_2.png)

Nginx está presente en sitios web conocidos como: WordPress, Netflix, Ohloh, y partes de Facebook entre otros.

**HAProxy**

Haproxy (High Availability Proxy) es un software Open Source escrito en #C por Willy Tarreau en 2001.
Proporciona un gran servicio de altas prestaciones para balanceo de carga y como servidor proxy para aplicaciones TCP Y HTTP.

HAProxy se centra en asegurar la carga avanzada de equilibrio a través de proporcionar una gran variedad de herramientas y funciones compatibles que sea lo más rápido y eficiente (en la memoria RAM y CPU uso particular) y estable posible. Estas son algunas de las posibilidades clave que HAProxy ofrece:
* Chequeo periódico de servidores.
* Registro avanzado y eprosnalizado.
* Potencia en el análisis de registro.
* Total soporte de HTTP tanto en servidores como en clientes.
* Interfaz gráfico de red.

HAProxy es muy es igual de simple que instalar en terminales Linux y Solaris, simplemente con el uso del comando sudo apt-get install haproxy.

E igualmente el modo de configurarlo es modificando el archivo /etc/haproxy/haproxy.cfg

![I_3](./imagenes/Imagen_3.png)
![I_4](./imagenes/Imagen_4.png)

HAProxy ha sido elegido como balanceador de carga para grandes servicio web como , GitHub, Stack Overflow, Reddit, Tumblr, Twitter y Tuenti, entre otros.

**Comparación**

Las dos soluciones son totalmente gratuitos y funcionales.
Prácticamnete tienen las mismas funcionalidades, son muy buenas soluciones para balanceo de carga, es posible su uso como proxy inverso, pero por parte de Nginx nos ofrece un servicio web completo que haproxy no.
Ambos son asíncronos por consurrencia, usados en balanceo de carga, poseen descarga SSL y compatibles con SPDY por complementos.
Nginx tiene complemento estáticamente compilado.
y HAProxy posee una consola de adminstración.
Por su parte Nginx es multiplataforma pero HAProxy es compatible con proxy TCP. 
Finalmente HAProxy tiene un loggin muy flexible y potente y aporta mucha información de conexión HTTP, una muy activa comunidad una API en tiempo real y una buena GUI, a demás de la peculiaridad de ofrecernos gran disponibilidad ya que se puede agregar/eliminar servidores de respaldo dinámicamente, por su parte falta decir que Nginx es muy fácil de trabaja, pero no es muy aconsejable para sistemas complejos o muy grandes.

**Conclusión**

En definitiva, Nginx nos ofrece la oportunidad de servicio web, es muy simple y sencillo de configurar y prácticamente igual de veloz que su competidor a la hora de balancear carga, pero posee unas claras desventajas en comparación con HAProxy a la hora de gestionar cargas muy grandes, siendo éste servicio elegido por las grandes empresas que soportan millones de accesos diarios en grandes masas.