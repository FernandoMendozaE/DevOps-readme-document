<div id="top"></div>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://www.nginx.com/">
    <img src="images/nginx.png" alt="Logo" width="90" height="90">
  </a>

  <h3 align="center">Documentación-NGINX</h3>

  <p align="center">
    <br />
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Tabla de contenido</summary>
  <ol>
    <li>
      <a href="#introducción-a-nginx">Introducción a NGINX</a>
    </li>
    <li>
      <a href="#cómo-instalar-nginx">Cómo instalar NGINX</a>
      <ul>
        <li><a href="#cómo-máquina-virtual-local-con-vagrant">Cómo máquina virtual local con Vagrant</a>
          <ul>
            <li><a href="#agregar-dominio-a-su-archivo-de-hosts">Agregar dominio a su archivo de hosts</a>
          </ul>
        </li>
        <li><a href="#instalar-nginx">Instalar NGINX</a></li>
      </ul>
    </li>
    <li><a href="#introducción-a-los-archivos-de-configuración-de-nginx">Introducción a los archivos de configuración de NGINX</a></li>
    <li>
      <a href="#cómo-configurar-un-servidor-web-básico">Cómo configurar un servidor web básico</a>
      <ul>
        <li><a href="#cómo-escribir-su-primer-archivo-de-configuración">Cómo escribir su primer archivo de configuración</a></li>
        <li><a href="#cómo-validar-y-recargar-archivos-de-configuración">Cómo validar y recargar archivos de configuración</a></li>
        <li><a href="#cómo-entender-directivas-y-contextos-en-nginx">Cómo entender directivas y contextos en NGINX</a></li>
        <li><a href="#cómo-servir-contenido-estático-usando-nginx">Cómo servir contenido estático usando NGINX</a></li>
        <li><a href="#manejo-de-tipos-de-archivos-estáticos-en-nginx">Manejo de tipos de archivos estáticos en NGINX</a></li>
        <li><a href="#cómo-incluir-archivos-de-configuración-parciales">Cómo incluir archivos de configuración parciales</a></li>
      </ul>
    </li>
    <li>
      <a href="#enrutamiento-dinámico-en-nginx">Enrutamiento dinámico en NGINX</a>
      <ul>
        <li><a href="#coincidencias-de-ubicación">Coincidencias de ubicación</a></li>
        <li><a href="#variables-en-nginx">Variables en NGINX</a></li>
        <li><a href="#redirecciones-y-reescrituras">Redirecciones y reescrituras</a></li>
        <li><a href="#cómo-probar-varios-archivos">Cómo probar varios archivos</a></li>
      </ul>
    </li>
    <li><a href="#iniciar-sesión-en-nginx">Iniciar sesión en NGINX</a></li>
    <li>
      <a href="#cómo-usar-nginx-como-proxy-inverso">Cómo usar NGINX como proxy inverso</a>
      <ul>
        <li><a href="#node-con-nginx">Node con NGINX</a></li>
        <li><a href="#php-con-nginx">PHP con NGINX</a></li>
      </ul>
    </li>
    <li><a href="#cómo-utilizar-nginx-como-equilibrador-de-carga">Cómo utilizar NGINX como equilibrador de carga</a></li>
    <li>
      <a href="#cómo-optimizar-nginx-para-obtener-el-máximo-rendimiento">Cómo optimizar NGINX para obtener el máximo rendimiento</a>
      <ul>
        <li><a href="#cómo-configurar-procesos-de-trabajo-y-conexiones-de-trabajo">Cómo configurar procesos de trabajo y conexiones de trabajo</a></li>
        <li><a href="#cómo-almacenar-contenido-estático-en-caché">Cómo almacenar contenido estático en caché</a></li>
        <li><a href="#cómo-comprimir-respuestas">Cómo comprimir respuestas</a></li>
      </ul>
    </li>
    <li><a href="#cómo-entender-el-archivo-de-configuración-principal">Cómo entender el archivo de configuración principal</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>

  </ol>
</details>

<!-- ABOUT THE PROJECT -->

## Introducción a NGINX

NGINX es un servidor web de alto rendimiento desarrollado para satisfacer las crecientes necesidades de la web moderna. Se enfoca en alto rendimiento, alta concurrencia y bajo uso de recursos. Aunque se lo conoce principalmente como un servidor web, NGINX en esencia es un servidor proxy inverso .

Sin embargo, NGINX no es el único servidor web en el mercado. Uno de sus mayores competidores es Apache HTTP Server (httpd) , lanzado por primera vez en 1995. A pesar de que Apache HTTP Server es más flexible, los administradores de servidores a menudo prefieren NGINX por dos razones principales:

- Puede manejar un mayor número de solicitudes simultáneas.
- Tiene una entrega de contenido estático más rápida con un bajo uso de recursos.

Si eso parece un poco complicado de entender, no se preocupe. Tener una comprensión básica del funcionamiento interno será suficiente por ahora.

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/2021/04/wQszK2rvq-1.png" alt="screenshot" />
</div>

NGINX es más rápido en la entrega de contenido estático y se mantiene relativamente más liviano en recursos porque no incorpora un procesador de lenguaje de programación dinámico. Cuando llega una solicitud de contenido estático, NGINX simplemente responde con el archivo sin ejecutar ningún proceso adicional.

Eso no significa que NGINX no pueda manejar solicitudes que requieren un procesador de lenguaje de programación dinámico. En tales casos, NGINX simplemente delega las tareas a procesos separados como PHP-FPM , Node.js o Python . Luego, una vez que ese proceso termina su trabajo, NGINX revierte la respuesta al cliente.

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/2021/04/_nT7rcdjG.png" alt="screenshot" />
</div>

NGINX también es mucho más fácil de configurar gracias a una sintaxis de archivo de configuración inspirada en varios lenguajes de secuencias de comandos que da como resultado archivos de configuración compactos y fáciles de mantener.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo instalar NGINX

Instalar NGINX en un sistema basado en Linux es bastante sencillo. Puede usar un servidor privado virtual que ejecuta Ubuntu como su área de juegos, o puede aprovisionar una máquina virtual en su sistema local usando Vagrant.

### Cómo máquina virtual local con Vagrant

Vagrant es una herramienta de código abierto de Hashicorp que le permite aprovisionar máquinas virtuales usando archivos de configuración simples.

Cree un directorio de trabajo en algún lugar de su sistema con un nombre sensato. El mío es `~/vagrant/nginx-handbook` directorio.

Dentro del directorio de trabajo, cree un archivo llamado `Vagrantfiley` coloque el siguiente contenido allí:

```sh
Vagrant.configure("2") do |config|

    config.vm.hostname = "nginx-handbook-box"

    config.vm.box = "ubuntu/focal64"

    config.vm.define "nginx-handbook-box"

    config.vm.network "private_network", ip: "192.168.20.20"

    config.vm.provider "virtualbox" do |vb|
      vb.cpus = 1
      vb.memory = "1024"
      vb.name = "nginx-handbook"
    end

  end
```

Este `Vagrantfilees` el archivo de configuración del que hablé anteriormente. Contiene información como el nombre de la máquina virtual, la cantidad de CPU, el tamaño de la RAM, la dirección IP y más.

Para iniciar una máquina virtual usando esta configuración, abra su terminal dentro del directorio de trabajo y ejecute el siguiente comando:

```sh
vagrant up

# Bringing machine 'nginx-handbook-box' up with 'virtualbox' provider...
# ==> nginx-handbook-box: Importing base box 'ubuntu/focal64'...
# ==> nginx-handbook-box: Matching MAC address for NAT networking...
# ==> nginx-handbook-box: Checking if box 'ubuntu/focal64' version '20210415.0.0' is up to date...
# ==> nginx-handbook-box: Setting the name of the VM: nginx-handbook
# ==> nginx-handbook-box: Clearing any previously set network interfaces...
# ==> nginx-handbook-box: Preparing network interfaces based on configuration...
#     nginx-handbook-box: Adapter 1: nat
#     nginx-handbook-box: Adapter 2: hostonly
# ==> nginx-handbook-box: Forwarding ports...
#     nginx-handbook-box: 22 (guest) => 2222 (host) (adapter 1)
# ==> nginx-handbook-box: Running 'pre-boot' VM customizations...
# ==> nginx-handbook-box: Booting VM...
# ==> nginx-handbook-box: Waiting for machine to boot. This may take a few minutes...
#     nginx-handbook-box: SSH address: 127.0.0.1:2222
#     nginx-handbook-box: SSH username: vagrant
#     nginx-handbook-box: SSH auth method: private key
#     nginx-handbook-box: Warning: Remote connection disconnect. Retrying...
#     nginx-handbook-box: Warning: Connection reset. Retrying...
#     nginx-handbook-box:
#     nginx-handbook-box: Vagrant insecure key detected. Vagrant will automatically replace
#     nginx-handbook-box: this with a newly generated keypair for better security.
#     nginx-handbook-box:
#     nginx-handbook-box: Inserting generated public key within guest...
#     nginx-handbook-box: Removing insecure key from the guest if it's present...
#     nginx-handbook-box: Key inserted! Disconnecting and reconnecting using new SSH key...
# ==> nginx-handbook-box: Machine booted and ready!
# ==> nginx-handbook-box: Checking for guest additions in VM...
# ==> nginx-handbook-box: Setting hostname...
# ==> nginx-handbook-box: Configuring and enabling network interfaces...
# ==> nginx-handbook-box: Mounting shared folders...
#     nginx-handbook-box: /vagrant => /home/fhsinchy/vagrant/nginx-handbook

vagrant status

# Current machine states:

# nginx-handbook-box           running (virtualbox)
```

Si todo se hizo correctamente, debe iniciar sesión en su máquina virtual, lo que será evidente por la `vagrant@nginx-handbook-box` línea en su terminal.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Agregar dominio a su archivo de hosts

Se podrá acceder a esta máquina virtual en **http://192.168.20.20** en su máquina local. Incluso puede asignar un dominio personalizado como **http://nginx-handbook.test** a la máquina virtual agregando una entrada a su archivo de **hosts** :

```sh
# on mac and linux terminal
sudo nano /etc/hosts

# on windows command prompt as administrator
notepad c:\windows\system32\drivers\etc\hosts
```

Ahora agregue la siguiente línea al final del archivo:

```sh
192.168.20.20   nginx-handbook.test
```

Ahora debería poder acceder a la máquina virtual en **http://nginx-handbook.test** URI en su navegador.

Puede detener o destruir la máquina virtual ejecutando los siguientes comandos dentro del directorio de trabajo:

```bash
# to stop the virtual machine
vagrant halt

# to destroy the virtual machine
vagrant destroy
```

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Instalar NGINX

Suponiendo que haya iniciado sesión en su servidor o máquina virtual, lo primero que debe hacer es realizar una actualización. Ejecute el siguiente comando para hacerlo:

```sh
sudo apt update && sudo apt upgrade -y
```

Después de la actualización, instale NGINX ejecutando el siguiente comando:

```sh
sudo apt install nginx -y
```

Una vez que se realiza la instalación, NGINX debe registrarse automáticamente como un `systemd` servicio y debe estar ejecutándose. Para verificar, ejecute el siguiente comando:

```sh
sudo systemctl status nginx

# ● nginx.service - A high performance web server and a reverse proxy server
#      Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
#      Active: active (running)
```

Si el estado dice `running`, entonces está listo para continuar. De lo contrario, puede iniciar el servicio ejecutando este comando:

```sh
sudo systemctl start nginx
```

Finalmente, para una verificación visual de que todo funciona correctamente, visite su servidor/máquina virtual con su navegador favorito y debería ver la página de bienvenida predeterminada de NGINX:

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/size/w1600/2021/04/image-89.png" alt="screenshot" />
</div>

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Introducción a los archivos de configuración de NGINX

Como servidor web, el trabajo de NGINX es servir contenido estático o dinámico a los clientes. Pero la forma en que se servirá ese contenido generalmente se controla mediante archivos de configuración.

Los archivos de configuración de NGINX terminan con la `.conf` extensión y generalmente se encuentran dentro del `/etc/nginx/` directorio. Comencemos `cd` ingresando a este directorio y obteniendo una lista de todos los archivos:

```sh
cd /etc/nginx

# lista archivos en formato largo con tamaños de archivo legibles
ls -lh

# drwxr-xr-x 2 root root 4.0K Apr 21  2020 conf.d
# -rw-r--r-- 1 root root 1.1K Feb  4  2019 fastcgi.conf
# -rw-r--r-- 1 root root 1007 Feb  4  2019 fastcgi_params
# -rw-r--r-- 1 root root 2.8K Feb  4  2019 koi-utf
# -rw-r--r-- 1 root root 2.2K Feb  4  2019 koi-win
# -rw-r--r-- 1 root root 3.9K Feb  4  2019 mime.types
# drwxr-xr-x 2 root root 4.0K Apr 21  2020 modules-available
# drwxr-xr-x 2 root root 4.0K Apr 17 14:42 modules-enabled
# -rw-r--r-- 1 root root 1.5K Feb  4  2019 nginx.conf
# -rw-r--r-- 1 root root  180 Feb  4  2019 proxy_params
# -rw-r--r-- 1 root root  636 Feb  4  2019 scgi_params
# drwxr-xr-x 2 root root 4.0K Apr 17 14:42 sites-available
# drwxr-xr-x 2 root root 4.0K Apr 17 14:42 sites-enabled
# drwxr-xr-x 2 root root 4.0K Apr 17 14:42 snippets
# -rw-r--r-- 1 root root  664 Feb  4  2019 uwsgi_params
# -rw-r--r-- 1 root root 3.0K Feb  4  2019 win-utf
```

