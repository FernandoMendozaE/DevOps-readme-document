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
    <li><a href="#roadmap">Roadmap</a></li>
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
| Prefijo preferencial | ``          |
| REGEX                | `~` o `~*`  |
| Prefijo              | `None`      |

</div>

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
