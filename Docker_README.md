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
  <a href="https://docs.docker.com/">
    <img src="images/docker.png" alt="Logo" width="180" height="120">
  </a>

  <h3 align="center">Documentación-Comandos</h3>

  <p align="center">
    <br />
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Tabla de contenido</summary>
  <ol>
    <li>
      <a href="#introducción-a-la-contenedorización-y-docker">Introducción a la contenedorización y Docker</a>
    </li>
    <li>
      <a href="#conceptos-básicos-de-docker">Conceptos básicos de Docker</a>
      <ul>
        <li><a href="#hello-world-en-docker">Hello World en Docker</a>
        </li>
        <li><a href="#que-es-un-contenedor">Que es un Contenedor</a></li>
        <li><a href="#que-es-una-imagen-docker">Que es una imagen Docker</a></li>
        <li><a href="#descripción-general-de-la-arquitectura-de-docker">Descripción general de la arquitectura de Docker</a></li>
      </ul>
    </li>
    <li>
      <a href="#conceptos-básicos-de-manipulación-de-contenedores-docker">Conceptos de manipulación de contenedores Docker</a>
      <ul>
        <li><a href="#cómo-ejecutar-un-contenedor-run">Cómo ejecutar un contenedor (run)</a></li>
        <li><a href="#cómo-publicar-un-puerto---publish-o--p">Cómo publicar un puerto (--publish o -p)</a></li>
        <li><a href="#cómo-usar-el-modo-separado---detach-o--d">Cómo usar el modo separado (--detach o -d)</a></li>
        <li><a href="#cómo-enumerar-contenedores-container-ls-o-ps">Cómo enumerar contenedores (container ls o ps)</a></li>
        <li><a href="#cómo-nombrar-o-cambiar-el-nombre-de-un-contenedor---name-y-rename">Cómo nombrar o cambiar el nombre de un contenedor (name y rename)</a></li>
        <li><a href="#cómo-detener-o-matar-un-contenedor-en-funcionamiento-stop-o-kill">Cómo detener o matar un contenedor en funcionamiento (stop o kill)</a></li>
        <li><a href="#cómo-reiniciar-un-contenedor-start-o-restart">Cómo reiniciar un contenedor (start o restart)</a></li>
        <li><a href="#cómo-crear-un-contenedor-sin-ejecutar-create-o-start">Cómo crear un contenedor sin ejecutar (create o start)</a></li>
        <li><a href="#cómo-quitar-contenedores-colgantes-rm-y---rm">Cómo quitar contenedores colgantes (rm y --rm)</a></li>
        <li><a href="#cómo-ejecutar-un-contenedor-en-modo-interactivo--it">Cómo ejecutar un contenedor en modo interactivo (it)</a></li>
        <li><a href="#cómo-ejecutar-comandos-dentro-de-un-contenedor">Cómo ejecutar comandos dentro de un contenedor</a></li>
      </ul>
    </li>
    <li>
      <a href="#conceptos-básicos-de-manipulación-de-imágenes-de-docker">Conceptos básicos de manipulación de imágenes de Docker</a>
      <ul>
        <li><a href="#cómo-crear-una-imagen-acoplable-build">Cómo crear una imagen acoplable (build)</a></li>
        <li><a href="#cómo-etiquetar-imágenes-de-docker--t-o---tag">Cómo etiquetar imágenes de Docker (-t o --tag)</a></li>
        <li><a href="#cómo-enumerar-imágenes-de-docker-images-o-image-ls">Cómo enumerar imágenes de Docker (images o image ls)</a></li>
        <li><a href="#cómo-eliminar-imágenes-de-docker-rmi-o-image-rm">Cómo eliminar imágenes de Docker (rmi o image rm)</a></li>
        <li><a href="#usando-como-imagen-base-alpine-linux">Usando como imagen base Alpine Linux</a></li>
        <li><a href="#cómo-compartir-sus-imágenes-de-docker-en-línea">Cómo compartir sus imágenes de Docker en línea</a></li>
      </ul>
    </li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>

  </ol>
</details>

<!-- ABOUT THE PROJECT -->

## Introducción a la contenedorización y Docker

La **`contenedorización`** implica encapsular o empaquetar el código de software y todas sus dependencias para que pueda ejecutarse de manera uniforme y consistente en cualquier infraestructura.

**`Docker`** es una plataforma de contenedorización de código abierto que le permite contener sus aplicaciones, compartirlas mediante registros públicos o privados y también organizarlas.

## Conceptos básicos de Docker

### Hello World en Docker

Habra la terminal y ejecuta el siguiente comando:

```sh
docker run hello-world

# Unable to find image 'hello-world:latest' locally
# latest: Pulling from library/hello-world
# 0e03bdcc26d7: Pull complete
# Digest: sha256:4cf9c47f86df71d48364001ede3a4fcd85ae80ce02ebad74156906caff5378bc
# Status: Downloaded newer image for hello-world:latest
#
# Hello from Docker!
# This message shows that your installation appears to be working correctly.
#
# To generate this message, Docker took the following steps:
#  1. The Docker client contacted the Docker daemon.
#  2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
#     (amd64)
#  3. The Docker daemon created a new container from that image which runs the
#     executable that produces the output you are currently reading.
#  4. The Docker daemon streamed that output to the Docker client, which sent it
#     to your terminal.
#
# To try something more ambitious, you can run an Ubuntu container with:
#  $ docker run -it ubuntu bash
#
# Share images, automate workflows, and more with a free Docker ID:
#  https://hub.docker.com/
#
# For more examples and ideas, visit:
#  https://docs.docker.com/get-started/
```