Entre estos archivos, debe haber uno llamado **nginx.conf** . Este es el archivo de configuración principal para NGINX. Puedes echar un vistazo al contenido de este archivo usando el `cat` programa:

```sh
cat nginx.conf

# user www-data;
# worker_processes auto;
# pid /run/nginx.pid;
# include /etc/nginx/modules-enabled/*.conf;

# events {
#     worker_connections 768;
#     # multi_accept on;
# }

# http {

#     ##
#     # Basic Settings
#     ##

#     sendfile on;
#     tcp_nopush on;
#     tcp_nodelay on;
#     keepalive_timeout 65;
#     types_hash_max_size 2048;
#     # server_tokens off;

#     # server_names_hash_bucket_size 64;
#     # server_name_in_redirect off;

#     include /etc/nginx/mime.types;
#     default_type application/octet-stream;

#     ##
#     # SSL Settings
#     ##

#     ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3; # Dropping SSLv3, ref: POODLE
#     ssl_prefer_server_ciphers on;

#     ##
#     # Logging Settings
#     ##

#     access_log /var/log/nginx/access.log;
#     error_log /var/log/nginx/error.log;

#     ##
#     # Gzip Settings
#     ##

#     gzip on;

#     # gzip_vary on;
#     # gzip_proxied any;
#     # gzip_comp_level 6;
#     # gzip_buffers 16 8k;
#     # gzip_http_version 1.1;
#     # gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;

#     ##
#     # Virtual Host Configs
#     ##

#     include /etc/nginx/conf.d/*.conf;
#     include /etc/nginx/sites-enabled/*;
# }


# #mail {
# #    # See sample authentication script at:
# #    # http://wiki.nginx.org/ImapAuthenticateWithApachePhpScript
# #
# #    # auth_http localhost/auth.php;
# #    # pop3_capabilities "TOP" "USER";
# #    # imap_capabilities "IMAP4rev1" "UIDPLUS";
# #
# #    server {
# #        listen     localhost:110;
# #        protocol   pop3;
# #        proxy      on;
# #    }
# #
# #    server {
# #        listen     localhost:143;
# #        protocol   imap;
# #        proxy      on;
# #    }
# #}
```

Intentar comprender este archivo en su estado actual será una pesadilla. Así que cambiemos el nombre del archivo y creemos uno nuevo vacío:

```sh
cd /etc/nginx/

# renames the file
sudo mv nginx.conf nginx.conf.backup

# creates a new file
sudo touch nginx.conf
```

Le **recomiendo encarecidamente** que no edite el archivo original `nginx.conf` a menos que sepa absolutamente lo que está haciendo. Con fines de aprendizaje, puede cambiarle el nombre.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo configurar un servidor web básico

El objetivo de esta sección es presentarle la sintaxis y los conceptos fundamentales de los archivos de configuración de NGINX.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo escribir su primer archivo de configuración

Comience abriendo el `nginx.conf `archivo recién creado con el editor de texto `nvim` :

```sh
sudoedit /etc/nginx/nginx.conf
```

Después de abrir el archivo, actualice su contenido para que se vea así:

```sh
events {

}

http {

    server {

        listen 80;
        server_name nginx-handbook.test;

        return 200 "Bonjour, mon ami!\n";
    }

}
```

Si tiene experiencia en la creación de API REST, puede adivinar por la return 200 "Bonjour, mon ami!\n";línea que el servidor se ha configurado para responder con un código de estado de 200 y el mensaje "¡Bonjour, mon ami!"

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo validar y recargar archivos de configuración

Después de escribir un nuevo archivo de configuración o actualizar uno antiguo, lo primero que debe hacer es verificar si hay errores de sintaxis en el archivo. El `nginx` binario incluye una opción `-t` para hacer precisamente eso.

```sh
sudo nginx -t

# nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
# nginx: configuration file /etc/nginx/nginx.conf test is successful
```

Si tiene errores de sintaxis, este comando le informará sobre ellos, incluido el número de línea.

Si actualiza el archivo de configuración, deberá indicar a NGINX explícitamente que vuelva a cargar el archivo de configuración. Hay dos maneras de hacerlo.

- Puede reiniciar el servicio NGINX ejecutando el comando:
  ```sh
  sudo systemctl restart nginx
  ```
- Puede enviar una `reload` señal a NGINX ejecutando el comando:

  ```sh
  sudo nginx -s reload
  ```

  La `-s` opción se utiliza para enviar varias señales a NGINX. Las señales disponibles son `stop`, `quity` . Entre las dos formas que acabo de mencionar, prefiero la segunda simplemente porque requiere menos tipeo `reload reopen`

Una vez que haya recargado el archivo de configuración puede verlo en acción enviando una simple solicitud de obtención al servidor:

```sh
curl -i http://nginx-handbook.test

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Wed, 21 Apr 2021 10:03:33 GMT
# Content-Type: text/plain
# Content-Length: 18
# Connection: keep-alive

# Bonjour, mon ami!
```

El servidor responde con un código de estado de 200 y el mensaje esperado.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo entender directivas y contextos en NGINX

Las pocas líneas de código que ha escrito aquí, aunque parecen simples, presentan dos de las terminologías más importantes de los archivos de configuración de NGINX. Son **directivas** y **contextos** .

Técnicamente, todo lo que hay dentro de un archivo de configuración de NGINX es una **directiva** . Las directivas son de dos tipos:

- Directivas simples
- Directivas de bloque

Una _directiva simple_ consiste en el nombre de la directiva y los parámetros delimitados por espacios, como `listen` , `return` y otros. Las directivas simples terminan con punto y coma.

Las _directivas de bloque_ son similares a las directivas simples, excepto que en lugar de terminar con punto y coma, terminan con un par de llaves `{ }` que encierran instrucciones adicionales.

Una directiva de bloque capaz de contener otras directivas en su interior se denomina contexto, es decir `events` , `http` etc. Hay cuatro _contextos_ centrales en NGINX:

- `events { }` – El `events` contexto se usa para establecer la configuración global con respecto a cómo NGINX manejará las solicitudes a nivel general. Solo puede haber un `events` contexto en un archivo de configuración válido.

- `http { }` – Evidente por el nombre, el `http` contexto se usa para definir la configuración con respecto a cómo el servidor manejará las solicitudes HTTP y HTTPS, específicamente. Solo puede haber un `http` contexto en un archivo de configuración válido.

- `server { }` – El `server` contexto está anidado dentro del `http` contexto y se usa para configurar servidores virtuales específicos dentro de un solo host. Puede haber varios `server` contextos en un archivo de configuración válido anidado dentro del `http` contexto. Cada `server` contexto se considera un host virtual.

- `main` – El `main` contexto es el propio archivo de configuración. Cualquier cosa escrita fuera de los tres contextos mencionados anteriormente está en el `main` contexto.

Ya mencioné que puede haber múltiples `server` contextos dentro de un archivo de configuración. Pero cuando una solicitud llega al servidor, ¿cómo sabe NGINX cuál de esos contextos debe manejar la solicitud?

La `listen` directiva es una de las formas de identificar el `server` contexto correcto dentro de una configuración. Considere el siguiente escenario:

```sh
events {

}

http {
    server {
        listen 80;
        server_name nginx-handbook.test;

        return 200 "hello from port 80!\n";
    }


    server {
        listen 8080;
        server_name nginx-handbook.test;

        return 200 "hello from port 8080!\n";
    }
}
```

Ahora, si envía una solicitud a http://nginx-handbook.test:80, recibirá "hola desde el puerto 80". como respuesta. Y si envía una solicitud a http://nginx-handbook.test:8080, recibirá "hola desde el puerto 8080". como respuesta:

```sh
curl nginx-handbook.test:80

# hello from port 80!

curl nginx-handbook.test:8080

# hello from port 8080!
```

Estos dos bloques de servidores son como dos personas que sostienen auriculares telefónicos, esperando responder cuando una solicitud llega a uno de sus números. Sus números están indicados por las `listen` directivas.

Además de la `listen` directiva, también existe la `server_name` directiva. Considere el siguiente escenario de una aplicación de administración de biblioteca imaginaria:

```sh
events {

}

http {
    server {
        listen 80;
        server_name library.test;

        return 200 "your local library!\n";
    }


    server {
        listen 80;
        server_name librarian.library.test;

        return 200 "welcome dear librarian!\n";
    }
}
```

Este es un ejemplo básico de la idea de hosts virtuales. Está ejecutando dos aplicaciones separadas con diferentes nombres de servidor en el mismo servidor.

Para que esta demostración funcione en su sistema, deberá actualizar su `hosts` archivo para incluir también estos dos nombres de dominio:

```sh
192.168.20.20   library.test
192.168.20.20   librarian.library.test
```

Si envía una solicitud a http://library.test, obtendrá "su biblioteca local". como respuesta. Si envía una solicitud a http://librarian.library.test, obtendrá "bienvenido querido bibliotecario". como respuesta.

```sh
curl http://library.test

# your local library!

curl http://librarian.library.test

# welcome dear librarian!
```

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo servir contenido estático usando NGINX

Para servir contenido estático, primero debe almacenarlo en algún lugar de su servidor. Si enumera los archivos y el directorio en la raíz de su servidor usando `ls` , encontrará un directorio llamado `/srv` allí:

```sh
ls -lh /

# lrwxrwxrwx   1 root    root       7 Apr 16 02:10 bin -> usr/bin
# drwxr-xr-x   3 root    root    4.0K Apr 16 02:13 boot
# drwxr-xr-x  16 root    root    3.8K Apr 21 09:23 dev
# drwxr-xr-x  92 root    root    4.0K Apr 21 09:24 etc
# drwxr-xr-x   4 root    root    4.0K Apr 21 08:04 home
# lrwxrwxrwx   1 root    root       7 Apr 16 02:10 lib -> usr/lib
# lrwxrwxrwx   1 root    root       9 Apr 16 02:10 lib32 -> usr/lib32
# lrwxrwxrwx   1 root    root       9 Apr 16 02:10 lib64 -> usr/lib64
# lrwxrwxrwx   1 root    root      10 Apr 16 02:10 libx32 -> usr/libx32
# drwx------   2 root    root     16K Apr 16 02:15 lost+found
# drwxr-xr-x   2 root    root    4.0K Apr 16 02:10 media
# drwxr-xr-x   2 root    root    4.0K Apr 16 02:10 mnt
# drwxr-xr-x   2 root    root    4.0K Apr 16 02:10 opt
# dr-xr-xr-x 152 root    root       0 Apr 21 09:23 proc
# drwx------   5 root    root    4.0K Apr 21 09:59 root
# drwxr-xr-x  26 root    root     820 Apr 21 09:47 run
# lrwxrwxrwx   1 root    root       8 Apr 16 02:10 sbin -> usr/sbin
# drwxr-xr-x   6 root    root    4.0K Apr 16 02:14 snap
# drwxr-xr-x   2 root    root    4.0K Apr 16 02:10 srv
# dr-xr-xr-x  13 root    root       0 Apr 21 09:23 sys
# drwxrwxrwt  11 root    root    4.0K Apr 21 09:24 tmp
# drwxr-xr-x  15 root    root    4.0K Apr 16 02:12 usr
# drwxr-xr-x   1 vagrant vagrant   38 Apr 21 09:23 vagrant
# drwxr-xr-x  14 root    root    4.0K Apr 21 08:34 var
```

Este `/srv` directorio está destinado a contener datos específicos del sitio que son atendidos por este sistema. Ahora `cd` en este directorio y clone el repositorio de código que viene como ejemplo:

```sh
cd /srv

sudo git clone https://github.com/fhsinchy/nginx-handbook-projects.git
```

Dentro del `nginx-handbook-projects` directorio debería haber un directorio llamado `static-demo` que contenga cuatro archivos en total:

```sh
ls -lh /srv/nginx-handbook-projects/static-demo

# -rw-r--r-- 1 root root 960 Apr 21 11:27 about.html
# -rw-r--r-- 1 root root 960 Apr 21 11:27 index.html
# -rw-r--r-- 1 root root 46K Apr 21 11:27 mini.min.css
# -rw-r--r-- 1 root root 19K Apr 21 11:27 the-nginx-handbook.jpg
```

Ahora que tiene el contenido estático para servir, actualice su configuración de la siguiente manera:

```sh
events {

}

http {

    server {

        listen 80;
        server_name nginx-handbook.test;

        root /srv/nginx-handbook-projects/static-demo;
    }

}
```

El código es casi el mismo, excepto que la `return` directiva ahora ha sido reemplazada por una `root` directiva. Esta directiva se utiliza para declarar el directorio raíz de un sitio.

Al escribir `root /srv/nginx-handbook-projects/static-demo` , le está diciendo a NGINX que busque archivos para servir dentro del `/srv/nginx-handbook-projects/static-demo` directorio si llega alguna solicitud a este servidor. Dado que NGINX es un servidor web, es lo suficientemente inteligente como para servir el `index.html` archivo de forma predeterminada.

Veamos si esto funciona o no. Pruebe y vuelva a cargar el archivo de configuración actualizado y visite el servidor [http://nginx-handbook.test](http://nginx-handbook.test) . Debería ser recibido con un sitio HTML algo roto:

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/size/w1600/2021/04/image-91.png" alt="screenshot" />
</div>

Aunque NGINX ha servido correctamente el archivo index.html, a juzgar por el aspecto de los tres enlaces de navegación, parece que el código CSS no funciona.

Puede pensar que hay algo mal en el archivo CSS. Pero en realidad, el problema está en el archivo de configuración.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Manejo de tipos de archivos estáticos en NGINX

Para depurar el problema al que se enfrenta en este momento, envíe una solicitud del archivo CSS al servidor:

```sh
curl -I http://nginx-handbook.test/mini.min.css

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Wed, 21 Apr 2021 12:17:16 GMT
# Content-Type: text/plain
# Content-Length: 46887
# Last-Modified: Wed, 21 Apr 2021 11:27:06 GMT
# Connection: keep-alive
# ETag: "60800c0a-b727"
# Accept-Ranges: bytes
```

Preste atención al **tipo de contenido** y vea cómo dice **text/plain** y no **text/css** . Esto significa que NGINX está sirviendo este archivo como texto sin formato en lugar de como una hoja de estilo.

Aunque NGINX es lo suficientemente inteligente como para encontrar el `index.html` archivo de forma predeterminada, es bastante tonto cuando se trata de interpretar los tipos de archivos. Para resolver este problema, actualice su configuración una vez más:

```sh
events {

}

http {

    types {
        text/html html;
        text/css css;
    }

    server {

        listen 80;
        server_name nginx-handbook.test;

        root /srv/nginx-handbook-projects/static-demo;
    }
}
```

El único cambio que hemos hecho al código es un nuevo `types` contexto anidado dentro del `http` bloque. Como ya habrá adivinado por el nombre, este contexto se utiliza para configurar tipos de archivos.

Al escribir `text/html html` en este contexto, le está diciendo a NGINX que analice cualquier archivo `text/html` que termine con la `html` extensión.

Puede pensar que configurar el tipo de archivo CSS debería ser suficiente, ya que el HTML se analiza correctamente, pero no.

Si introduce un `types` contexto en la configuración, NGINX se vuelve aún más tonto y solo analiza los archivos configurados por usted. Entonces, si solo define `text/css css` en este contexto, NGINX comenzará a analizar el archivo HTML como texto sin formato.

Valide y vuelva a cargar el archivo de configuración recién actualizado y visite el servidor una vez más. Envíe una solicitud para el archivo CSS una vez más, y esta vez el archivo debe analizarse como un archivo de **texto/css** :

```sh
curl -I http://nginx-handbook.test/mini.min.css

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Wed, 21 Apr 2021 12:29:35 GMT
# Content-Type: text/css
# Content-Length: 46887
# Last-Modified: Wed, 21 Apr 2021 11:27:06 GMT
# Connection: keep-alive
# ETag: "60800c0a-b727"
# Accept-Ranges: bytes
```

Visite el servidor para una verificación visual [http://nginx-handbook.test](http://nginx-handbook.test) , y el sitio debería verse mejor esta vez:

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/size/w1600/2021/04/image-92.png" alt="screenshot" />
</div>

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo incluir archivos de configuración parciales

La asignación de tipos de archivos dentro del `types` contexto puede funcionar para proyectos pequeños, pero para proyectos más grandes puede ser engorroso y propenso a errores.

NGINX proporciona una solución para este problema. Si enumera los archivos dentro del `/etc/nginx` directorio una vez más, verá un archivo llamado mime.types.

```sh
ls -lh /etc/nginx

# drwxr-xr-x 2 root root 4.0K Apr 21  2020 conf.d
# -rw-r--r-- 1 root root 1.1K Feb  4  2019 fastcgi.conf
# -rw-r--r-- 1 root root 1007 Feb  4  2019 fastcgi_params
# -rw-r--r-- 1 root root 2.8K Feb  4  2019 koi-utf
# -rw-r--r-- 1 root root 2.2K Feb  4  2019 koi-win
# -rw-r--r-- 1 root root 3.9K Feb  4  2019 mime.types
# drwxr-xr-x 2 root root 4.0K Apr 21  2020 modules-available
# drwxr-xr-x 2 root root 4.0K Apr 17 14:42 modules-enabled
# -rw-r--r-- 1 root root 1.5K Feb  4  2019 nginx.conf
# -rw-r--r-- 1 root root  180 Feb  4  2019 proxy_params
# -rw-r--r-- 1 root root  636 Feb  4  2019 scgi_params
# drwxr-xr-x 2 root root 4.0K Apr 17 14:42 sites-available
# drwxr-xr-x 2 root root 4.0K Apr 17 14:42 sites-enabled
# drwxr-xr-x 2 root root 4.0K Apr 17 14:42 snippets
# -rw-r--r-- 1 root root  664 Feb  4  2019 uwsgi_params
# -rw-r--r-- 1 root root 3.0K Feb  4  2019 win-utf
```

Echemos un vistazo al contenido de este archivo:

```sh
cat /etc/mime.types

# types {
#     text/html                             html htm shtml;
#     text/css                              css;
#     text/xml                              xml;
#     image/gif                             gif;
#     image/jpeg                            jpeg jpg;
#     application/javascript                js;
#     application/atom+xml                  atom;
#     application/rss+xml                   rss;

#     text/mathml                           mml;
#     text/plain                            txt;
#     text/vnd.sun.j2me.app-descriptor      jad;
#     text/vnd.wap.wml                      wml;
#     text/x-component                      htc;

#     image/png                             png;
#     image/tiff                            tif tiff;
#     image/vnd.wap.wbmp                    wbmp;
#     image/x-icon                          ico;
#     image/x-jng                           jng;
#     image/x-ms-bmp                        bmp;
#     image/svg+xml                         svg svgz;
#     image/webp                            webp;

#     application/font-woff                 woff;
#     application/java-archive              jar war ear;
#     application/json                      json;
#     application/mac-binhex40              hqx;
#     application/msword                    doc;
#     application/pdf                       pdf;
#     application/postscript                ps eps ai;
#     application/rtf                       rtf;
#     application/vnd.apple.mpegurl         m3u8;
#     application/vnd.ms-excel              xls;
#     application/vnd.ms-fontobject         eot;
#     application/vnd.ms-powerpoint         ppt;
#     application/vnd.wap.wmlc              wmlc;
#     application/vnd.google-earth.kml+xml  kml;
#     application/vnd.google-earth.kmz      kmz;
#     application/x-7z-compressed           7z;
#     application/x-cocoa                   cco;
#     application/x-java-archive-diff       jardiff;
#     application/x-java-jnlp-file          jnlp;
#     application/x-makeself                run;
#     application/x-perl                    pl pm;
#     application/x-pilot                   prc pdb;
#     application/x-rar-compressed          rar;
#     application/x-redhat-package-manager  rpm;
#     application/x-sea                     sea;
#     application/x-shockwave-flash         swf;
#     application/x-stuffit                 sit;
#     application/x-tcl                     tcl tk;
#     application/x-x509-ca-cert            der pem crt;
#     application/x-xpinstall               xpi;
#     application/xhtml+xml                 xhtml;
#     application/xspf+xml                  xspf;
#     application/zip                       zip;

#     application/octet-stream              bin exe dll;
#     application/octet-stream              deb;
#     application/octet-stream              dmg;
#     application/octet-stream              iso img;
#     application/octet-stream              msi msp msm;

#     application/vnd.openxmlformats-officedocument.wordprocessingml.document    docx;
#     application/vnd.openxmlformats-officedocument.spreadsheetml.sheet          xlsx;
#     application/vnd.openxmlformats-officedocument.presentationml.presentation  pptx;

#     audio/midi                            mid midi kar;
#     audio/mpeg                            mp3;
#     audio/ogg                             ogg;
#     audio/x-m4a                           m4a;
#     audio/x-realaudio                     ra;

#     video/3gpp                            3gpp 3gp;
#     video/mp2t                            ts;
#     video/mp4                             mp4;
#     video/mpeg                            mpeg mpg;
#     video/quicktime                       mov;
#     video/webm                            webm;
#     video/x-flv                           flv;
#     video/x-m4v                           m4v;
#     video/x-mng                           mng;
#     video/x-ms-asf                        asx asf;
#     video/x-ms-wmv                        wmv;
#     video/x-msvideo                       avi;
# }
```

El archivo contiene una larga lista de tipos de archivos y sus extensiones. Para usar este archivo dentro de su archivo de configuración, actualice su configuración para que tenga el siguiente aspecto:

```sh
events {

}

http {

    include /etc/nginx/mime.types;

    server {

        listen 80;
        server_name nginx-handbook.test;

        root /srv/nginx-handbook-projects/static-demo;
    }

}
```

El antiguo `types` contexto ahora ha sido reemplazado por una nueva `include` directiva. Como sugiere el nombre, esta directiva le permite incluir contenido de otros archivos de configuración.

Valide y vuelva a cargar el archivo de configuración y envíe una solicitud para el `mini.min.css` archivo una vez más:

```sh
curl -I http://nginx-handbook.test/mini.min.css

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Wed, 21 Apr 2021 12:29:35 GMT
# Content-Type: text/css
# Content-Length: 46887
# Last-Modified: Wed, 21 Apr 2021 11:27:06 GMT
# Connection: keep-alive
# ETag: "60800c0a-b727"
# Accept-Ranges: bytes
```

Visite el servidor para una verificación visual [http://nginx-handbook.test](http://nginx-handbook.test) :

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/size/w1600/2021/04/image-92.png" alt="screenshot" />
</div>

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Enrutamiento dinámico en NGINX

La configuración que escribió en la sección anterior era una configuración de servidor de contenido estático muy simple. Todo lo que hizo fue hacer coincidir un archivo de la raíz del sitio correspondiente a la URI que visita el cliente y responder.

Entonces, si el cliente solicita archivos existentes en la raíz, como `index.html`, `about.html` o `mini.min.css` NGINX devolverá el archivo. Pero si visita una ruta como http://nginx-handbook.test/nothing, responderá con la página 404 predeterminada:

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/size/w1600/2021/04/image-93.png" width="800"/>
</div>

<br>

En esta sección, aprenderá sobre el `location` contexto, las variables, las redirecciones, las reescrituras y la `try_files` directiva.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Coincidencias de ubicación

El primer concepto que discutiremos en esta sección es el `location` contexto. Actualice la configuración de la siguiente manera:

```sh
events {

}

http {

    server {

        listen 80;
        server_name nginx-handbook.test;

        location /agatha {
            return 200 "Miss Marple.\nHercule Poirot.\n";
        }
    }
}
```

Hemos reemplazado la `root` directiva con un nuevo `location` contexto. Este contexto suele estar anidado dentro de `server` bloques. Puede haber múltiples `location` contextos dentro de un `server` contexto.

Si envía una solicitud a http://nginx-handbook.test/agatha, obtendrá un código de respuesta 200 y una lista de personajes creados por Agatha Christie.

```sh
curl -i http://nginx-handbook.test/agatha

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Wed, 21 Apr 2021 15:59:07 GMT
# Content-Type: text/plain
# Content-Length: 29
# Connection: keep-alive

# Miss Marple.
# Hercule Poirot.
```

Ahora, si envía una solicitud a http://nginx-handbook.test/agatha-christie, obtendrá la misma respuesta:

```sh
curl -i http://nginx-handbook.test/agatha-christie

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Wed, 21 Apr 2021 15:59:07 GMT
# Content-Type: text/plain
# Content-Length: 29
# Connection: keep-alive

# Miss Marple.
# Hercule Poirot.
```

Esto sucede porque, al escribir `location /agatha`, le estás diciendo a NGINX que coincida con cualquier URI que comience con "agatha". Este tipo de coincidencia se denomina **coincidencia de prefijo**.

Para realizar una **coincidencia exacta**, deberá actualizar el código de la siguiente manera:

```sh
events {

}

http {

    server {

        listen 80;
        server_name nginx-handbook.test;

        location = /agatha {
            return 200 "Miss Marple.\nHercule Poirot.\n";
        }
    }

}
```

Agregar un `=` letrero antes del URI de ubicación le indicará a NGINX que responda solo si la URL coincide exactamente. Ahora, si envía una solicitud a algo que no sea `/agatha` , obtendrá una respuesta 404.

```sh
curl -I http://nginx-handbook.test/agatha-christie

# HTTP/1.1 404 Not Found
# Server: nginx/1.18.0 (Ubuntu)
# Date: Wed, 21 Apr 2021 16:14:29 GMT
# Content-Type: text/html
# Content-Length: 162
# Connection: keep-alive

curl -I http://nginx-handbook.test/agatha

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Wed, 21 Apr 2021 16:15:04 GMT
# Content-Type: text/plain
# Content-Length: 29
# Connection: keep-alive
```

Otro tipo de coincidencia en NGINX es la coincidencia de expresiones **regulares**. Al usar esta coincidencia, puede comparar las URL de ubicación con expresiones regulares complejas.

```sh
events {

}

http {

    server {

        listen 80;
        server_name nginx-handbook.test;

        location ~ /agatha[0-9] {
            return 200 "Miss Marple.\nHercule Poirot.\n";
        }
    }

}
```

Al reemplazar el `=` signo utilizado anteriormente con un `~` signo, le está diciendo a NGINX que realice una coincidencia de expresión regular. Establecer la ubicación en `~ /agatha[0-9]` significa que NIGINX solo responderá si hay un número después de la palabra "agatha":

```sh
curl -I http://nginx-handbook.test/agatha

# HTTP/1.1 404 Not Found
# Server: nginx/1.18.0 (Ubuntu)
# Date: Wed, 21 Apr 2021 16:14:29 GMT
# Content-Type: text/html
# Content-Length: 162
# Connection: keep-alive

curl -I http://nginx-handbook.test/agatha8

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Wed, 21 Apr 2021 16:15:04 GMT
# Content-Type: text/plain
# Content-Length: 29
# Connection: keep-alive
```

Una coincidencia de expresiones regulares distingue entre mayúsculas y minúsculas de forma predeterminada, lo que significa que si escribe en mayúscula cualquiera de las letras, la ubicación no funcionará:

```sh
curl -I http://nginx-handbook.test/Agatha8

# HTTP/1.1 404 Not Found
# Server: nginx/1.18.0 (Ubuntu)
# Date: Wed, 21 Apr 2021 16:14:29 GMT
# Content-Type: text/html
# Content-Length: 162
# Connection: keep-alive
```

Para convertir esto en mayúsculas y minúsculas, deberá agregar un `*` después del `~` signo.

```sh
events {

}

http {

    server {

        listen 80;
        server_name nginx-handbook.test;

        location ~* /agatha[0-9] {
            return 200 "Miss Marple.\nHercule Poirot.\n";
        }
    }

}
```

Eso le indicará a NGINX que suelte la sensibilidad de tipo y haga coincidir la ubicación de todos modos.

```sh
curl -I http://nginx-handbook.test/agatha8

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Wed, 21 Apr 2021 16:15:04 GMT
# Content-Type: text/plain
# Content-Length: 29
# Connection: keep-alive

curl -I http://nginx-handbook.test/Agatha8

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Wed, 21 Apr 2021 16:15:04 GMT
# Content-Type: text/plain
# Content-Length: 29
# Connection: keep-alive

```

NGINX asigna valores de prioridad a estas coincidencias, y una coincidencia de expresiones regulares tiene más prioridad que una coincidencia de prefijo.

```sh
events {

}

http {

    server {

        listen 80;
        server_name nginx-handbook.test;

        location /Agatha8 {
            return 200 "prefix matched.\n";
        }

        location ~* /agatha[0-9] {
            return 200 "regex matched.\n";
        }
    }

}
```

Ahora, si envía una solicitud a http://nginx-handbook.test/Agatha8, obtendrá la siguiente respuesta:

```sh
curl -i http://nginx-handbook.test/Agatha8

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Thu, 22 Apr 2021 08:08:18 GMT
# Content-Type: text/plain
# Content-Length: 15
# Connection: keep-alive

# regex matched.
```

Pero esta prioridad se puede cambiar un poco. El último tipo de coincidencia en NGINX es una **coincidencia de prefijo preferencial**. Para convertir una coincidencia de prefijo en preferencial, debe incluir el `^~` modificador antes del URI de ubicación:

```sh
events {

}

http {

    server {

        listen 80;
        server_name nginx-handbook.test;

        location ^~ /Agatha8 {
            return 200 "prefix matched.\n";
        }

        location ~* /agatha[0-9] {
            return 200 "regex matched.\n";
        }
    }

}
```

Ahora, si envía una solicitud a http://nginx-handbook.test/Agatha8, obtendrá la siguiente respuesta:

```sh
curl -i http://nginx-handbook.test/Agatha8

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Thu, 22 Apr 2021 08:13:24 GMT
# Content-Type: text/plain
# Content-Length: 16
# Connection: keep-alive

# prefix matched.
```

Esta vez, gana la coincidencia de prefijo. Entonces, la lista de todas las coincidencias en orden descendente de prioridad es la siguiente:

<div align="center">

| JUEGO                | MODIFICADOR |
| -------------------- | ----------- |
| Exacto               | `=`         |
| Prefijo preferencial | `^~`        |
| REGEX                | `~` o `~*`  |
| Prefijo              | `None`      |

</div>

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Variables en NGINX

Las variables en NGINX son similares a las variables en otros lenguajes de programación. La `set` directiva se puede usar para declarar nuevas variables en cualquier lugar dentro del archivo de configuración:

```sh
set $<variable_name> <variable_value>;

# set name "Farhan"
# set age 25
# set is_working true
```

Las variables pueden ser de tres tipos.

- Cuerda
- Entero
- booleano

Además de las variables que declara, existen variables integradas dentro de los módulos NGINX. Un índice alfabético de variables está disponible en la documentación oficial.

Para ver algunas de las variables en acción, actualice la configuración de la siguiente manera:

```sh
events {

}

http {

    server {

        listen 80;
        server_name nginx-handbook.test;

        return 200 "Host - $host\nURI - $uri\nArgs - $args\n";
    }

}
```

Ahora, al enviar una solicitud al servidor, debe obtener una respuesta de la siguiente manera:

```sh
# curl http://nginx-handbook.test/user?name=Farhan

# Host - nginx-handbook.test
# URI - /user
# Args - name=Farhan
```

Como puede ver, las variables `$host` y `$uri` contienen la dirección raíz y el URI solicitado en relación con la raíz, respectivamente. La `$args` variable, como puede ver, contiene todas las cadenas de consulta.

En lugar de imprimir la forma de cadena literal de las cadenas de consulta, puede acceder a los valores individuales utilizando la `$arg` variable.

```sh
events {

}

http {

    server {

        listen 80;
        server_name nginx-handbook.test;

        set $name $arg_name; # $arg_<query string name>

        return 200 "Name - $name\n";
    }

}
```

Ahora la respuesta del servidor debería verse así:

```sh
curl http://nginx-handbook.test?name=Farhan

# Name - Farhan
```

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Redirecciones y reescrituras

Una redirección en NGINX es igual que las redirecciones en cualquier otra plataforma. Para demostrar cómo funcionan los redireccionamientos, actualice su configuración para que se vea así:

```sh
events {

}

http {

    include /etc/nginx/mime.types;

    server {

        listen 80;
        server_name nginx-handbook.test;

        root /srv/nginx-handbook-projects/static-demo;

        location = /index_page {
            return 307 /index.html;
        }

        location = /about_page {
            return 307 /about.html;
        }
    }
}
```

Ahora, si envía una solicitud a http://nginx-handbook.test/about_page, será redirigido a http://nginx-handbook.test/about.html:

```sh
curl -I http://nginx-handbook.test/about_page

# HTTP/1.1 307 Temporary Redirect
# Server: nginx/1.18.0 (Ubuntu)
# Date: Thu, 22 Apr 2021 18:02:04 GMT
# Content-Type: text/html
# Content-Length: 180
# Location: http://nginx-handbook.test/about.html
# Connection: keep-alive
```

Como puede ver, el servidor respondió con un código de estado de 307 y la ubicación indica http://nginx-handbook.test/about.html. Si visita http://nginx-handbook.test/about_page desde un navegador, verá que la URL cambiará automáticamente a http://nginx-handbook.test/about.html.

Una `rewrite` directiva, sin embargo, funciona un poco diferente. Cambia la URI internamente, sin avisar al usuario. Para verlo en acción, actualice su configuración de la siguiente manera:

```sh
events {

}

http {

    include /etc/nginx/mime.types;

    server {

        listen 80;
        server_name nginx-handbook.test;

        root /srv/nginx-handbook-projects/static-demo;

        rewrite /index_page /index.html;

        rewrite /about_page /about.html;
    }
}
```

Ahora, si envía una solicitud a http://nginx-handbook.test/about_page URI, obtendrá un código de respuesta 200 y el código HTML para el archivo about.html en respuesta:

```sh
curl -i http://nginx-handbook.test/about_page

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Thu, 22 Apr 2021 18:09:31 GMT
# Content-Type: text/html
# Content-Length: 960
# Last-Modified: Wed, 21 Apr 2021 11:27:06 GMT
# Connection: keep-alive
# ETag: "60800c0a-3c0"
# Accept-Ranges: bytes

# <!DOCTYPE html>
# <html lang="en">
# <head>
#     <meta charset="UTF-8">
#     <meta http-equiv="X-UA-Compatible" content="IE=edge">
#     <meta name="viewport" content="width=device-width, initial-scale=1.0">
#     <title>NGINX Handbook Static Demo</title>
#     <link rel="stylesheet" href="mini.min.css">
#     <style>
#         .container {
#             max-width: 1024px;
#             margin-left: auto;
#             margin-right: auto;
#         }
#
#         h1 {
#             text-align: center;
#         }
#     </style>
# </head>
# <body class="container">
#     <header>
#         <a class="button" href="index.html">Index</a>
#         <a class="button" href="about.html">About</a>
#         <a class="button" href="nothing">Nothing</a>
#     </header>
#     <div class="card fluid">
#         <img src="./the-nginx-handbook.jpg" alt="The NGINX Handbook Cover Image">
#     </div>
#     <div class="card fluid">
#         <h1>this is the <strong>about.html</strong> file</h1>
#     </div>
# </body>
# </html>
```

Y si visita la URI usando un navegador, verá la página about.html mientras que la URL permanece sin cambios:

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/2021/04/rewrite.png" alt="screenshot" />
</div>

Además de la forma en que se maneja el cambio de URI, hay otra diferencia entre una redirección y una reescritura. Cuando ocurre una reescritura, `server` NGINX vuelve a evaluar el contexto. Entonces, una reescritura es una operación más costosa que una redirección.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo probar varios archivos

El concepto final que mostraré en esta sección es la `try_files` directiva. En lugar de responder con un solo archivo, la `try_files` directiva le permite comprobar la existencia de varios archivos.

```sh
events {

}

http {

    include /etc/nginx/mime.types;

    server {

        listen 80;
        server_name nginx-handbook.test;

        root /srv/nginx-handbook-projects/static-demo;

        try_files /the-nginx-handbook.jpg /not_found;

        location /not_found {
            return 404 "sadly, you've hit a brick wall buddy!\n";
        }
    }
}
```

Como puede ver, `try_files` se ha agregado una nueva directiva. Al escribir `try_files /the-nginx-handbook.jpg /not_found;` , le indica a NGINX que busque un archivo llamado the-nginx-handbook.jpg en la raíz cada vez que se recibe una solicitud. Si no existe, vaya a la `/not_found` ubicación.

Ahora, si visitas el servidor, verás la imagen:

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/size/w1600/2021/04/image-94.png" alt="screenshot" />
</div>

<br>

Pero si actualiza la configuración para intentar con un archivo inexistente como blackhole.jpg, obtendrá una respuesta 404 con el mensaje "sadly, you've hit a brick wall buddy!".

Ahora, el problema de escribir una `try_files` directiva de esta manera es que no importa qué URL visite (http://nginx-handbook.test/nothing), siempre que el servidor reciba una solicitud y el archivo the-nginx-handbook.jpg se encuentre en el disco, NGINX lo devolverá.

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/2021/04/try-files.png" alt="screenshot" />
</div>

<br>

Y es por eso `try_files` que a menudo se usa con la `$uri` variable NGINX.

```sh
events {

}

http {

    include /etc/nginx/mime.types;

    server {

        listen 80;
        server_name nginx-handbook.test;

        root /srv/nginx-handbook-projects/static-demo;

        try_files $uri /not_found;

        location /not_found {
            return 404 "sadly, you've hit a brick wall buddy!\n";
        }
    }
}
```

Al escribir `try_files $uri /not_found;` , le está indicando a NGINX que primero intente obtener el URI solicitado por el cliente. Si no encuentra ese, intente con el siguiente.

Entonces, si visita http://nginx-handbook.test/index.html, debería obtener la página index.html anterior. Lo mismo ocurre con la página about.html:

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/size/w1600/2021/04/image-95.png" alt="screenshot" />
</div>

<br>

Pero si solicita un archivo que no existe, obtendrá la respuesta de la` /not_found` ubicación:

```sh
curl -i http://nginx-handbook.test/nothing

# HTTP/1.1 404 Not Found
# Server: nginx/1.18.0 (Ubuntu)
# Date: Thu, 22 Apr 2021 20:01:57 GMT
# Content-Type: text/plain
# Content-Length: 38
# Connection: keep-alive

# sadly, you've hit a brick wall buddy!
```

Una cosa que quizás ya haya notado es que si visita la raíz del servidor http://nginx-handbook.test, obtiene la respuesta 404.

Esto se debe a que cuando accede a la raíz del servidor, la `$uri` variable no corresponde a ningún archivo existente, por lo que NGINX le proporciona la ubicación alternativa. Si desea solucionar este problema, actualice su configuración de la siguiente manera:

```sh
events {

}

http {

    include /etc/nginx/mime.types;

    server {

        listen 80;
        server_name nginx-handbook.test;

        root /srv/nginx-handbook-projects/static-demo;

        try_files $uri $uri/ /not_found;

        location /not_found {
            return 404 "sadly, you've hit a brick wall buddy!\n";
        }
    }
}
```

Al escribir `try_files $uri $uri/ /not_found;` , le indica a NGINX que primero intente obtener el URI solicitado. Si eso no funciona, intente con el URI solicitado como un directorio, y cada vez que NGINX termina en un directorio, automáticamente comienza a buscar un archivo index.html.

Ahora, si visita el servidor, debería obtener el archivo index.html correctamente:

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/size/w1600/2021/04/image-95.png" alt="screenshot" />
</div>

El `try_files` es el tipo de directiva que se puede utilizar en una serie de variaciones. En las próximas secciones, encontrará algunas otras variaciones, pero le sugiero que investigue un poco en Internet sobre los diferentes usos de esta directiva por su cuenta.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Iniciar sesión en NGINX

De forma predeterminada, los archivos de registro de NGINX se encuentran dentro de `/var/log/nginx` . Si enumera el contenido de este directorio, puede ver algo como lo siguiente:

```sh
ls -lh /var/log/nginx/

# -rw-r----- 1 www-data adm     0 Apr 25 07:34 access.log
# -rw-r----- 1 www-data adm     0 Apr 25 07:34 error.log
```

Comencemos por vaciar los dos archivos.

```sh
# delete the old files
sudo rm /var/log/nginx/access.log /var/log/nginx/error.log

# create new files
sudo touch /var/log/nginx/access.log /var/log/nginx/error.log

# reopen the log files
sudo nginx -s reopen
```

Si no envía una `reopen` señal a NGINX, seguirá escribiendo registros en los flujos abiertos anteriormente y los nuevos archivos permanecerán vacíos.

Ahora, para realizar una entrada en el registro de acceso, envíe una solicitud al servidor.

```sh
curl -I http://nginx-handbook.test

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Sun, 25 Apr 2021 08:35:59 GMT
# Content-Type: text/html
# Content-Length: 960
# Last-Modified: Sun, 25 Apr 2021 08:35:33 GMT
# Connection: keep-alive
# ETag: "608529d5-3c0"
# Accept-Ranges: bytes

sudo cat /var/log/nginx/access.log

# 192.168.20.20 - - [25/Apr/2021:08:35:59 +0000] "HEAD / HTTP/1.1" 200 0 "-" "curl/7.68.0"
```

Como puede ver, se ha agregado una nueva entrada al archivo access.log. Cualquier solicitud al servidor se registrará en este archivo de forma predeterminada. Pero podemos cambiar este comportamiento usando la `access_log` directiva.

```sh
events {

}

http {

    include /etc/nginx/mime.types;

    server {

        listen 80;
        server_name nginx-handbook.test;

        location / {
            return 200 "this will be logged to the default file.\n";
        }

        location = /admin {
            access_log /var/log/nginx/admin.log;

            return 200 "this will be logged in a separate file.\n";
        }

        location = /no_logging {
            access_log off;

            return 200 "this will not be logged.\n";
        }
    }
}
```

La primera `access_log` directiva dentro del bloque de ubicación /admin le indica a NGINX que escriba cualquier registro de acceso de este URI en el `/var/log/nginx/admin.log` archivo. El segundo dentro de la ubicación /no_logging desactiva completamente los registros de acceso para esta ubicación.

Comencemos por vaciar los archivos y crearlos.

```sh
# delete the old files
sudo rm /var/log/nginx/access.log /var/log/nginx/error.log

# create new files
sudo touch /var/log/nginx/access.log /var/log/nginx/error.log /var/log/nginx/admin.log

# reopen the log files
sudo nginx -s reopen
```

Valide y vuelva a cargar la configuración. Ahora, si envía solicitudes a estas ubicaciones e inspecciona los archivos de registro, debería ver algo como esto:

```sh
curl http://nginx-handbook.test/no_logging
# this will not be logged

sudo cat /var/log/nginx/access.log
# empty

curl http://nginx-handbook.test/admin
# this will be logged in a separate file.

sudo cat /var/log/nginx/access.log
# empty

sudo cat /var/log/nginx/admin.log
# 192.168.20.20 - - [25/Apr/2021:11:13:53 +0000] "GET /admin HTTP/1.1" 200 40 "-" "curl/7.68.0"

curl  http://nginx-handbook.test/
# this will be logged to the default file.

sudo cat /var/log/nginx/access.log
# 192.168.20.20 - - [25/Apr/2021:11:15:14 +0000] "GET / HTTP/1.1" 200 41 "-" "curl/7.68.0"
```

El archivo error.log, por otro lado, contiene los registros de errores. Para realizar una entrada en error.log, deberá hacer que NGINX se bloquee. Para hacerlo, actualice su configuración de la siguiente manera:

```sh
events {

}

http {

    include /etc/nginx/mime.types;

    server {

        listen 80;
        server_name nginx-handbook.test;

        return 200 "..." "...";
    }

}
```

Como sabe, la `return` directiva solo toma dos parámetros, pero aquí hemos dado tres. Ahora intente volver a cargar la configuración y aparecerá un mensaje de error:

```sh
sudo nginx -s reload

# nginx: [emerg] invalid number of arguments in "return" directive in /etc/nginx/nginx.conf:14
```

Verifique el contenido del registro de errores y el mensaje también debería estar presente allí:

```sh
sudo cat /var/log/nginx/error.log

# 2021/04/25 08:35:45 [notice] 4169#4169: signal process started
# 2021/04/25 10:03:18 [emerg] 8434#8434: invalid number of arguments in "return" directive in /etc/nginx/nginx.conf:14
```

Los mensajes de error tienen niveles. Una `notice` entrada en el registro de errores es inofensiva, pero una `emerg` entrada de emergencia debe abordarse de inmediato.

Hay ocho niveles de mensajes de error:

- `debug` – Información de depuración útil para ayudar a determinar dónde radica el problema.
- `info`– Mensajes informativos que no es necesario leer pero que puede ser bueno saber.
- `notice`– Pasó algo normal que vale la pena señalar.
- `warn`– Algo inesperado sucedió, sin embargo, no es motivo de preocupación.
- `error`– Algo no tuvo éxito.
- `crit` – Hay problemas que necesitan ser abordados críticamente.
- `alert` – Se requiere una acción inmediata.
- `emerg` – El sistema está en un estado inutilizable y requiere atención inmediata.

De forma predeterminada, NGINX registra todos los niveles de mensajes. Puede anular este comportamiento utilizando la `error_log` directiva. Si desea establecer el nivel mínimo de un mensaje para que sea `warn` , actualice su archivo de configuración de la siguiente manera:

```sh
events {

}

http {

    include /etc/nginx/mime.types;

    server {

        listen 80;
        server_name nginx-handbook.test;

    	error_log /var/log/error.log warn;

        return 200 "..." "...";
    }

}
```

`warn` Valide y vuelva a cargar la configuración, y de ahora en adelante solo se registrarán los mensajes con un nivel de o superior.

```sh
cat /var/log/nginx/error.log

# 2021/04/25 11:27:02 [emerg] 12769#12769: invalid number of arguments in "return" directive in /etc/nginx/nginx.conf:16
```

A diferencia de la salida anterior, aquí no hay `notice` entradas. `emerg` es un error de mayor nivel que `warn` y por eso se ha registrado.

Para la mayoría de los proyectos, dejar la configuración de error como está debería estar bien. La única sugerencia que tengo es establecer el nivel mínimo de error en `warn` . De esta forma, no tendrá que buscar entradas innecesarias en el registro de errores.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo usar NGINX como proxy inverso

Cuando se configura como un proxy inverso, NGINX se ubica entre el cliente y un servidor back-end. El cliente envía solicitudes a NGINX, luego NGINX pasa la solicitud al back-end.

Una vez que el servidor back-end termina de procesar la solicitud, la envía de vuelta a NGINX. A su vez, NGINX devuelve la respuesta al cliente.

Durante todo el proceso, el cliente no tiene idea de quién está procesando realmente la solicitud. Suena complicado por escrito, pero una vez que lo haga usted mismo, verá lo fácil que lo hace NGINX.

Veamos un ejemplo muy básico y poco práctico de proxy inverso:

```sh
events {

}

http {

    include /etc/nginx/mime.types;

    server {
        listen 80;
        server_name nginx.test;

        location / {
            proxy_pass "http://nginx.org/";
        }
    }
}
```

Además de validar y volver a cargar la configuración, también deberá agregar esta dirección a su `hosts` archivo para que esta demostración funcione en su sistema:

```sh
192.168.20.20   nginx.test
```

Ahora, si visita http://nginx.test, será recibido por el sitio original http://nginx.org mientras que el URI permanece sin cambios.

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/size/w1600/2021/04/nginx-org-proxy.png" alt="screenshot" />
</div>

Incluso debería poder navegar por el sitio hasta cierto punto. Si visita http://nginx.test/en/docs/, debería obtener la página http://nginx.org/en/docs/ como respuesta.

Entonces, como puede ver, en un nivel básico, la `proxy_pass` directiva simplemente pasa la solicitud de un cliente a un servidor de terceros y revierte la respuesta al cliente.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Node con NGINX

Ahora que sabe cómo configurar un servidor proxy inverso básico, puede servir una aplicación Node.js con proxy inverso mediante NGINX. He agregado una aplicación de demostración dentro del repositorio que viene con este artículo.

Si ya ha clonado el repositorio interno /`srv/nginx-handbook-projects` , el node-js-demoproyecto debería estar disponible en el `/srv/nginx-handbook-projects/node-js-demo` directorio.

La aplicación de demostración es un servidor HTTP simple que responde con un código de estado 200 y una carga JSON. Puede iniciar la aplicación simplemente ejecutándola `node app.js` , pero una mejor manera es usar PM2.

Instale PM2 globalmente ejecutando `sudo npm install -g pm2` . Una vez completada la instalación, ejecute el siguiente comando mientras se encuentra dentro del `/srv/nginx-handbook-projects/node-js-demo` directorio:

```sh
pm2 start app.js

# [PM2] Process successfully started
# ┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
# │ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
# ├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
# │ 0  │ app                │ fork     │ 0    │ online    │ 0%       │ 21.2mb   │
# └────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
```

La aplicación debería estar ejecutándose ahora, pero no debería ser accesible desde fuera del servidor. Para verificar si la aplicación se está ejecutando o no, envíe una solicitud de obtención a http://localhost:3000 desde el interior de su servidor:

```sh
curl -i localhost:3000

# HTTP/1.1 200 OK
# X-Powered-By: Express
# Content-Type: application/json; charset=utf-8
# Content-Length: 62
# ETag: W/"3e-XRN25R5fWNH2Tc8FhtUcX+RZFFo"
# Date: Sat, 24 Apr 2021 12:09:55 GMT
# Connection: keep-alive
# Keep-Alive: timeout=5

# { "status": "success", "message": "You're reading The NGINX Handbook!" }
```

Si obtiene una respuesta de 200, entonces el servidor está funcionando bien. Ahora, para configurar NGINX como proxy inverso, abra su archivo de configuración y actualice su contenido de la siguiente manera:

```sh
events {

}

http {

    server {

        listen 80;
        server_name nginx-handbook.test;

        location / {
            proxy_pass http://localhost:3000;
        }
    }
}
```

Nada nuevo que explicar aquí. Simplemente está pasando la solicitud recibida a la aplicación Node.js que se ejecuta en el puerto 3000. Ahora, si envía una solicitud al servidor desde el exterior, debería obtener una respuesta de la siguiente manera:

```sh
curl -i http://nginx-handbook.test

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Sat, 24 Apr 2021 14:58:01 GMT
# Content-Type: application/json
# Transfer-Encoding: chunked
# Connection: keep-alive

# { "status": "success", "message": "You're reading The NGINX Handbook!" }
```

Aunque esto funciona para un servidor básico como este, es posible que deba agregar algunas directivas más para que funcione en un escenario del mundo real según los requisitos de su aplicación.

Por ejemplo, si su aplicación maneja conexiones de socket web, debe actualizar la configuración de la siguiente manera:

```sh
events {

}

http {

    server {

        listen 80;
            server_name nginx-handbook.test;

            location / {
                proxy_pass http://localhost:3000;
                proxy_http_version 1.1;
                proxy_set_header Upgrade $http_upgrade;
                proxy_set_header Connection 'upgrade';
            }
    }

}
```

La `proxy_http_version` directiva establece la versión HTTP para el servidor. Por defecto es 1.0, pero web socket requiere que sea al menos 1.1. La `proxy_set_header` directiva se utiliza para establecer un encabezado en el servidor de fondo. La sintaxis genérica para esta directiva es la siguiente:

```sh
proxy_set_header <header name> <header value>
```

Entonces, al escribir `proxy_set_header Upgrade $http_upgrade;` , le está indicando a NGINX que pase el valor de la `$http_upgrade` variable como un encabezado con nombre `Upgrade` , lo mismo para el `Connection` encabezado.

Si desea obtener más información sobre el proxy de socket web, este enlace (https://nginx.org/en/docs/http/websocket.html) a los documentos oficiales de NGINX puede ser de ayuda.

Dependiendo de los encabezados requeridos por su aplicación, es posible que deba establecer más de ellos. Pero la configuración mencionada anteriormente se usa muy comúnmente para servir aplicaciones Node.js.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### PHP con NGINX

PHP y NGINX van juntos como el pan y la mantequilla. Después de todo, la E y la P en la pila LEMP representan NGINX y PHP.

Ya he incluido una aplicación PHP de demostración en el repositorio que viene con este artículo. Si ya lo ha clonado en el `/srv/nginx-handbook-projects` directorio, entonces la aplicación debería estar dentro de `/srv/nginx-handbook-projects/php-demo` .

Para que esta demostración funcione, deberá instalar un paquete llamado PHP-FPM. Para instalar el paquete, puede ejecutar el siguiente comando:

```sh
sudo apt install php-fpm -y
```

Para probar la aplicación, inicie un servidor PHP ejecutando el siguiente comando dentro del `/srv/nginx-handbook-projects/php-demo` directorio:

```sh
php -S localhost:8000

# [Sat Apr 24 16:17:36 2021] PHP 7.4.3 Development Server (http://localhost:8000) started
```

La aplicación debe ejecutarse en el puerto 8000, pero no se puede acceder a ella desde el exterior del servidor. Para verificar, envíe una solicitud de obtención a http://localhost:8000 desde dentro de su servidor:

```sh
curl -I localhost:8000

# HTTP/1.1 200 OK
# Host: localhost:8000
# Date: Sat, 24 Apr 2021 16:22:42 GMT
# Connection: close
# X-Powered-By: PHP/7.4.3
# Content-type: application/json

# {"status":"success","message":"You're reading The NGINX Handbook!"}
```

Si obtiene una respuesta de 200, entonces el servidor está funcionando bien. Al igual que la configuración de Node.js, ahora puede simplemente `proxy_pass` enviar solicitudes a localhost: 8000, pero con PHP, hay una mejor manera.

La parte `FPM` en `PHP-FPM` **significa Módulo de proceso FastCGI. FastCGI es un protocolo como HTTP para intercambiar datos binarios**. Este protocolo es un poco más rápido que HTTP y brinda mayor seguridad.

Para usar FastCGI en lugar de HTTP, actualice su configuración de la siguiente manera:

```sh
events {

}

http {

      include /etc/nginx/mime.types;

      server {

          listen 80;
          server_name nginx-handbook.test;
          root /srv/nginx-handbook-projects/php-demo;

          index index.php;

          location / {
              try_files $uri $uri/ =404;
          }

          location ~ \.php$ {
              fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
              fastcgi_param REQUEST_METHOD $request_method;
              fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
      }
   }
}
```

Comencemos con la nueva `index` directiva. Como sabe, NGINX por defecto busca un archivo index.html para servir. Pero en el proyecto de demostración, se llama index.php. Entonces, al escribir `index index.php` , le está indicando a NGINX que use el archivo index.php como root en su lugar.

Esta directiva puede aceptar múltiples parámetros. Si escribe algo como `index index.php index.html` , NGINX primero buscará index.php. Si no encuentra ese archivo, buscará un archivo index.html.

La `try_files` directiva dentro del primer `location` contexto es la misma que ha visto en una sección anterior. El `=404` al final indica el error a lanzar si no se encuentra ninguno de los archivos.

El segundo `location` bloque es el lugar donde ocurre la magia principal. Como puede ver, hemos reemplazado la `proxy_pass` directiva por una nueva `fastcgi_pass` . Como sugiere el nombre, se utiliza para pasar una solicitud a un servicio FastCGI.

El servicio `PHP-FPM` por defecto se ejecuta en el puerto 9000 del host. Entonces, en lugar de usar un socket de Unix como lo hice aquí, puede pasar la solicitud` http://localhost:9000` directamente. Pero usar un socket Unix es más seguro.

Si tiene varias versiones de PHP-FPM instaladas, simplemente puede enumerar todas las ubicaciones de los archivos de socket ejecutando el siguiente comando

```sh
sudo find / -name *fpm.sock

# /run/php/php7.4-fpm.sock
# /run/php/php-fpm.sock
# /etc/alternatives/php-fpm.sock
# /var/lib/dpkg/alternatives/php-fpm.sock
```

El `/run/php/php-fpm.sock` archivo hace referencia a la última versión de PHP-FPM instalada en su sistema. _Prefiero usar el que tiene el número de versión_. De esta manera, incluso si PHP-FPM se actualiza, estaré seguro de la versión que estoy usando.

A diferencia de pasar solicitudes a través de HTTP, pasar solicitudes a través de FPM requiere que pasemos información adicional.

La forma general de pasar información extra al servicio FPM es usando la `fastcgi_param` directiva. Como mínimo, deberá pasar el método de solicitud y el nombre del script al servicio de back-end para que funcione el proxy.

El `fastcgi_param REQUEST_METHOD $request_method;` pasa el método de solicitud al back-end y la `fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;` línea pasa la ubicación exacta del script PHP para ejecutar.

En este estado, su configuración debería funcionar. Para probarlo, visite su servidor (http://nginx-handbook.test/) y debería recibir algo como esto:

<br>
<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/size/w1600/2021/04/500-on-fastcgi.png" width="800"/>
</div>
<br>

Bueno, eso es raro. Un error 502 significa que NGINX se ha bloqueado por algún motivo. Aquí es donde los registros de errores pueden resultar útiles. Echemos un vistazo a la última entrada en el archivo error.log:

```sh
tail -n 1 /var/log/nginx/error.log

# 2021/04/24 17:15:17 [crit] 17691#17691: *21 connect() to unix:/var/run/php/php7.4-fpm.sock failed (13: Permission denied) while connecting to upstream, client: 192.168.20.20, server: nginx-handbook.test, request: "GET / HTTP/1.1", upstream: "fastcgi://unix:/var/run/php/php7.4-fpm.sock:", host: "nginx-handbook.test"
```

Parece que al proceso NGINX se le niega el permiso para acceder al proceso PHP-FPM.

Una de las principales razones para obtener un error de permiso denegado es la falta de coincidencia del usuario. Eche un vistazo al usuario que posee el proceso de trabajo de NGINX.

```sh
ps aux | grep nginx

# root         677  0.0  0.4   8892  4260 ?        Ss   14:31   0:00 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
# nobody     17691  0.0  0.3   9328  3452 ?        S    17:09   0:00 nginx: worker process
# vagrant    18224  0.0  0.2   8160  2552 pts/0    S+   17:19   0:00 grep --color=auto nginx
```

Como puede ver, el proceso actualmente es propiedad de nobody. Ahora inspeccione el proceso PHP-FPM.

```sh
ps aux | grep php

# root       14354  0.0  1.8 195484 18924 ?        Ss   16:11   0:00 php-fpm: master process (/etc/php/7.4/fpm/php-fpm.conf)
# www-data   14355  0.0  0.6 195872  6612 ?        S    16:11   0:00 php-fpm: pool www
# www-data   14356  0.0  0.6 195872  6612 ?        S    16:11   0:00 php-fpm: pool www
# vagrant    18296  0.0  0.0   8160   664 pts/0    S+   17:20   0:00 grep --color=auto php
```

Este proceso, por otro lado, es propiedad del `www-data` usuario. Es por eso que a NGINX se le niega el acceso a este proceso.

Para resolver este problema, actualice su configuración de la siguiente manera:

```sh
user www-data;

events {

}

http {

      include /etc/nginx/mime.types;

      server {

          listen 80;
          server_name nginx-handbook.test;
          root /srv/nginx-handbook-projects/php-demo;

          index index.php;

          location / {
              try_files $uri $uri/ =404;
          }

          location ~ \.php$ {
              fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
              fastcgi_param REQUEST_METHOD $request_method;
              fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
      }
   }
}
```

La `user` directiva es responsable de establecer el propietario de los procesos de trabajo de NGINX. Ahora inspeccione el proceso NGINX una vez más:

```sh
ps aux | grep nginx

# root         677  0.0  0.4   8892  4264 ?        Ss   14:31   0:00 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
# www-data   20892  0.0  0.3   9292  3504 ?        S    18:10   0:00 nginx: worker process
# vagrant    21294  0.0  0.2   8160  2568 pts/0    S+   18:18   0:00 grep --color=auto nginx
```

Sin duda, el proceso ahora es propiedad del `www-data` usuario. Envía una solicitud a tu servidor para comprobar si funciona o no:

```sh
curl -i http://nginx-handbook.test

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Sat, 24 Apr 2021 18:22:24 GMT
# Content-Type: application/json
# Transfer-Encoding: chunked
# Connection: keep-alive

# {"status":"success","message":"You're reading The NGINX Handbook!"}
```

Si obtiene un código de estado 200 con una carga JSON, está listo para comenzar.

Esta configuración simple está bien para la aplicación de demostración, pero en proyectos de la vida real tendrá que pasar algunos parámetros adicionales.

Por esta razón, NGINX incluye una configuración parcial llamada `fastcgi_params` . Este archivo contiene una lista de los parámetros FastCGI más comunes.

```sh
cat /etc/nginx/fastcgi_params

# fastcgi_param  QUERY_STRING       $query_string;
# fastcgi_param  REQUEST_METHOD     $request_method;
# fastcgi_param  CONTENT_TYPE       $content_type;
# fastcgi_param  CONTENT_LENGTH     $content_length;

# fastcgi_param  SCRIPT_NAME        $fastcgi_script_name;
# fastcgi_param  REQUEST_URI        $request_uri;
# fastcgi_param  DOCUMENT_URI       $document_uri;
# fastcgi_param  DOCUMENT_ROOT      $document_root;
# fastcgi_param  SERVER_PROTOCOL    $server_protocol;
# fastcgi_param  REQUEST_SCHEME     $scheme;
# fastcgi_param  HTTPS              $https if_not_empty;

# fastcgi_param  GATEWAY_INTERFACE  CGI/1.1;
# fastcgi_param  SERVER_SOFTWARE    nginx/$nginx_version;

# fastcgi_param  REMOTE_ADDR        $remote_addr;
# fastcgi_param  REMOTE_PORT        $remote_port;
# fastcgi_param  SERVER_ADDR        $server_addr;
# fastcgi_param  SERVER_PORT        $server_port;
# fastcgi_param  SERVER_NAME        $server_name;

# PHP only, required if PHP was built with --enable-force-cgi-redirect
# fastcgi_param  REDIRECT_STATUS    200;
```

Como puede ver, este archivo también contiene el `REQUEST_METHOD` parámetro. En lugar de pasar eso manualmente, simplemente puede incluir este archivo en su configuración:

```sh
user www-data;

events {

}

http {

      include /etc/nginx/mime.types;

      server {

          listen 80;
          server_name nginx-handbook.test;
          root /srv/nginx-handbook-projects/php-demo;

          index index.php;

          location / {
              try_files $uri $uri/ =404;
          }

          location ~ \.php$ {
              fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
              fastcgi_param SCRIPT_FILENAME $realpath_root$fastcgi_script_name;
              include /etc/nginx/fastcgi_params;
      }
   }
}
```

Su servidor debería comportarse de la misma manera. Además del `fastcgi_params` archivo, también puede encontrar el `fastcgi.conf` archivo que contiene un conjunto de parámetros ligeramente diferente. Le sugiero que evite eso debido a algunas inconsistencias con su comportamiento.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo utilizar NGINX como equilibrador de carga

Gracias al diseño de proxy inverso de NGINX, puede configurarlo fácilmente como balanceador de carga.

Ya he agregado una demostración al repositorio que viene con este artículo. Si ya ha clonado el repositorio dentro del /`srv/nginx-handbook-projects/` directorio, la demostración debería estar en el `/srv/nginx-handbook-projects/load-balancer-demo/` directorio.

En un escenario de la vida real, el equilibrio de carga puede ser necesario en proyectos a gran escala distribuidos en varios servidores. Pero para esta demostración simple, he creado tres servidores Node.js muy simples que responden con un número de servidor y un código de estado 200.

Ejecute los siguientes comandos para iniciar los tres servidores Node.js:

```sh
pm2 start /srv/nginx-handbook-projects/load-balancer-demo/server-1.js

pm2 start /srv/nginx-handbook-projects/load-balancer-demo/server-2.js

pm2 start /srv/nginx-handbook-projects/load-balancer-demo/server-3.js

pm2 list

# ┌────┬────────────────────┬──────────┬──────┬───────────┬──────────┬──────────┐
# │ id │ name               │ mode     │ ↺    │ status    │ cpu      │ memory   │
# ├────┼────────────────────┼──────────┼──────┼───────────┼──────────┼──────────┤
# │ 0  │ server-1           │ fork     │ 0    │ online    │ 0%       │ 37.4mb   │
# │ 1  │ server-2           │ fork     │ 0    │ online    │ 0%       │ 37.2mb   │
# │ 2  │ server-3           │ fork     │ 0    │ online    │ 0%       │ 37.1mb   │
# └────┴────────────────────┴──────────┴──────┴───────────┴──────────┴──────────┘
```

Deben ejecutarse tres servidores Node.js en localhost:3001, localhost:3002, localhost:3003 respectivamente.

Ahora actualice su configuración de la siguiente manera:

```sh
events {

}

http {

    upstream backend_servers {
        server localhost:3001;
        server localhost:3002;
        server localhost:3003;
    }

    server {

        listen 80;
        server_name nginx-handbook.test;

        location / {
            proxy_pass http://backend_servers;
        }
    }
}
```

La configuración dentro del `server` contexto es la misma que ya has visto. El `upstream` contexto, sin embargo, es nuevo. Un upstream en NGINX es una colección de servidores que se pueden tratar como un solo backend.

Entonces, los tres servidores que comenzó a usar PM2 se pueden colocar dentro de un solo flujo ascendente y puede dejar que NGINX equilibre la carga entre ellos.

Para probar la configuración, deberá enviar una serie de solicitudes al servidor. Puede automatizar el proceso usando un `while` bucle en bash:

```sh
while sleep 0.5; do curl http://nginx-handbook.test; done

# response from server - 2.
# response from server - 3.
# response from server - 1.
# response from server - 2.
# response from server - 3.
# response from server - 1.
# response from server - 2.
# response from server - 3.
# response from server - 1.
# response from server - 2.
```

Puede cancelar el bucle pulsando `Ctrl + C` en su teclado. Como puede ver en las respuestas del servidor, NGINX equilibra la carga de los servidores automáticamente.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo optimizar NGINX para obtener el máximo rendimiento

En esta sección del artículo, aprenderá sobre varias formas de obtener el máximo rendimiento de su servidor.

Algunos de estos métodos serán específicos de la aplicación, lo que significa que probablemente necesitarán ajustes teniendo en cuenta los requisitos de su aplicación. Pero algunas de ellas serán técnicas generales de optimización.

Al igual que en las secciones anteriores, los cambios en la configuración serán frecuentes en esta, así que no olvides validar y recargar tu archivo de configuración cada vez.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo configurar procesos de trabajo y conexiones de trabajo

Como ya mencioné en una sección anterior, NGINX puede generar múltiples procesos de trabajo capaces de manejar miles de solicitudes cada uno.

```sh
sudo systemctl status nginx

# ● nginx.service - A high performance web server and a reverse proxy server
#      Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
#      Active: active (running) since Sun 2021-04-25 08:33:11 UTC; 5h 45min ago
#        Docs: man:nginx(8)
#    Main PID: 3904 (nginx)
#       Tasks: 2 (limit: 1136)
#      Memory: 3.2M
#      CGroup: /system.slice/nginx.service
#              ├─ 3904 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
#              └─16443 nginx: worker process
```

Como puede ver, en este momento solo hay un proceso de trabajo NGINX en el sistema. Este número, sin embargo, se puede cambiar haciendo un pequeño cambio en el archivo de configuración.

```sh
worker_processes 2;

events {

}

http {

    server {

        listen 80;
        server_name nginx-handbook.test;

        return 200 "worker processes and worker connections configuration!\n";
    }
}
```

La `worker_process` directiva escrita en el `main` contexto es responsable de establecer la cantidad de procesos de trabajo para generar. Ahora verifique el servicio NGINX una vez más y debería ver dos procesos de trabajo:

```sh
sudo systemctl status nginx

# ● nginx.service - A high performance web server and a reverse proxy server
#      Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
#      Active: active (running) since Sun 2021-04-25 08:33:11 UTC; 5h 54min ago
#        Docs: man:nginx(8)
#     Process: 22610 ExecReload=/usr/sbin/nginx -g daemon on; master_process on; -s reload (code=exited, status=0/SUCCESS)
#    Main PID: 3904 (nginx)
#       Tasks: 3 (limit: 1136)
#      Memory: 3.7M
#      CGroup: /system.slice/nginx.service
#              ├─ 3904 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
#              ├─22611 nginx: worker process
#              └─22612 nginx: worker process
```

Establecer el número de procesos de trabajo es fácil, pero determinar el número óptimo de procesos de trabajo requiere un poco más de trabajo.

Los procesos de trabajo son de naturaleza asíncrona. Esto significa que procesarán las solicitudes entrantes tan rápido como lo permita el hardware.

Ahora considere que su servidor se ejecuta en un procesador de un solo núcleo. Si establece la cantidad de procesos de trabajo en 1, ese único proceso utilizará el 100 % de la capacidad de la CPU. Pero si lo configura en 2, los dos procesos podrán utilizar el 50% de la CPU cada uno. Por lo tanto, aumentar la cantidad de procesos de trabajo no significa un mejor rendimiento.

Una regla general para determinar el número óptimo de procesos de trabajo es **número de procesos de trabajo = número de núcleos de CPU**.

Si está ejecutando en un servidor con una CPU de doble núcleo, la cantidad de procesos de trabajo debe establecerse en 2. En un núcleo cuádruple, debe establecerse en 4 ... y entiende la idea.

Determinar la cantidad de CPU en su servidor es muy fácil en Linux.

```sh
nproc

# 1
```

Estoy en una sola máquina virtual de CPU, por lo `npro` cque detecta que hay una CPU. Ahora que conoce el número de CPU, todo lo que queda por hacer es establecer el número en la configuración.

Eso está muy bien, pero cada vez que actualice el servidor y cambie el número de CPU, tendrá que actualizar la configuración del servidor manualmente.

NGINX proporciona una mejor manera de lidiar con este problema. Simplemente puede establecer la cantidad de procesos de trabajo `auto` y NGINX establecerá la cantidad de procesos en función de la cantidad de CPU automáticamente.

```sh
worker_processes auto;

events {

}

http {

    server {

        listen 80;
        server_name nginx-handbook.test;

        return 200 "worker processes and worker connections configuration!\n";
    }
}
```

Inspeccione el proceso NGINX una vez más:

```sh
sudo systemctl status nginx

# ● nginx.service - A high performance web server and a reverse proxy server
#      Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
#      Active: active (running) since Sun 2021-04-25 08:33:11 UTC; 6h ago
#        Docs: man:nginx(8)
#     Process: 22610 ExecReload=/usr/sbin/nginx -g daemon on; master_process on; -s reload (code=exited, status=0/SUCCESS)
#    Main PID: 3904 (nginx)
#       Tasks: 2 (limit: 1136)
#      Memory: 3.2M
#      CGroup: /system.slice/nginx.service
#              ├─ 3904 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
#              └─23659 nginx: worker process
```

El número de procesos de trabajo vuelve a ser uno, porque eso es lo óptimo para este servidor.

Además de los procesos de trabajo, también existe la conexión de trabajo, que indica el mayor número de conexiones que puede manejar un solo proceso de trabajo.

Al igual que la cantidad de procesos de trabajo, este número también está relacionado con la cantidad de su núcleo de CPU y la cantidad de archivos que su sistema operativo puede abrir por núcleo.

Averiguar este número es muy fácil en Linux:

```sh
ulimit -n

# 1024
```

Ahora que tienes el número, todo lo que queda es establecerlo en la configuración:

```sh
worker_processes auto;

events {
    worker_connections 1024;
}

http {

    server {

        listen 80;
        server_name nginx-handbook.test;

        return 200 "worker processes and worker connections configuration!\n";
    }
}
```

La `worker_connections` directiva es responsable de establecer el número de conexiones de trabajadores en una configuración. Esta es también la primera vez que trabaja con el `events` contexto.

En una sección anterior, mencioné que este contexto se usa para establecer valores utilizados por NGINX a nivel general. La configuración de conexiones de trabajadores es un ejemplo de ello.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo almacenar contenido estático en caché

La segunda técnica para optimizar su servidor es almacenar contenido estático en caché. Independientemente de la aplicación que esté sirviendo, siempre se está sirviendo una cierta cantidad de contenido estático, como hojas de estilo, imágenes, etc.

Teniendo en cuenta que no es probable que este contenido cambie con mucha frecuencia, es una buena idea almacenarlos en caché durante un cierto período de tiempo. NGINX también facilita esta tarea.

```sh
worker_processes auto;

events {
    worker_connections 1024;
}

http {

    include /etc/nginx/mime.types;

    server {

        listen 80;
        server_name nginx-handbook.test;

        root /srv/nginx-handbook-projects/static-demo;

        location ~* \.(css|js|jpg)$ {
            access_log off;

            add_header Cache-Control public;
            add_header Pragma public;
            add_header Vary Accept-Encoding;
            expires 1M;
        }
    }
}
```

Al escribir `location ~\* .(css|js|jpg)$` , le indica a NGINX que coincida con las solicitudes que solicitan un archivo que termine con `.css` , `.js` y `.jpg`.

Puede usar la `add_header` directiva para incluir un encabezado en la respuesta al cliente. Anteriormente, vio la `proxy_set_header` directiva utilizada para establecer encabezados en una solicitud en curso al servidor backend. La `add_header` directiva, por otro lado, solo agrega un encabezado dado a la respuesta.

Al configurar el `Cache-Control` encabezado como público, le está diciendo al cliente que este contenido se puede almacenar en caché de cualquier manera. El `Pragma` encabezado es solo una versión anterior del `Cache-Control` encabezado y hace más o menos lo mismo.

El siguiente encabezado, `Vary` , es responsable de informar al cliente que este contenido almacenado en caché puede variar.

El valor de `Accept-Encoding` significa que el contenido puede variar dependiendo de la codificación de contenido aceptada por el cliente. Esto se aclarará más en la siguiente sección.

Finalmente, la `expires` directiva le permite configurar el `Expires` encabezado convenientemente. La `expires` directiva toma la duración del tiempo que este caché será válido. Al configurarlo, `1M` le está diciendo a NGINX que almacene en caché el contenido durante un mes. También puede configurarlo en `10m` 10 minutos, `24h` 24 horas, etc.

Ahora, para probar la configuración, envíe una solicitud del archivo the-nginx-handbook.jpg desde el servidor:

```sh
curl -I http://nginx-handbook.test/the-nginx-handbook.jpg

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Sun, 25 Apr 2021 15:58:22 GMT
# Content-Type: image/jpeg
# Content-Length: 19209
# Last-Modified: Sun, 25 Apr 2021 08:35:33 GMT
# Connection: keep-alive
# ETag: "608529d5-4b09"
# Expires: Tue, 25 May 2021 15:58:22 GMT
# Cache-Control: max-age=2592000
# Cache-Control: public
# Pragma: public
# Vary: Accept-Encoding
# Accept-Ranges: bytes
```

Como puede ver, los encabezados se agregaron a la respuesta y cualquier navegador moderno debería poder interpretarlos.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo comprimir respuestas

La última técnica de optimización que mostraré hoy es bastante sencilla: comprimir las respuestas para reducir su tamaño.

```sh
worker_processes auto;

events {
    worker_connections 1024;
}

http {
    include /etc/nginx/mime.types;

    gzip on;
    gzip_comp_level 3;

    gzip_types text/css text/javascript;

    server {

        listen 80;
        server_name nginx-handbook.test;

        root /srv/nginx-handbook-projects/static-demo;

        location ~* \.(css|js|jpg)$ {
            access_log off;

            add_header Cache-Control public;
            add_header Pragma public;
            add_header Vary Accept-Encoding;
            expires 1M;
        }
    }
}
```

Si aún no está familiarizado con él, GZIP es un formato de archivo popular utilizado por las aplicaciones para la compresión y descompresión de archivos. NGINX puede utilizar este formato para comprimir respuestas usando las `gzip` directivas.

Al escribir `gzip on` en el `http` contexto, le está dando instrucciones a NGINX para que comprima las respuestas. La `gzip_comp_level` directiva establece el nivel de compresión. Puede establecerlo en un número muy alto, pero eso no garantiza una mejor compresión. Establecer un número entre 1 y 4 le brinda un resultado eficiente. Por ejemplo, me gusta establecerlo en 3.

De forma predeterminada, NGINX comprime las respuestas HTML. Para comprimir otros formatos de archivo, deberá pasarlos como parámetros a la `gzip_types` directiva. Al escribir `gzip_types text/css text/javascript;` , le está diciendo a NGINX que comprima cualquier archivo con los tipos mime de texto/css y texto/javascript.

Configurar la compresión en NGINX no es suficiente. El cliente tiene que pedir la respuesta comprimida en lugar de las respuestas sin comprimir. Espero que recuerde la `add_header Vary Accept-Encoding;` línea en la sección anterior sobre el almacenamiento en caché. Este encabezado le permite saber al cliente que la respuesta puede variar según lo que acepte el cliente.

Como ejemplo, si desea solicitar la versión sin comprimir del archivo mini.min.css del servidor, puede hacer algo como esto:

```sh
curl -I http://nginx-handbook.test/mini.min.css

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Sun, 25 Apr 2021 16:30:32 GMT
# Content-Type: text/css
# Content-Length: 46887
# Last-Modified: Sun, 25 Apr 2021 08:35:33 GMT
# Connection: keep-alive
# ETag: "608529d5-b727"
# Expires: Tue, 25 May 2021 16:30:32 GMT
# Cache-Control: max-age=2592000
# Cache-Control: public
# Pragma: public
# Vary: Accept-Encoding
# Accept-Ranges: bytes
```

Como puede ver, no hay nada sobre la compresión. Ahora, si desea solicitar la versión comprimida del archivo, deberá enviar un encabezado adicional.

```sh
curl -I -H "Accept-Encoding: gzip" http://nginx-handbook.test/mini.min.css

# HTTP/1.1 200 OK
# Server: nginx/1.18.0 (Ubuntu)
# Date: Sun, 25 Apr 2021 16:31:38 GMT
# Content-Type: text/css
# Last-Modified: Sun, 25 Apr 2021 08:35:33 GMT
# Connection: keep-alive
# ETag: W/"608529d5-b727"
# Expires: Tue, 25 May 2021 16:31:38 GMT
# Cache-Control: max-age=2592000
# Cache-Control: public
# Pragma: public
# Vary: Accept-Encoding
# Content-Encoding: gzip
```

Como puede ver en los encabezados de respuesta, `Content-Encoding` ahora está configurado para `gzip` indicar que esta es la versión comprimida del archivo.

Ahora, si desea comparar la diferencia en el tamaño del archivo, puede hacer algo como esto:

```sh
cd ~
mkdir compression-test && cd compression-test

curl http://nginx-handbook.test/mini.min.css > uncompressed.css

curl -H "Accept-Encoding: gzip" http://nginx-handbook.test/mini.min.css > compressed.css

ls -lh

# -rw-rw-r-- 1 vagrant vagrant 9.1K Apr 25 16:35 compressed.css
# -rw-rw-r-- 1 vagrant vagrant  46K Apr 25 16:35 uncompressed.css
```

La versión sin comprimir del archivo es `46K` y la versión comprimida es `9.1K` casi seis veces más pequeña. En sitios de la vida real donde las hojas de estilo pueden ser mucho más grandes, la compresión puede hacer que sus respuestas sean más pequeñas y rápidas.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo entender el archivo de configuración principal

Espero que recuerde el `nginx.conf` archivo original que cambió de nombre en una sección anterior. De acuerdo con el wiki de Debian , este archivo debe ser modificado por los mantenedores de NGINX y no por los administradores del servidor, a menos que sepan exactamente lo que están haciendo.

Pero a lo largo de todo el artículo, les he enseñado a configurar sus servidores en este mismo archivo. En esta sección, sin embargo, le mostraré cómo debe configurar sus servidores sin cambiar el `nginx.conf` archivo.

Para empezar, primero elimine o cambie el nombre de su `nginx.conf` archivo modificado y recupere el original:

```sh
sudo rm /etc/nginx/nginx.conf

sudo mv /etc/nginx/nginx.conf.backup /etc/nginx/nginx.conf

sudo nginx -s reload
```

Ahora NGINX debería volver a su estado original. Echemos un vistazo al contenido de este archivo una vez más ejecutando el sudo cat /etc/nginx/nginx.confarchivo:

```sh
user www-data;
worker_processes auto;
pid /run/nginx.pid;
include /etc/nginx/modules-enabled/*.conf;

events {
	worker_connections 768;
	# multi_accept on;
}

http {

	##
	# Basic Settings
	##

	sendfile on;
	tcp_nopush on;
	tcp_nodelay on;
	keepalive_timeout 65;
	types_hash_max_size 2048;
	# server_tokens off;

	# server_names_hash_bucket_size 64;
	# server_name_in_redirect off;

	include /etc/nginx/mime.types;
	default_type application/octet-stream;

	##
	# SSL Settings
	##

	ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3; # Dropping SSLv3, ref: POODLE
	ssl_prefer_server_ciphers on;

	##
	# Logging Settings
	##

	access_log /var/log/nginx/access.log;
	error_log /var/log/nginx/error.log;

	##
	# Gzip Settings
	##

	gzip on;

	# gzip_vary on;
	# gzip_proxied any;
	# gzip_comp_level 6;
	# gzip_buffers 16 8k;
	# gzip_http_version 1.1;
	# gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;

	##
	# Virtual Host Configs
	##

	include /etc/nginx/conf.d/*.conf;
	include /etc/nginx/sites-enabled/*;
}


#mail {
#	# See sample authentication script at:
#	# http://wiki.nginx.org/ImapAuthenticateWithApachePhpScript
#
#	# auth_http localhost/auth.php;
#	# pop3_capabilities "TOP" "USER";
#	# imap_capabilities "IMAP4rev1" "UIDPLUS";
#
#	server {
#		listen     localhost:110;
#		protocol   pop3;
#		proxy      on;
#	}
#
#	server {
#		listen     localhost:143;
#		protocol   imap;
#		proxy      on;
#	}
#}
```

Ahora debería poder entender este archivo sin muchos problemas. En el contexto principal `user www-data;` , las `worker_processes auto; `líneas deben ser fácilmente reconocibles para usted.

La línea `pid /run/nginx.pid; `establece el ID de proceso para el proceso NGINX e `include /etc/nginx/modules-enabled/\*.conf;` incluye cualquier archivo de configuración que se encuentre en el `/etc/nginx/modules-enabled/` directorio.

Este directorio está destinado a módulos dinámicos NGINX. No he cubierto los módulos dinámicos en este artículo, así que lo omitiré.

Ahora dentro del `http` contexto, en la configuración básica, puede ver algunas técnicas de optimización comunes aplicadas. Esto es lo que hacen estas técnicas:

- `sendfile on;` deshabilita el almacenamiento en búfer para archivos estáticos.
- `tcp_nopush on;` permite enviar el encabezado de respuesta en un paquete.
- `tcp_nodelay on;` deshabilita el algoritmo de Nagle, lo que resulta en una entrega de archivos estáticos más rápida.

La `keepalive_timeout` directiva indica cuánto tiempo mantener abierta una conexión y la `types_hash_maxsize` directiva establece el tamaño del mapa hash de tipos. También incluye el `mime.types` archivo por defecto.

Omitiré la configuración de SSL simplemente porque no la hemos cubierto en este artículo. Ya hemos discutido la configuración de registro y gzip. Puede ver algunas de las directivas con respecto a gzip como se comenta. Siempre que comprenda lo que está haciendo, puede personalizar esta configuración.

Utiliza el `mail` contexto para configurar NGINX como un servidor de correo. Hasta ahora solo hemos hablado de NGINX como un servidor web, así que también lo omitiré.

Ahora, en la configuración de hosts virtuales, debería ver dos líneas de la siguiente manera:

```sh
##
# Virtual Host Configs
##

include /etc/nginx/conf.d/*.conf;
include /etc/nginx/sites-enabled/*;
```

Estas dos líneas indican a NGINX que incluya cualquier archivo de configuración que se encuentre dentro de los directorios `/etc/nginx/conf.d/` y `/etc/nginx/sites-enabled/`.

Después de ver estas dos líneas, la gente suele tomar estos dos directorios como el lugar ideal para colocar sus archivos de configuración, pero eso no es correcto.

Hay otro directorio `/etc/nginx/sites-available/` destinado a almacenar archivos de configuración para sus hosts virtuales. El `/etc/nginx/sites-enabled/` directorio está destinado a almacenar los enlaces simbólicos a los archivos del `/etc/nginx/sites-available/directorio`.

De hecho, hay una configuración de ejemplo:

```sh
ln -lh /etc/nginx/sites-enabled/

# lrwxrwxrwx 1 root root 34 Apr 25 08:33 default -> /etc/nginx/sites-available/default
```

Como puede ver, el directorio contiene un enlace simbólico al `/etc/nginx/sites-available/default` archivo.

La idea es escribir varios hosts virtuales dentro del `/etc/nginx/sites-available/` directorio y activar algunos de ellos al vincularlos simbólicamente al `/etc/nginx/sites-enabled/` directorio.

Para demostrar este concepto, configuremos un servidor estático simple. Primero, elimine el enlace simbólico predeterminado del host virtual, desactivando esta configuración en el proceso:

```sh
sudo rm /etc/nginx/sites-enabled/default

ls -lh /etc/nginx/sites-enabled/

# lrwxrwxrwx 1 root root 41 Apr 25 18:01 nginx-handbook -> /etc/nginx/sites-available/nginx-handbook
```

Cree un nuevo archivo ejecutando `sudo touch /etc/nginx/sites-available/nginx-handbook` y coloque el siguiente contenido allí:

```sh
server {
    listen 80;
    server_name nginx-handbook.test;

    root /srv/nginx-handbook-projects/static-demo;
}
```

Los archivos dentro del `/etc/nginx/sites-available/` directorio deben incluirse dentro del `http` contexto principal, por lo que solo deben contener serverbloques.

Ahora cree un enlace simbólico a este archivo dentro del `/etc/nginx/sites-enabled/` directorio ejecutando el siguiente comando:

```sh
sudo ln -s /etc/nginx/sites-available/nginx-handbook /etc/nginx/sites-enabled/nginx-handbook

ls -lh /etc/nginx/sites-enabled/

# lrwxrwxrwx 1 root root 34 Apr 25 08:33 default -> /etc/nginx/sites-available/default
# lrwxrwxrwx 1 root root 41 Apr 25 18:01 nginx-handbook -> /etc/nginx/sites-available/nginx-handbook
```

Antes de validar y volver a cargar el archivo de configuración, deberá volver a abrir los archivos de registro. De lo contrario, puede obtener un error de permiso denegado. Esto sucede porque la ID del proceso es diferente esta vez como resultado del intercambio del nginx.confarchivo anterior.

```sh
sudo rm /var/log/nginx/*.log

sudo touch /var/log/nginx/access.log /var/log/nginx/error.log

sudo nginx -s reopen
```

Finalmente, valide y vuelva a cargar el archivo de configuración:

```sh
sudo nginx -t

# nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
# nginx: configuration file /etc/nginx/nginx.conf test is successful

sudo nginx -s reload
```

Visite el servidor (http://nginx-handbook.test/) y debería ser recibido con la buena y antigua página del manual de NGINX:

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/size/w1600/2021/04/image-100.png" alt="screenshot" />
</div>

Si configuró el servidor correctamente y aún recibe la página de bienvenida de NGINX anterior, realice una actualización completa. El navegador a menudo conserva activos antiguos y requiere un poco de limpieza.

<p align="right">(<a href="#top">volver arriba</a>)</p>s

```sh

```

```sh

```

```sh

```

```sh

```

```sh

```

```sh

```

```sh

```

```sh

```

<p align="right">(<a href="#top">volver arriba</a>)</p>

<!-- GETTING STARTED -->

## Getting Started

This is an example of how you may give instructions on setting up your project locally.
To get a local copy up and running follow these simple example steps.

### Prerequisites

This is an example of how to list things you need to use the software and how to install them.

- npm
  ```sh
  npm install npm@latest -g
  ```

### Installation

_Below is an example of how you can instruct your audience on installing and setting up your app. This template doesn't rely on any external dependencies or services._

1. Get a free API Key at [https://example.com](https://example.com)
2. Clone the repo
   ```sh
   git clone https://github.com/your_username_/Project-Name.git
   ```
3. Install NPM packages
   ```sh
   npm install
   ```
4. Enter your API in `config.js`
   ```js
   const API_KEY = 'ENTER YOUR API'
   ```

<p align="right">(<a href="#top">volver arriba</a>)</p>

<!-- USAGE EXAMPLES -->

## Usage

Use this space to show useful examples of how a project can be used. Additional screenshots, code examples and demos work well in this space. You may also link to more resources.

_For more examples, please refer to the [Documentation](https://example.com)_

<p align="right">(<a href="#top">volver arriba</a>)</p>

<!-- ROADMAP -->

## Roadmap

- [x] Add Changelog
- [x] Add volver arriba links
- [ ] Add Additional Templates w/ Examples
- [ ] Add "components" document to easily copy & paste sections of the readme
- [ ] Multi-language Support
  - [ ] Chinese
  - [ ] Spanish

See the [open issues](https://github.com/othneildrew/Best-README-Template/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#top">volver arriba</a>)</p>

<!-- CONTRIBUTING -->

## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#top">volver arriba</a>)</p>

<!-- LICENSE -->

## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#top">volver arriba</a>)</p>

<!-- CONTACT -->

## Contact

Your Name - [@your_twitter](https://twitter.com/your_username) - email@example.com

Project Link: [https://github.com/your_username/repo_name](https://github.com/your_username/repo_name)

<p align="right">(<a href="#top">volver arriba</a>)</p>

<!-- ACKNOWLEDGMENTS -->

## Acknowledgments

Use this space to list resources you find helpful and would like to give credit to. I've included a few of my favorites to kick things off!

- [Choose an Open Source License](https://choosealicense.com)
- [GitHub Emoji Cheat Sheet](https://www.webpagefx.com/tools/emoji-cheat-sheet)
- [Malven's Flexbox Cheatsheet](https://flexbox.malven.co/)
- [Malven's Grid Cheatsheet](https://grid.malven.co/)
- [Img Shields](https://shields.io)
- [GitHub Pages](https://pages.github.com)
- [Font Awesome](https://fontawesome.com)
- [React Icons](https://react-icons.github.io/react-icons/search)

<p align="right">(<a href="#top">volver arriba</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->

[contributors-shield]: https://img.shields.io/github/contributors/othneildrew/Best-README-Template.svg?style=for-the-badge
[contributors-url]: https://github.com/othneildrew/Best-README-Template/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/othneildrew/Best-README-Template.svg?style=for-the-badge
[forks-url]: https://github.com/othneildrew/Best-README-Template/network/members
[stars-shield]: https://img.shields.io/github/stars/othneildrew/Best-README-Template.svg?style=for-the-badge
[stars-url]: https://github.com/othneildrew/Best-README-Template/stargazers
[issues-shield]: https://img.shields.io/github/issues/othneildrew/Best-README-Template.svg?style=for-the-badge
[issues-url]: https://github.com/othneildrew/Best-README-Template/issues
[license-shield]: https://img.shields.io/github/license/othneildrew/Best-README-Template.svg?style=for-the-badge
[license-url]: https://github.com/othneildrew/Best-README-Template/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/othneildrew
[product-screenshot]: images/screenshot.png
[next.js]: https://img.shields.io/badge/next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white
[next-url]: https://nextjs.org/
[react.js]: https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB
[react-url]: https://reactjs.org/
[vue.js]: https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D
[vue-url]: https://vuejs.org/
[angular.io]: https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white
[angular-url]: https://angular.io/
[svelte.dev]: https://img.shields.io/badge/Svelte-4A4A55?style=for-the-badge&logo=svelte&logoColor=FF3E00
[svelte-url]: https://svelte.dev/
[laravel.com]: https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white
[laravel-url]: https://laravel.com
[bootstrap.com]: https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white
[bootstrap-url]: https://getbootstrap.com
[jquery.com]: https://img.shields.io/badge/jQuery-0769AD?style=for-the-badge&logo=jquery&logoColor=white
[jquery-url]: https://jquery.com