La imagen [hello-world](https://hub.docker.com/_/hello-world) es un ejemplo de contenedorización mínima con Docker. Tiene un solo programa compilado a partir de un archivo [hello.c](https://github.com/docker-library/hello-world/blob/master/hello.c) responsable de imprimir el mensaje que estás viendo en tu terminal.

Ahora en su terminal, puede usar el `docker ps -a` comando para ver todos los contenedores que se están ejecutando actualmente o se han ejecutado en el pasado:

```sh
docker ps -a

# CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                     PORTS               NAMES
# 128ec8ceab71        hello-world         "/hello"            14 seconds ago      Exited (0) 13 seconds ago                      exciting_chebyshev
```

En la salida:

- `CONTAINER ID` – Se ejecuta una identificación del contenedor con ID `128ec8ceab71` .

- `IMAGE` – Usa la imagen `hello-world` .

- `STATUS` – Tiene `Exited (0) 13 seconds ago` donde el `(0)` código de salida significa que no se produjo ningún error durante el tiempo de ejecución del contenedor.

- `NAMES` - Se ejecutó un contenedor llamado `exciting_chebyshev`

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Que es un Contenedor

Un contenedor es una abstracción en la capa de la aplicación que empaqueta el código y las dependencias juntos. En lugar de virtualizar toda la máquina física, los contenedores virtualizan solo el sistema operativo host.

Al igual que las máquinas virtuales, los contenedores son entornos completamente aislados del sistema host y entre sí. También son mucho más livianos que la máquina virtual tradicional, por lo que se puede ejecutar una gran cantidad de contenedores simultáneamente sin afectar el rendimiento del sistema host.‌

Los contenedores y las máquinas virtuales son en realidad diferentes formas de virtualizar su hardware físico. La principal diferencia entre estos dos es el método de virtualización.

Las máquinas virtuales generalmente son creadas y administradas por un programa conocido como hipervisor, como Oracle VM VirtualBox , VMware Workstation , KVM , Microsoft Hyper-V , etc. Este programa de hipervisor generalmente se encuentra entre el sistema operativo host y las máquinas virtuales para actuar como un medio de comunicación.

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/2021/04/virtual-machines.svg" alt="screenshot" />
</div>

Cada máquina virtual viene con su propio sistema operativo invitado, que es tan pesado como el sistema operativo anfitrión.

La aplicación que se ejecuta dentro de una máquina virtual se comunica con el sistema operativo invitado, que se comunica con el hipervisor, que luego se comunica con el sistema operativo host para asignar los recursos necesarios de la infraestructura física a la aplicación en ejecución.

Como puede ver, existe una larga cadena de comunicación entre las aplicaciones que se ejecutan dentro de las máquinas virtuales y la infraestructura física. La aplicación que se ejecuta dentro de la máquina virtual puede requerir solo una pequeña cantidad de recursos, pero el sistema operativo invitado agrega una sobrecarga notable.

A diferencia de una máquina virtual, un contenedor hace el trabajo de virtualización de una manera más inteligente. En lugar de tener un sistema operativo invitado completo dentro de un contenedor, solo utiliza el sistema operativo host a través del tiempo de ejecución del contenedor mientras mantiene el aislamiento, al igual que una máquina virtual tradicional.

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/2021/04/containers.svg" alt="screenshot" />
</div>

El tiempo de ejecución del contenedor, que es Docker, se encuentra entre los contenedores y el sistema operativo host en lugar de un hipervisor. Luego, los contenedores se comunican con el tiempo de ejecución del contenedor, que luego se comunica con el sistema operativo host para obtener los recursos necesarios de la infraestructura física.

Como resultado de la eliminación de toda la capa del sistema operativo huésped, los contenedores son mucho más livianos y consumen menos recursos que las máquinas virtuales tradicionales.

Como demostración del punto, observe el siguiente bloque de código:

```sh
uname -a
# Linux alpha-centauri 5.8.0-22-generic #23-Ubuntu SMP Fri Oct 9 00:34:40 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

docker run alpine uname -a
# Linux f08dbbe9199b 5.8.0-22-generic #23-Ubuntu SMP Fri Oct 9 00:34:40 UTC 2020 x86_64 Linux
```

En el bloque de código anterior, ejecuté el `uname -a` comando en mi sistema operativo host para imprimir los detalles del kernel. Luego, en la siguiente línea, ejecuté el mismo comando dentro de un contenedor que ejecuta [Alpine Linux](https://alpinelinux.org/) .

Como puede ver en el resultado, el contenedor está usando el kernel de mi sistema operativo host. Esto demuestra que los contenedores virtualizan el sistema operativo host en lugar de tener un sistema operativo propio.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Que es una imagen Docker

Las imágenes son archivos autónomos de varias capas que actúan como plantilla para crear contenedores. Son como una copia congelada de solo lectura de un contenedor. Las imágenes se pueden intercambiar a través de registros.

En el pasado, diferentes motores de contenedores tenían diferentes formatos de imagen. Pero más tarde, la Open Container Initiative (OCI) definió una especificación estándar para imágenes de contenedores que cumplen los principales motores de contenedores que existen. Esto significa que una imagen creada con Docker se puede usar con otro tiempo de ejecución como Podman sin ningún problema adicional.

Los contenedores son solo imágenes en estado de ejecución. Cuando obtiene una imagen de Internet y ejecuta un contenedor con esa imagen, esencialmente crea otra capa temporal de escritura encima de las anteriores de solo lectura.

> Tenga en cuenta que las imágenes son archivos de solo lectura de varias capas que contienen su aplicación en el estado deseado.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Descripción general de la arquitectura de Docker

Ahora que se ha familiarizado con la mayoría de los conceptos fundamentales relacionados con la creación de contenedores y Docker, es hora de que comprenda cómo se diseñó Docker como software.

El motor consta de tres componentes principales:

1. **Docker Daemon:** El daemon ( `dockerd`) es un proceso que sigue ejecutándose en segundo plano y espera comandos del cliente. El daemon es capaz de administrar varios objetos Docker.
2. **Docker Client:** El cliente ( `docker`) es un programa de interfaz de línea de comandos principalmente responsable de transportar los comandos emitidos por los usuarios.
3. **API REST:** La API REST actúa como un puente entre el daemon y el cliente. Cualquier comando emitido usando el cliente pasa a través de la API para llegar finalmente al daemon.

Según los documentos oficiales:

> "Docker utiliza una arquitectura cliente-servidor. El cliente de Docker se comunica con el demonio de Docker , que hace el trabajo pesado de construir, ejecutar y distribuir sus contenedores de Docker".

<br>

Ahora es el momento de que entiendas cómo todas estas piezas del rompecabezas que acabas de aprender funcionan en armonía. Antes de sumergirme en la explicación de lo que realmente sucede cuando ejecuta el docker run `hello-world` comando, permítame mostrarle un pequeño diagrama que hice:

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/2021/01/docker-run-hello-world.svg" alt="screenshot" />
</div>

Esta imagen es una versión ligeramente modificada de la que se encuentra en los documentos oficiales . Los eventos que ocurren cuando ejecuta el comando son los siguientes:

1. Ejecutas el `docker run hello-world` comando donde `hello-world` está el nombre de una imagen.
2. El cliente de Docker se acerca al daemon, le dice que obtenga la `hello-world` imagen y ejecute un contenedor a partir de eso.
3. El demonio Docker busca la imagen dentro de su repositorio local y se da cuenta de que no está allí, lo que da como resultado `Unable to find image 'hello-world:latest' locally` que esté impreso en su terminal.
4. Luego, el demonio se comunica con el registro público predeterminado, que es Docker Hub, y extrae la última copia de la `hello-world` imagen, indicada por la `latest: Pulling from library/hello-world` línea en su terminal.
5. Luego, el demonio Docker crea un nuevo contenedor a partir de la imagen recién extraída.
6. Finalmente, el demonio Docker ejecuta el contenedor creado usando la `hello-world` imagen que genera el muro de texto en su terminal.

El comportamiento predeterminado del demonio Docker es buscar imágenes en el concentrador que no están presentes localmente. Pero una vez que se ha obtenido una imagen, permanecerá en el caché local. Entonces, si ejecuta el comando nuevamente, no verá las siguientes líneas en la salida:

```sh
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
0e03bdcc26d7: Pull complete
Digest: sha256:d58e752213a51785838f9eed2b7a498ffa1cb3aa7f946dda11af39286c3db9a9
Status: Downloaded newer image for hello-world:latest
```

Si hay una versión más nueva de la imagen disponible en el registro público, el daemon recuperará la imagen nuevamente. Esa `:latest` es una etiqueta. Las imágenes suelen tener etiquetas significativas para indicar versiones o compilaciones.

<p align="right">(<a href="#top">volver arriba</a>)</p>

## Conceptos básicos de manipulación de contenedores Docker

La manipulación de contenedores es una de las tareas más comunes que realizará todos los días, por lo que es crucial tener una comprensión adecuada de los diversos comandos.

Sin embargo, tenga en cuenta que esta no es una lista exhaustiva de todos los comandos que puede ejecutar en Docker. Hablaré sólo de los más comunes. Cada vez que desee obtener más información sobre los comandos disponibles, simplemente visite la [referencia](https://docs.docker.com/engine/reference/commandline/docker/) oficial de la línea de comandos de Docker.

### Cómo ejecutar un contenedor (run)

La sintaxis genérica de este comando es la siguiente:

```sh
docker run <image name>
```

Aunque este es un comando perfectamente válido, hay una mejor manera de enviar comandos al dockerdaemon, la línea de comandos se reestructuró para tener la siguiente sintaxis:

```sh
docker <object> <command> <options>
```

En esta sintaxis:

- `object` indica el tipo de objeto Docker que manipulará. Puede ser un `container`, `image` o `network` un `volume` objeto.
- `command` indica la tarea a realizar por el daemon, es decir el `run` comando.
- `options` puede ser cualquier parámetro válido que pueda anular el comportamiento predeterminado del comando, como la `--publish` opción para la asignación de puertos.

Ahora, siguiendo esta sintaxis, el `run` comando se puede escribir de la siguiente manera:

```sh
docker container run <image name>
```

La `image name` puede ser cualquier imagen de un registro en línea o de su sistema local . Como ejemplo, puede intentar ejecutar un contenedor utilizando la imagen [hello-world](https://hub.docker.com/_/hello-world) .

```sh
docker container run hello-world
# Unable to find image 'hello-world:latest' locally
# latest: Pulling from library/hello-world
# 2db29710123e: Pull complete
# Digest: sha256:7d246653d0511db2a6b2e0436cfd0e52ac8c066000264b3ce63331ac66dca625
# Status: Downloaded newer image for hello-world:latest

# Hello from Docker!
# This message shows that your installation appears to be working correctly.

# To generate this message, Docker took the following steps:
#  1. The Docker client contacted the Docker daemon.
#  2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
#     (amd64)
#  3. The Docker daemon created a new container from that image which runs the
#     executable that produces the output you are currently reading.
#  4. The Docker daemon streamed that output to the Docker client, which sent it
#     to your terminal.

# To try something more ambitious, you can run an Ubuntu container with:
#  $ docker run -it ubuntu bash

# Share images, automate workflows, and more with a free Docker ID:
#  https://hub.docker.com/

# For more examples and ideas, visit:
#  https://docs.docker.com/get-started/
```

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo publicar un puerto (--publish o -p)

Los contenedores son entornos aislados. Su sistema host no sabe nada sobre lo que sucede dentro de un contenedor. Por lo tanto, las aplicaciones que se ejecutan dentro de un contenedor permanecen inaccesibles desde el exterior.

Para permitir el acceso desde fuera de un contenedor, debe publicar el puerto adecuado dentro del contenedor en un puerto de su red local. La sintaxis común para la opción `--publish` o `-p` es la siguiente:

```sh
--publish <host port>:<container port>
```

Ejecute el siguiente comando en su terminal:

```sh
docker container run -p 8080:80 fhsinchy/hello-dock
# /docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
# /docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
# /docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
# 10-listen-on-ipv6-by-default.sh: Getting the checksum of /etc/nginx/conf.d/default.conf
# 10-listen-on-ipv6-by-default.sh: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
# /docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
# /docker-entrypoint.sh: Configuration complete; ready for start up
```

Cuando escribió `-p 8080:80` en la subsección anterior, significaba que cualquier solicitud enviada al puerto 8080 de su sistema host se reenviará al puerto 80 dentro del contenedor‌.

Ahora, para acceder a la aplicación en su navegador, visite http://127.0.0.1:8080.

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/size/w1600/2021/01/hello-dock.png" alt="screenshot" />
</div>

Puede detener el contenedor simplemente presionando la `ctrl + c` combinación de teclas mientras la ventana de la terminal está enfocada o cerrando la ventana de la terminal por completo.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo usar el modo separado (--detach o -d)

Otra opción muy popular del `run` comando es la opción `--detach` o `-d` . En el ejemplo anterior, para que el contenedor siguiera ejecutándose, tenía que mantener abierta la ventana de la terminal. Cerrar la ventana del terminal también detuvo el contenedor en ejecución.

Para anular este comportamiento y mantener un contenedor ejecutándose en segundo plano, puede incluir la `-d` opción con el `run` comando de la siguiente manera:

```sh
docker container run -d -p 8080:80 fhsinchy/hello-dock

# 9f21cb77705810797c4b847dbd330d9c732ffddba14fb435470567a7a3f46cdc
```

A diferencia del ejemplo anterior, esta vez no se le arrojará un muro de texto. En cambio, lo que obtendrá es la ID del contenedor recién creado.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo enumerar contenedores (container ls o ps)

El `container ls` comando se puede usar para enumerar los contenedores que se están ejecutando actualmente. Para hacerlo, ejecute el siguiente comando:

```sh
docker container ls

# CONTAINER ID        IMAGE                 COMMAND                  CREATED             STATUS              PORTS                  NAMES
# 9f21cb777058        fhsinchy/hello-dock   "/docker-entrypoint.…"   5 seconds ago       Up 5 seconds        0.0.0.0:8080->80/tcp   gifted_sammet
```

Se está ejecutando un contenedor llamado `gifted_sammet`. Fue creado `5 seconds ago` y el estado es `Up 5 seconds` , el que indica que el contenedor se ha estado ejecutando correctamente desde su creación.

El `CONTAINER ID` es `9f21cb777058` que son los primeros 12 caracteres del ID de contenedor completo. El ID de contenedor completo `9f21cb77705810797c4b847dbd330d9c732ffddba14fb435470567a7a3f46cdc` es de 64 caracteres. Este ID de contenedor completo se imprimió como resultado del `docker container run` comando en la sección anterior.

En la lista debajo de la `PORTS` columna, el puerto 8080 de su red local apunta hacia el puerto 80 dentro del contenedor. El nombre `gifted_sammet` es generado por Docker y puede ser algo completamente diferente en su computadora.

- **Para enumerar los contenedores que se han ejecutado en el pasado, puede usar la opción `--all` o `-a` :**

  ```sh
  docker ps -a

  # CONTAINER ID        IMAGE                 COMMAND                  CREATED             STATUS                     PORTS                  NAMES
  # 9f21cb777058        fhsinchy/hello-dock   "/docker-entrypoint.…"   2 minutes ago       Up 2 minutes               0.0.0.0:8080->80/tcp   gifted_sammet
  # 6cf52771dde1        fhsinchy/hello-dock   "/docker-entrypoint.…"   3 minutes ago       Exited (0) 3 minutes ago                          reverent_torvalds
  # 128ec8ceab71        hello-world           "/hello"
  ```

  Como puede ver, el segundo contenedor de la lista `reverent_torvalds` se creó anteriormente y salió con el código de estado 0, lo que indica que no se produjo ningún error durante el tiempo de ejecución del contenedor.

- **Para visualizar el último contenedor que ha realizado una operacion, puede usar la opción `-l` :**

  ```sh
  docker ps -l
  CONTAINER ID   IMAGE         COMMAND    CREATED          STATUS                      PORTS     NAMES
  62058bf739a1   hello-world   "/hello"   46 minutes ago   Exited (0) 46 minutes ago             vigilant_poitras
  ```

- **Para visualizar los últimos contenedores que han realizado alguna operacion, ademas se puede especificar la cantidad que se desea mostrar, puede usar la opción `-n` :**

  ```sh
  docker ps -n 4
  CONTAINER ID   IMAGE              COMMAND                  CREATED          STATUS                          PORTS      NAMES
  62058bf739a1   hello-world        "/hello"                 58 minutes ago   Exited (0) 58 minutes ago                  vigilant_poitras
  e72e9a6b0185   f8ee70060666       "docker-entrypoint.s…"   3 days ago       Exited (255) 3 days ago         3000/tcp   notes-api-dev
  4a31ad1dec73   postgres:12        "docker-entrypoint.s…"   3 days ago       Exited (255) 3 days ago         5432/tcp   notes-db-dev
  2697ebccfc75   notes-router:dev   "/docker-entrypoint.…"   3 days ago       Restarting (1) 19 seconds ago              notes-router-dev
  ```

  Mostrar n últimos contenedores creados (incluye todos los estados), en el ejemplo mostrara los ultimos 4 contenedores que hayan realizado alguna operacion.

- **Para poder ver el tamaño que ocupa un contendor en el sistema, puede usar la opción `-s` :**

  ```sh
  docker ps -s
  # CONTAINER ID   IMAGE                        COMMAND                  CREATED          STATUS             PORTS                      NAMES                  SIZE
  # 87f0fc540ec7   fhsinchy/hello-dock          "/docker-entrypoint.…"   11 minutes ago   Up 11 minutes      0.0.0.0:8080->80/tcp       compassionate_wilson   1.12kB (virtual 21.9MB)
  # d53d1c98d18b   testing-playwright-api_api   "npm start"              5 days ago       Up About an hour   0.0.0.0:3001->3000/tcp     affiliation-api        208kB (virtual 1.91GB)
  # 1faaed01558d   mongo                        "docker-entrypoint.s…"   5 days ago       Up About an hour   0.0.0.0:27019->27017/tcp   affiliation-db         0B (virtual 697MB)
  ```

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo nombrar o cambiar el nombre de un contenedor (--name y rename)

1. Nombrar un contenedor se puede lograr usando la `--name` opción. Para ejecutar otro contenedor utilizando la `fhsinchy/hello-dock` imagen con el nombre `hello-dock-container` , puede ejecutar el siguiente comando:

   ```sh
   docker container run -d -p 8888:80 --name hello-dock-container fhsinchy/hello-dock
   # b1db06e400c4c5e81a93a64d30acc1bf821bed63af36cab5cdb95d25e114f5fb
   ```

2. Para que puede cambiar el nombre de los contenedores antiguos con el container renamecomando. La sintaxis del comando es la siguiente:

   ```sh
   docker container rename <container identifier> <new name>
   ```

   <p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo detener o matar un contenedor en funcionamiento (stop o kill)

Hay dos comandos que se ocupan de esta tarea. El primero es el `container stop` comando. La sintaxis genérica del comando es la siguiente:

```sh
docker container stop <container identifier>
```

Donde `container identifier` puede ser el **id** o el **nombre del contenedor**.

Ahora ejecute el siguiente comando para detener el contenedor:

```sh
docker container stop hello-dock-container

# hello-dock-container
```

Si usa el nombre como identificador, obtendrá el nombre como resultado. El `stop` comando cierra un contenedor con gracia mediante el envío de una `SIGTERM` señal. Si el contenedor no se detiene dentro de un período determinado, `SIGKILL` se envía una señal que cierra el contenedor inmediatamente.

En los casos en los que desee enviar una `SIGKILL` señal en lugar de una `SIGTERM` señal, puede usar el `container kill` comando en su lugar. El container killcomando sigue la misma sintaxis que el `stop` comando.

```sh
docker container kill hello-dock-container-2

# hello-dock-container-2
```

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo reiniciar un contenedor (start o restart)

Cuando digo reiniciar me refiero a dos escenarios específicamente. Son los siguientes:

- Reiniciar un contenedor que se detuvo o eliminó previamente.
- Reinicio de un contenedor en ejecución.

El `container start` comando se puede usar para iniciar cualquier contenedor detenido o eliminado. La sintaxis del comando es la siguiente:

```sh
docker container start <container identifier>
```

Ahora, en escenarios en los que le gustaría reiniciar un contenedor en ejecución, puede usar el `container restart` comando. La sintaxis del comando es la siguiente:

```sh
docker container restart <container identifier>
```

La principal diferencia entre los dos comandos es que el `container restart` comando intenta detener el contenedor de destino y luego lo vuelve a iniciar, mientras que el comando `container start` simplemente inicia un contenedor ya detenido.

En el caso de un contenedor detenido, ambos comandos son exactamente iguales. Pero en el caso de un contenedor en ejecución, debe usar el `container restart` comando.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo crear un contenedor sin ejecutar (create o start)

Hasta ahora en esta sección, ha iniciado contenedores usando el `container run` comando que en realidad es una combinación de dos comandos separados. Estos comandos son los siguientes:

- `container create` El comando crea un contenedor a partir de una imagen determinada.
- `container start` El comando inicia un contenedor que ya se ha creado.

Usando estos dos comandos, puede hacer algo como lo siguiente:

```sh
docker container create -p 8080:80 fhsinchy/hello-dock

# 2e7ef5098bab92f4536eb9a372d9b99ed852a9a816c341127399f51a6d053856

docker container ls --all

# CONTAINER ID        IMAGE                 COMMAND                  CREATED             STATUS              PORTS               NAMES
# 2e7ef5098bab        fhsinchy/hello-dock   "/docker-entrypoint.…"   30 seconds ago      Created                                 hello-dock
```

Evidentemente por la salida del `container ls --all` comando, `hello-dock` se ha creado un contenedor con el nombre de usando la `fhsinchy/hello-dock` imagen. El `STATUS` del contenedor es `Created` en este momento y, dado que no se está ejecutando, no aparecerá en la lista sin el uso de la `--all` opción.

Una vez que se ha creado el contenedor, se puede iniciar con el `container start` comando.

```sh
docker container start hello-dock

# hello-dock

docker container ls

# CONTAINER ID        IMAGE                 COMMAND                  CREATED              STATUS              PORTS                  NAMES
# 2e7ef5098bab        fhsinchy/hello-dock   "/docker-entrypoint.…"   About a minute ago   Up 29 seconds       0.0.0.0:8080->80/tcp   hello-dock
```

El contenedor `STATUS` ha cambiado de `Created` a `Up 29 seconds` , lo que indica que el contenedor ahora está en estado de ejecución.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo quitar contenedores colgantes (rm y --rm)

Para eliminar un contenedor detenido, puede usar el `container rm` comando. La sintaxis genérica es la siguiente:

```sh
docker container rm <container identifier>
```

También puede eliminar varios contenedores a la vez pasando sus identificadores uno tras otro separados por espacios.

- **Eliminar todos los contenedores terminados**

  Puede localizar contenedores utilizando `docker ps -a` y filtrarlos según su estado: “created”, “restarting”, “running”, “paused” o “exited”. A fin de revisar la lista de contenedores terminados, utilice el indicador `-f` para filtrar según el estado. Cuando haya verificado que desea eliminar esos contenedores, utilice -q para pasar los IDs al comando `docker rm` .

  Enumerar:

  ```sh
  docker ps -a -f status=exited
  ```

  Eliminar:

  ```sh
  docker rm $(docker ps -a -f status=exited -q)
  ```

- **Eliminar contenedores utilizando más de un filtro**
  Los filtros de Docker pueden combinarse repitiendo el indicador de filtro con un valor adicional. Esto da como resultado una lista de contenedores que cumplen cualquier condición. Por ejemplo, si desea eliminar todos los contenedores marcados como `Created` (un estado que se puede generar cuando ejecuta un contenedor con un comando no válido) o `Exited`, puede utilizar dos filtros:

  Enumerar:

  ```sh
  docker ps -a -f status=exited -f status=created
  ```

  Eliminar:

  ```sh
  docker rm $(docker ps -a -f status=exited -f status=created -q)
  ```

- **Eliminar contenedores colgantes**

  En lugar de eliminar contenedores individuales, si desea eliminar todos los contenedores colgantes de una sola vez, puede usar el `container prune` comando.

  ```sh
  docker container prune
  ```

- **Detener y eliminar todos los contenedores**
  Puede revisar los contenedores de su sistema con `docker ps`. Al añadir el indicador `-a` se mostrarán todos los contenedores. Cuando esté seguro de que desea eliminarlos, puede añadir el indicador `-q` para proporcionar los ID a los comandos `docker stop` y `docker rm` :

  Enumerar:

  ```sh
  docker ps -a
  ```

  Eliminar:

  ```sh
  docker stop $(docker ps -a -q)
  docker rm $(docker ps -a -q)
  ```

- **Eliminar un contenedor al cerrarlo**
  Si al crear un contenedor sabe que no querrá conservarlo una vez que lo termine, puede ejecutar `docker run --rm` para eliminarlo automáticamente después de cerrarlo.

  Ejecutar y eliminar:

  ```sh
  docker run --rm image_name
  ```

  Ejecute el siguiente ejemplo:

  ```sh
  docker container run --rm --detach --publish 8888:80 --name hello-dock-volatile fhsinchy/hello-dock

  # 0d74e14091dc6262732bee226d95702c21894678efb4043663f7911c53fb79f3
  ```

  Puede usar el container lscomando para verificar que el contenedor se está ejecutando:

  ```sh
  docker container ls

  # CONTAINER ID   IMAGE                 COMMAND                  CREATED              STATUS              PORTS                  NAMES
  # 0d74e14091dc   fhsinchy/hello-dock   "/docker-entrypoint.…"   About a minute ago   Up About a minute   0.0.0.0:8888->80/tcp   hello-dock-volatile
  ```

  Ahora, si detiene el contenedor y luego verifica nuevamente con el container ls --allcomando:

  ```sh
  docker container stop hello-dock-volatile

  # hello-dock-volatile

  docker container ls --all

  # CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
  ```

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo ejecutar un contenedor en modo interactivo (-it)

Las distribuciones populares como Ubuntu , Fedora y Debian tienen imágenes oficiales de Docker disponibles en el hub. Los lenguajes de programación como python , php , go o tiempos de ejecución como node y deno tienen sus imágenes oficiales.

Estas imágenes no solo ejecutan algún programa preconfigurado. En cambio, estos están configurados para ejecutar un shell de forma predeterminada. En el caso de las imágenes del sistema operativo, puede ser algo como `sh` o `bash` y en el caso de los lenguajes de programación o los tiempos de ejecución, suele ser su shell de idioma predeterminado.

Como ya habrá aprendido de sus experiencias previas con las computadoras, los shells son programas interactivos. Una imagen configurada para ejecutar dicho programa es una imagen interactiva. Estas imágenes requieren `-it` que se pase una opción especial en el `container run` comando.

Como ejemplo, si ejecuta un contenedor usando la `ubuntu` imagen mediante la ejecución docker container run ubuntu, verá que no sucede nada. Pero si ejecuta el mismo comando con la `-it` opción, debería aterrizar directamente en bash dentro del contenedor de Ubuntu.

```sh
docker container run --rm -it ubuntu

# root@dbb1f56b9563:/# cat /etc/os-release
# NAME="Ubuntu"
# VERSION="20.04.1 LTS (Focal Fossa)"
# ID=ubuntu
# ID_LIKE=debian
# PRETTY_NAME="Ubuntu 20.04.1 LTS"
# VERSION_ID="20.04"
# HOME_URL="https://www.ubuntu.com/"
# SUPPORT_URL="https://help.ubuntu.com/"
# BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
# PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
# VERSION_CODENAME=focal
# UBUNTU_CODENAME=focal
```

Como puede ver en la salida del `cat /etc/os-release` comando, de hecho estoy interactuando con el bash que se ejecuta dentro del contenedor de Ubuntu.

La `-it` opción prepara el escenario para que interactúes con cualquier programa interactivo dentro de un contenedor. Esta opción es en realidad dos opciones separadas combinadas.

- La opción `-i` o `--interactive` lo conecta con el flujo de entrada del contenedor, para que pueda enviar entradas a bash.
- La opción `-t` o `--tty` se asegura de que obtenga un buen formato y una experiencia similar a la de un terminal nativo mediante la asignación de un pseudo-tty.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo ejecutar comandos dentro de un contenedor

La sintaxis genérica para pasar un comando a un contenedor que no se está ejecutando es la siguiente:

```sh
docker container run <image name> <command>
```

Ejecute el siguiente comando en su terminal:

```sh
docker run alpine uname -a
# Linux f08dbbe9199b 5.8.0-22-gener
```

Ejecuté `uname -a` para imprimir los detalles del kernel dentro de un contenedor que ejecuta Alpine Linux.

<p align="right">(<a href="#top">volver arriba</a>)</p>

## Conceptos básicos de manipulación de imágenes de Docker

En esta sección, aprenderá los conceptos básicos para crear imágenes, ejecutar contenedores usándolas y compartirlas en línea.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo crear una imagen acoplable (build)

Para la explicación usaremos el siguiente ejemplo:

Trabajaremos con un administrador de listas de tareas simple que se ejecuta en Node.js. Si no está familiarizado con Node.js, no se preocupe. No se necesita experiencia real en JavaScript.

En este punto, su equipo de desarrollo es bastante pequeño y simplemente está creando una aplicación para probar su MVP (producto mínimo viable). Desea mostrar cómo funciona y qué es capaz de hacer sin tener que pensar en cómo funcionará para un equipo grande, varios desarrolladores, etc.

<div align="center"> 
  <img src="https://docs.docker.com/get-started/images/todo-list-sample.png" alt="screenshot" width="500"/>
</div>

#### Obtén la aplicación

Antes de que podamos ejecutar la aplicación, necesitamos obtener el código fuente de la aplicación en nuestra máquina.

1. Descargue el contenido de la aplicación desde el [repositorio de inicio](https://github.com/docker/getting-started/tree/master) .

2. Una vez extraído diríjase a la carpeta app, use su editor de código favorito para abrir el proyecto. Si necesita un editor, puede usar Visual Studio Code . Debería ver los `package.json` dos subdirectorios `( srcy spec)` .

#### Crea la imagen del contenedor de la aplicación

Para construir la aplicación, necesitamos usar un archivo Dockerfile. Un Dockerfile es simplemente un script de instrucciones basado en texto que se usa para crear una imagen de contenedor. Si ha creado Dockerfiles antes, es posible que vea algunas fallas en el Dockerfile a continuación. Pero no te preocupes. Los repasamos.

1. Cree un archivo con el nombre `Dockerfile` en la misma carpeta que el archivo `package.json` con los siguientes contenidos.

   ```sh
   # syntax=docker/dockerfile:1
   FROM node:12-alpine
   RUN apk add --no-cache python2 g++ make
   WORKDIR /app
   COPY . .
   RUN yarn install --production
   CMD ["node", "src/index.js"]
   EXPOSE 3000
   ```

2. Si aún no lo ha hecho, abra una terminal y vaya al `app` directorio con el archivo `Dockerfile` . Ahora crea la imagen del contenedor usando el `docker build` comando.

   ```sh
   docker build -t getting-started .
   # [+] Building 47.0s (16/16) FINISHED
   #  => [internal] load build definition from Dockerfile                                                                                       0.1s
   #  => => transferring dockerfile: 227B                                                                                                       0.0s
   #  => [internal] load .dockerignore                                                                                                          0.0s
   #  => => transferring context: 2B                                                                                                            0.0s
   #  => resolve image config for docker.io/docker/dockerfile:1                                                                                 3.7s
   #  => [auth] docker/dockerfile:pull token for registry-1.docker.io                                                                           0.0s
   #  => CACHED docker-image://docker.io/docker/dockerfile:1@sha256:443aab4ca21183e069e7d8b2dc68006594f40bddf1b15bbd83f5137bd93e80e2            0.0s
   #  => [internal] load build definition from Dockerfile                                                                                       0.0s
   #  => [internal] load .dockerignore                                                                                                          0.0s
   #  => [internal] load metadata for docker.io/library/node:12-alpine                                                                          2.3s
   #  => [auth] library/node:pull token for registry-1.docker.io                                                                                0.0s
   #  => [1/5] FROM docker.io/library/node:12-alpine@sha256:d4b15b3d48f42059a15bd659be60afe21762aae9d6cbea6f124440895c27db68                    0.0s
   #  => [internal] load build context                                                                                                          0.3s
   #  => => transferring context: 4.62MB                                                                                                        0.2s
   #  => CACHED [2/5] RUN apk add --no-cache python2 g++ make                                                                                   0.0s
   #  => CACHED [3/5] WORKDIR /app                                                                                                              0.0s
   #  => [4/5] COPY . .                                                                                                                         0.3s
   #  => [5/5] RUN yarn install --production                                                                                                   35.9s
   #  => exporting to image                                                                                                                     3.6s
   #  => => exporting layers                                                                                                                    3.6s
   #  => => writing image sha256:58eba0bc3efe3f87537245740ae5aca8b79fd3e58470eb63a541a1495900be31                                               0.0s
   #  => => naming to docker.io/library/getting-started                                                                                         0.0s
   ```

   Este comando usó Dockerfile para crear una nueva imagen de contenedor. Es posible que haya notado que se descargaron muchas "capas". Esto se debe a que le indicamos al constructor que queríamos comenzar desde la `node:12-alpine` imagen. Pero, como no teníamos eso en nuestra máquina, esa imagen necesitaba ser descargada.

   Después de descargar la imagen, la copiamos en nuestra aplicación y la usamos `yarn` para instalar las dependencias de nuestra aplicación. La `CMD`directiva especifica el comando predeterminado que se ejecutará al iniciar un contenedor desde esta imagen.

   Finalmente, la **`-t`** bandera etiqueta nuestra imagen. Piense en esto simplemente como un nombre legible por humanos para la imagen final. Dado que nombramos la imagen `getting-started` , podemos hacer referencia a esa imagen cuando ejecutamos un contenedor.

   El **`.`** al final del `docker build` comando le dice a Docker que debe buscar `Dockerfile` en el directorio actual.

#### Iniciar un contenedor de aplicaciones

Ahora que tenemos una imagen, ejecutemos la aplicación. Para hacerlo, usaremos el `docker run` comando.

1. Inicie su contenedor usando el docker runcomando y especifique el nombre de la imagen que acabamos de crear:

   ```sh
   docker run -dp 3000:3000 getting-started
   ```

¿Recuerdas las banderas `-d` y ? `-p` estamos ejecutando el nuevo contenedor en modo "separado" (en segundo plano) y creando una asignación entre el puerto 3000 del host y el puerto 3000 del contenedor. Sin la asignación de puertos, no podríamos acceder a la aplicación.

2. Después de unos segundos, abra su navegador web en http://localhost:3000 . Deberías ver nuestra aplicación.

<div align="center"> 
  <img src="https://docs.docker.com/get-started/images/todo-list-empty.png" alt="screenshot" width="500"/>
</div>

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo etiquetar imágenes de Docker (-t o --tag)

Al igual que los contenedores, puede asignar identificadores personalizados a sus imágenes en lugar de confiar en la identificación generada aleatoriamente. En el caso de una imagen, se llama etiquetar en lugar de nombrar. La opción `--tag` o `-t` se utiliza en tales casos.

La sintaxis genérica para la opción es la siguiente:

```sh
--tag <image repository>:<image tag>
```

Tome la imagen mysql oficial , por ejemplo. Si desea ejecutar un contenedor con una versión específica de MySQL, como 5.7, puede ejecutar `docker container run mysql:5.7` donde `mysql` es la imagen del repositorio y `5.7` es el tag.

Usaremos el anterior ejemplo para un mejor entendimiento, para etiquetar su imagen `getting-started` puede ejecutar el siguiente comando:

```sh
docker image build -t getting-started:packaded .
# [+] Building 13.5s (16/16) FINISHED
#  => [internal] load build definition from Dockerfile                                                               0.0s
#  => => transferring dockerfile: 227B                                                                               0.0s
#  => [internal] load .dockerignore                                                                                  0.0s
#  => => transferring context: 2B                                                                                    0.0s
#  => resolve image config for docker.io/docker/dockerfile:1                                                        10.2s
#  => [auth] docker/dockerfile:pull token for registry-1.docker.io                                                   0.0s
#  => CACHED docker-image://docker.io/docker/dockerfile:1@sha256:443aab4ca21183e069e7d8b2dc68006594f40bddf1b15bbd83  0.0s
#  => [internal] load build definition from Dockerfile                                                               0.0s
#  => [internal] load .dockerignore                                                                                  0.0s
#  => [internal] load metadata for docker.io/library/node:12-alpine                                                  1.9s
#  => [auth] library/node:pull token for registry-1.docker.io                                                        0.0s
#  => [1/5] FROM docker.io/library/node:12-alpine@sha256:d4b15b3d48f42059a15bd659be60afe21762aae9d6cbea6f124440895c  0.0s
#  => [internal] load build context                                                                                  0.6s
#  => => transferring context: 4.62MB                                                                                0.6s
#  => CACHED [2/5] RUN apk add --no-cache python2 g++ make                                                           0.0s
#  => CACHED [3/5] WORKDIR /app                                                                                      0.0s
#  => CACHED [4/5] COPY . .                                                                                          0.0s
#  => CACHED [5/5] RUN yarn install --production                                                                     0.0s
#  => exporting to image                                                                                             0.1s
#  => => exporting layers                                                                                            0.0s
#  => => writing image sha256:58eba0bc3efe3f87537245740ae5aca8b79fd3e58470eb63a541a1495900be31                       0.0s
#  => => naming to docker.io/library/getting-started:packaded
```

En los casos en los que olvidó etiquetar una imagen durante el tiempo de compilación, o tal vez quiera cambiar la etiqueta, puede usar el `image tag` comando para hacerlo:

```sh
docker image tag <image id> <image repository>:<image tag>

## or ##

docker image tag <image repository>:<image tag> <new image repository>:<new image tag>
```

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo enumerar imágenes de Docker (images o image ls)

Puede usar el `images` comando para enumerar todas las imágenes en su sistema local:

```sh
docker images

# REPOSITORY     TAG        IMAGE ID       CREATED         SIZE
# <none>         <none>     3199372aa3fc   7 seconds ago   132MB
# custom-nginx   packaged   f8837621b99d   4 minutes ago   132MB
```

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo eliminar imágenes de Docker (rmi o image rm)

Las imágenes enumeradas aquí se pueden eliminar con el `image rm` comando. La sintaxis genérica es la siguiente:

```sh
docker image rm <image identifier>
```

- **Eliminar una o más imágenes específicas**

  Utilice el comando `docker images` con el indicador `-a` para localizar el ID de las imágenes que quiere eliminar. Esto le mostrará todas las imágenes, incluidas las capas de imagen intermedias. Cuando localice las imágenes que desee eliminar, puede pasar su ID o etiqueta a `docker rmi` :

  Enumerar:

  ```sh
  docker images -a
  ```

  Eliminar:

  ```sh
  docker rmi Image Image
  ```

- **Eliminar imágenes pendientes**

  Las imágenes de Docker constan de varias capas. Las imágenes pendientes son capas que no tienen relación con imágenes etiquetadas. Ya no sirven para nada y ocupan espacio en el disco. Se pueden ubicar añadiendo el indicador de filtro `-f` junto con el valor `dangling=true` al comando `docker images` . Si está seguro de que quiere eliminarlas, puede utilizar el comando` docker images purge` :

  Enumerar:

  ```sh
  docker images -f dangling=true
  ```

  Eliminar:

  ```sh
  docker images purge
  ```

- **Eliminar todas las imágenes**

  Es posible enumerar todas las imágenes de Docker de un sistema añadiendo `-a` al comando `docker images` . Una vez que esté seguro de que desea eliminarlas por completo, puede añadir el indicador `-q` para pasar el ID de la imagen a `docker rmi` :

  Enumerar:

  ```sh
  docker images -a
  ```

  Eliminar:

  ```sh
  docker rmi $(docker images -a -q)
  ```

  <p align="right">(<a href="#top">volver arriba</a>)</p>

### Usando como imagen base Alpine Linux

Si ha estado jugando con los contenedores desde hace algún tiempo, es posible que haya oído hablar de algo llamado [Alpine Linux](https://alpinelinux.org/). [Es una distribución de Linux](https://en.wikipedia.org/wiki/Linux) con todas las funciones como [Ubuntu](https://ubuntu.com/), [Debian](https://www.debian.org/) o [Fedora](https://getfedora.org/).

Pero lo bueno de Alpine es que está construido alrededor `musl` `libc` y `busybox` es liviano. Mientras que la última imagen de ubuntu pesa alrededor de 28 MB, [alpine](https://hub.docker.com/_/alpine) pesa 2,8 MB.

Además de la naturaleza liviana, Alpine también es seguro y se adapta mucho mejor para crear contenedores que las otras distribuciones.

Aunque no es tan fácil de usar como otras distribuciones comerciales, la transición a Alpine sigue siendo muy sencilla.

Cree un Dockerfile y copie el contenido de la siguiente manera:

```sh
FROM alpine:latest

EXPOSE 80

ARG FILENAME="nginx-1.19.2"
ARG EXTENSION="tar.gz"

ADD https://nginx.org/download/${FILENAME}.${EXTENSION} .

RUN apk add --no-cache pcre zlib && \
    apk add --no-cache \
            --virtual .build-deps \
            build-base \
            pcre-dev \
            zlib-dev \
            openssl-dev && \
    tar -xvf ${FILENAME}.${EXTENSION} && rm ${FILENAME}.${EXTENSION} && \
    cd ${FILENAME} && \
    ./configure \
        --sbin-path=/usr/bin/nginx \
        --conf-path=/etc/nginx/nginx.conf \
        --error-log-path=/var/log/nginx/error.log \
        --http-log-path=/var/log/nginx/access.log \
        --with-pcre \
        --pid-path=/var/run/nginx.pid \
        --with-http_ssl_module && \
    make && make install && \
    cd / && rm -rfv /${FILENAME} && \
    apk del .build-deps

CMD ["nginx", "-g", "daemon off;"]
```

- En lugar de usar `apt-get install` para instalar paquetes, usamos `apk add` . La -`-no-cache` opción significa que el paquete descargado no se almacenará en caché. Del mismo modo, usaremos` apk del` en lugar de `apt-get remove` para desinstalar paquetes.
- La `--virtual` opción para el `apk add` comando se usa para agrupar un grupo de paquetes en un solo paquete virtual para facilitar la administración. Los paquetes que se necesitan solo para construir el programa se etiquetan y `.build-deps` luego se eliminan en la línea 29 al ejecutar el `apk del .build-deps` comando. Puede obtener más información sobre los virtuales en los documentos oficiales.
- Los nombres de los paquetes son un poco diferentes aquí. Por lo general, cada distribución de Linux tiene su repositorio de paquetes disponible para todos donde puede buscar paquetes. Si conoce los paquetes necesarios para una determinada tarea, puede dirigirse al repositorio designado para una distribución y buscarlo. [Puede buscar paquetes de Alpine Linux aquí](https://pkgs.alpinelinux.org/packages).

Ahora cree una nueva imagen usando esto `Dockerfile` y vea la diferencia en el tamaño del archivo:

```sh
docker image build --tag custom-nginx:built .

# Sending build context to Docker daemon  1.055MB
# Step 1/7 : FROM alpine:latest
#  ---> 7731472c3f2a
# Step 2/7 : EXPOSE 80
#  ---> Running in 8336cfaaa48d
# Removing intermediate container 8336cfaaa48d
#  ---> d448a9049d01
# Step 3/7 : ARG FILENAME="nginx-1.19.2"
#  ---> Running in bb8b2eae9d74
# Removing intermediate container bb8b2eae9d74
#  ---> 87ca74f32fbe
# Step 4/7 : ARG EXTENSION="tar.gz"
#  ---> Running in aa09627fe48c
# Removing intermediate container aa09627fe48c
#  ---> 70cb557adb10
# Step 5/7 : ADD https://nginx.org/download/${FILENAME}.${EXTENSION} .
# Downloading [==================================================>]  1.049MB/1.049MB
#  ---> b9790ce0c4d6
# Step 6/7 : RUN apk add --no-cache pcre zlib &&     apk add --no-cache             --virtual .build-deps             build-base             pcre-dev             zlib-dev             openssl-dev &&     tar -xvf ${FILENAME}.${EXTENSION} && rm ${FILENAME}.${EXTENSION} &&     cd ${FILENAME} &&     ./configure         --sbin-path=/usr/bin/nginx         --conf-path=/etc/nginx/nginx.conf         --error-log-path=/var/log/nginx/error.log         --http-log-path=/var/log/nginx/access.log         --with-pcre         --pid-path=/var/run/nginx.pid         --with-http_ssl_module &&     make && make install &&     cd / && rm -rfv /${FILENAME} &&     apk del .build-deps
#  ---> Running in 0b301f64ffc1
### LONG INSTALLATION AND BUILD STUFF GOES HERE ###
# Removing intermediate container 0b301f64ffc1
#  ---> dc7e4161f975
# Step 7/7 : CMD ["nginx", "-g", "daemon off;"]
#  ---> Running in b579e4600247
# Removing intermediate container b579e4600247
#  ---> 3e186a3c6830
# Successfully built 3e186a3c6830
# Successfully tagged custom-nginx:built

docker image ls

# REPOSITORY         TAG       IMAGE ID       CREATED         SIZE
# custom-nginx       built     3e186a3c6830   8 seconds ago   12.8MB
```

Mientras que la versión de ubuntu ocupaba 81,6 MB, la versión alpina se ha reducido a 12,8 MB, lo que supone una gran ganancia. Además del `apk` administrador de paquetes, hay algunas otras cosas que difieren en Alpine de Ubuntu, pero no son tan importantes. Puedes buscar en Internet cada vez que te quedes atascado.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo compartir sus imágenes de Docker en línea

Ahora que sabe cómo hacer imágenes, es hora de compartirlas con el mundo. Compartir imágenes en línea es fácil. Todo lo que necesita es una cuenta en cualquiera de los registros en línea. Usaré [Docker Hub](https://hub.docker.com/) aquí.

Vaya a la página de [registro](https://hub.docker.com/signup) y cree una cuenta gratuita. Una cuenta gratuita le permite alojar repositorios públicos ilimitados y un repositorio privado.

Una vez que haya creado la cuenta, deberá iniciar sesión con la CLI de Docker. Así que abre tu terminal y ejecuta el siguiente comando para hacerlo:

```sh
docker login

# Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
# Username: fhsinchy
# Password:
# WARNING! Your password will be stored unencrypted in /home/fhsinchy/.docker/config.json.
# Configure a credential helper to remove this warning. See
# https://docs.docker.com/engine/reference/commandline/login/#credentials-store
#
# Login Succeeded
```

Se le pedirá su nombre de usuario y contraseña. Si los ingresa correctamente, debe iniciar sesión en su cuenta correctamente.

Para compartir una imagen en línea, la imagen debe estar etiquetada. Ya aprendió sobre el etiquetado en una subsección anterior. Solo para refrescar su memoria, la sintaxis genérica para la opción `--tag` o `-t` es la siguiente

```sh
--tag <image repository>:<image tag>
```

Como ejemplo, compartamos la `custom-nginx` imagen en línea. Para hacerlo, abra una nueva ventana de terminal dentro del `custom-nginx` directorio del proyecto.

Para compartir una imagen en línea, deberá etiquetarla siguiendo la `<docker hub username>/<image name>:<image tag>` sintaxis. Mi nombre de usuario es `fhsinchy` por lo que el comando se verá así:

```sh
docker image build --tag fhsinchy/custom-nginx:latest .

# Step 1/9 : FROM ubuntu:latest
#  ---> d70eaf7277ea
# Step 2/9 : RUN apt-get update &&     apt-get install build-essential                    libpcre3                     libpcre3-dev                     zlib1g                     zlib1g-dev                     libssl-dev                     -y &&     apt-get clean && rm -rf /var/lib/apt/lists/*
#  ---> cbe1ced3da11
### LONG INSTALLATION STUFF GOES HERE ###
# Step 3/9 : ARG FILENAME="nginx-1.19.2"
#  ---> Running in 33b62a0e9ffb
# Removing intermediate container 33b62a0e9ffb
#  ---> fafc0aceb9c8
# Step 4/9 : ARG EXTENSION="tar.gz"
#  ---> Running in 5c32eeb1bb11
# Removing intermediate container 5c32eeb1bb11
#  ---> 36efdf6efacc
# Step 5/9 : ADD https://nginx.org/download/${FILENAME}.${EXTENSION} .
# Downloading [==================================================>]  1.049MB/1.049MB
#  ---> dba252f8d609
# Step 6/9 : RUN tar -xvf ${FILENAME}.${EXTENSION} && rm ${FILENAME}.${EXTENSION}
#  ---> Running in 2f5b091b2125
### LONG EXTRACTION STUFF GOES HERE ###
# Removing intermediate container 2f5b091b2125
#  ---> 2c9a325d74f1
# Step 7/9 : RUN cd ${FILENAME} &&     ./configure         --sbin-path=/usr/bin/nginx         --conf-path=/etc/nginx/nginx.conf         --error-log-path=/var/log/nginx/error.log         --http-log-path=/var/log/nginx/access.log         --with-pcre         --pid-path=/var/run/nginx.pid         --with-http_ssl_module &&     make && make install
#  ---> Running in 11cc82dd5186
### LONG CONFIGURATION AND BUILD STUFF GOES HERE ###
# Removing intermediate container 11cc82dd5186
#  ---> 6c122e485ec8
# Step 8/9 : RUN rm -rf /${FILENAME}}
#  ---> Running in 04102366960b
# Removing intermediate container 04102366960b
#  ---> 6bfa35420a73
# Step 9/9 : CMD ["nginx", "-g", "daemon off;"]
#  ---> Running in 63ee44b571bb
# Removing intermediate container 63ee44b571bb
#  ---> 4ce79556db1b
# Successfully built 4ce79556db1b
# Successfully tagged fhsinchy/custom-nginx:latest
```

En este comando, el f`hsinchy/custom-nginx` es el repositorio de imágenes y `latesct` es la etiqueta. El nombre de la imagen puede ser el que quieras y no se puede cambiar una vez que hayas subido la imagen. La etiqueta se puede cambiar cuando lo desee y, por lo general, refleja la versión del software o diferentes tipos de compilaciones.

Toma la `node` imagen como ejemplo. La `node:lts` imagen se refiere a la versión de soporte a largo plazo de Node.js, mientras que la `node:lts-alpine` versión se refiere a la versión de Node.js creada para Alpine Linux, que es mucho más pequeña que la normal.

Si no asigna ninguna etiqueta a la imagen, se etiquetará automáticamente como `latest` . Pero eso no significa que la `latest` etiqueta siempre hará referencia a la última versión. Si, por algún motivo, etiqueta explícitamente una versión anterior de la imagen como `latest` , entonces Docker no hará ningún esfuerzo adicional para verificarlo.

Una vez que se ha creado la imagen, puede cargarla ejecutando el siguiente comando:

```sh
docker image push <image repository>:<image tag>
```

Así que en mi caso el comando será el siguiente:

```sh
docker image push fhsinchy/custom-nginx:latest

# The push refers to repository [docker.io/fhsinchy/custom-nginx]
# 4352b1b1d9f5: Pushed
# a4518dd720bd: Pushed
# 1d756dc4e694: Pushed
# d7a7e2b6321a: Pushed
# f6253634dc78: Mounted from library/ubuntu
# 9069f84dbbe9: Mounted from library/ubuntu
# bacd3af13903: Mounted from library/ubuntu
# latest: digest: sha256:ffe93440256c9edb2ed67bf3bba3c204fec3a46a36ac53358899ce1a9eee497a size: 1788
```

Dependiendo del tamaño de la imagen, la carga puede demorar algún tiempo. Una vez que haya terminado, debería poder encontrar la imagen en la página de perfil de su hub.

  <p align="right">(<a href="#top">volver arriba</a>)</p>

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

```sh

```

<p align="right">(<a href="#top">volver arriba</a>)</p>
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
