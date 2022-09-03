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
    <li>
      <a href="#cómo-convertir-en-contenedor-una-aplicación-de-javascript">Cómo convertir en contenedor una aplicación de JavaScript</a>
      <ul>
        <li><a href="#cómo-escribir-el-dockerfile-de-desarrollo">Cómo escribir el Dockerfile de desarrollo</a></li>
        <li><a href="#cómo-trabajar-con-montajes-de-enlace-en-docker">Cómo trabajar con montajes de enlace en Docker</a></li>
        <li><a href="#cómo-trabajar-con-volúmenes-anónimos-en-docker">Cómo trabajar con volúmenes anónimos en Docker</a></li>
        <li><a href="#cómo-realizar-compilaciones-de-varias-etapas-en-docker">Cómo realizar compilaciones de varias etapas en Docker</a></li>
        <li><a href="#cómo-ignorar-archivos-innecesarios">Cómo ignorar archivos innecesarios</a></li>
      </ul>
    </li>
    <li>
      <a href="#conceptos-básicos-de-manipulación-de-red-en-docker">Conceptos básicos de manipulación de red en Docker</a>
      <ul>
        <li><a href="#cómo-enumerar-redes-en-docker-network-ls">Cómo enumerar redes en Docker (network ls)</a></li>
        <li><a href="#cómo-crear-un-puente-definido-por-el-usuario-en-docker-network-create">Cómo crear un puente definido por el usuario en Docker (network create)</a></li>
        <li><a href="#cómo-adjuntar-un-contenedor-a-una-red-en-docker">Cómo adjuntar un contenedor a una red en Docker</a></li>
        <li><a href="#cómo-separar-contenedores-de-una-red-en-docker">Cómo separar contenedores de una red en Docker</a></li>
        <li><a href="#cómo-deshacerse-de-las-redes-en-docker-network-rm">Cómo deshacerse de las redes en Docker (network rm)</a></li>
      </ul>
    </li>
    <li>
      <a href="#cómo-convertir-en-contenedor-una-aplicación-de-javascript-de-varios-contenedores">Cómo convertir en contenedor una aplicación de JavaScript de varios contenedores</a>
      <ul>
        <li><a href="#cómo-ejecutar-el-servidor-de-base-de-datos">Cómo ejecutar el servidor de base de datos</a></li>
        <li>
          <a href="#cómo-trabajar-con-volúmenes-con-nombre-en-docker">Cómo trabajar con volúmenes con nombre en Docker</a>
          <ul>
            <li><a href="#comó-crear-un-volúmen-volume-create">Comó crear un volúmen  (volume create)</a></li>
            <li><a href="#cómo-enumerar-volúmenes-volumen-ls">Cómo enumerar volúmenes (volumen ls)</a></li>
            <li><a href="#cómo-adjuntar-un-volúmen-a-un-contenedor-en-docker--v">Cómo adjuntar un volúmen a un contenedor en Docker (-v)</a></li>
            <li><a href="#cómo-eliminar-volúmenes-volume-rm">Cómo eliminar volúmenes (volume rm)</a></li>
          </ul>
        </li>
        <li><a href="#cómo-acceder-a-los-registros-desde-un-contenedor-en-docker-logs">Cómo acceder a los registros desde un contenedor en Docker (logs)</a></li>
        <li><a href="#ejemplo-práctico">Ejemplo práctico</a></li>
        <li><a href="#cómo-ejecutar-comandos-en-un-contenedor-en-ejecución-exec">Cómo ejecutar comandos en un contenedor en ejecución (exec)</a></li>
        <li><a href="#"></a></li>
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

2. Una vez extraído diríjase a la carpeta app, use su editor de código favorito para abrir el proyecto. Si necesita un editor, puede usar Visual Studio Code . Debería ver los `package.json` dos subdirectorios (`src` y `spec`).

#### Crea la imagen del contenedor de la aplicación

Para construir la aplicación, necesitamos usar un archivo Dockerfile. Un Dockerfile es simplemente un script de instrucciones basado en texto que se usa para crear una imagen de contenedor.

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

   Después de descargar la imagen, la copiamos en nuestra aplicación y usamos `yarn` para instalar las dependencias de nuestra aplicación. La `CMD`directiva especifica el comando predeterminado que se ejecutará al iniciar un contenedor desde esta imagen.

   Finalmente, la **`-t`** bandera etiqueta nuestra imagen. Piense en esto simplemente como un nombre legible por humanos para la imagen final. Dado que nombramos la imagen `getting-started` , podemos hacer referencia a esa imagen cuando ejecutamos un contenedor.

   El **`.`** al final del `docker build` comando le dice a Docker que debe buscar `Dockerfile` en el directorio actual.

#### Iniciar un contenedor de aplicaciones

Ahora que tenemos una imagen, ejecutemos la aplicación. Para hacerlo, usaremos el `docker run` comando.

1. Inicie su contenedor usando el docker runcomando y especifique el nombre de la imagen que acabamos de crear:

   ```sh
   docker run -dp 3000:3000 getting-started
   ```

¿Recuerdas las banderas `-d` y `-p` ? estamos ejecutando el nuevo contenedor en modo "separado" (en segundo plano) y creando una asignación entre el puerto 3000 del host y el puerto 3000 del contenedor. Sin la asignación de puertos, no podríamos acceder a la aplicación.

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

Tome la imagen `mysql` oficial, por ejemplo. Si desea ejecutar un contenedor con una versión específica de MySQL, como 5.7, puede ejecutar `docker container run mysql:5.7` donde `mysql` es la imagen del repositorio y `5.7` es el tag.

Usaremos el anterior ejemplo para un mejor entendimiento, para etiquetar su imagen `getting-started` puede ejecutar el siguiente comando:

```sh
docker image build -t getting-started:v1.0 .
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

  Las imágenes de Docker constan de varias capas. Las imágenes pendientes son capas que no tienen relación con imágenes etiquetadas. Ya no sirven para nada y ocupan espacio en el disco. Se pueden ubicar añadiendo el indicador de filtro `-f` junto con el valor `dangling=true` al comando `docker images` . Si está seguro de que quiere eliminarlas, puede utilizar el comando` docker image prune` :

  Enumerar:

  ```sh
  docker images -f dangling=true
  ```

  Eliminar:

  ```sh
  docker image prune -f
  ```

  La opción `--force` o `-f` salta cualquier pregunta de confirmación. También puede usar la opción `--all` o `-a`para eliminar todas las imágenes almacenadas en caché en su registro local.

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

Ahora cree una nueva imagen usando las configuraciones del `Dockerfile` creado.

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

En este comando, el `fhsinchy/custom-nginx` es el repositorio de imágenes y `latest` es la etiqueta. El nombre de la imagen puede ser el que quieras y no se puede cambiar una vez que hayas subido la imagen. La etiqueta se puede cambiar cuando lo desee y, por lo general, refleja la versión del software o diferentes tipos de compilaciones.

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

## Cómo convertir en contenedor una aplicación de JavaScript

En esta subsección, trabajará con el código fuente del [repositorio](https://github.com/fhsinchy/docker-handbook-projects). En el proceso de contenedorización de esta aplicación muy simple, se le presentarán los volúmenes y las compilaciones de varias etapas, dos de los conceptos más importantes de Docker.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo escribir el Dockerfile de desarrollo

Para empezar, abra el directorio donde ha clonado el repositorio que viene con este libro. El código de la `hello-dock` aplicación reside dentro del subdirectorio, este es un proyecto de JavaScript muy simple impulsado por el proyecto vitejs/vite .

Acontinuación cree una nueva `Dockerfile.dev` dentro `hello-dock` del directorio de su proyecto y coloque el siguiente contenido en él:

```sh
FROM node:lts-alpine

EXPOSE 3000

USER node

RUN mkdir -p /home/node/app

WORKDIR /home/node/app

COPY ./package.json .
RUN npm install

COPY . .

CMD [ "npm", "run", "dev" ]
```

La explicación de este código es la siguiente:

- Las `FROM` instrucciones aquí establecen la imagen oficial de Node.js como base, brindándole todas las bondades de Node.js necesarias para ejecutar cualquier aplicación de JavaScript. La `lts-alpine` etiqueta indica que desea utilizar la variante Alpine, versión de soporte a largo plazo de la imagen. Las etiquetas disponibles y la documentación necesaria para la imagen se pueden encontrar en la página del centro de [nodos](https://hub.docker.com/_/node) .

- La `USER` instrucción establece el usuario predeterminado para la imagen en `node`. De forma predeterminada, Docker ejecuta contenedores como usuario raíz. Pero según las [mejores prácticas de Docker y Node.js](https://github.com/nodejs/docker-node/blob/main/docs/BestPractices.md), esto puede representar una amenaza para la seguridad. Por lo tanto, es una mejor idea ejecutar como usuario no root siempre que sea posible. La imagen del nodo viene con un nombre de usuario no raíz `node` que puede establecer como el usuario predeterminado usando la `USER` instrucción.

- La `RUN mkdir -p /home/node/app` instrucción crea un directorio llamado `app` dentro del directorio de inicio del `node` usuario. El directorio de inicio para cualquier usuario que no sea root en Linux suele ser `/home/<user name>` el predeterminado.

- Luego, la `WORKDIR` instrucción establece el directorio de trabajo predeterminado en el directorio recién creado `/home/node/app` . Por defecto, el directorio de trabajo de cualquier imagen es la raíz. No desea que se rocíen archivos innecesarios en todo su directorio raíz, ¿verdad? Por lo tanto, cambia el directorio de trabajo predeterminado a algo más sensato `/home/node/app` o lo que quiera. Este directorio de trabajo será aplicable a cualquier instrucción , `COPY` y `ADD` .

- La `COPY` instrucción aquí copia el `package.json` archivo que contiene información sobre todas las dependencias necesarias para esta aplicación. La `RUN` instrucción ejecuta el `npm install` comando, que es el comando predeterminado para instalar dependencias mediante un `package.json` archivo en los proyectos de Node.js. El `.` al final representa el directorio de trabajo.

- La segunda `COPY` instrucción copia el resto del contenido del directorio actual ( `.` ) del sistema de archivos host al directorio de trabajo ( `.` ) dentro de la imagen.

- Finalmente, la `CMD` instrucción aquí establece el comando predeterminado para esta imagen que está `npm run dev` escrita en `exec` forma.

- El `vite` servidor de desarrollo se ejecuta de forma predeterminada en el puerto `3000` , y agregar un `EXPOSE` comando parecía una buena idea, así que ya está.

Ahora, para construir una imagen a partir de esto `Dockerfile.dev` , puede ejecutar el siguiente comando:

```sh
docker image build --file Dockerfile.dev --tag hello-dock:dev .

# Step 1/7 : FROM node:lts
#  ---> b90fa0d7cbd1
# Step 2/7 : EXPOSE 3000
#  ---> Running in 722d639badc7
# Removing intermediate container 722d639badc7
#  ---> e2a8aa88790e
# Step 3/7 : WORKDIR /app
#  ---> Running in 998e254b4d22
# Removing intermediate container 998e254b4d22
#  ---> 6bd4c42892a4
# Step 4/7 : COPY ./package.json .
#  ---> 24fc5164a1dc
# Step 5/7 : RUN npm install
#  ---> Running in 23b4de3f930b
### LONG INSTALLATION STUFF GOES HERE ###
# Removing intermediate container 23b4de3f930b
#  ---> c17ecb19a210
# Step 6/7 : COPY . .
#  ---> afb6d9a1bc76
# Step 7/7 : CMD [ "npm", "run", "dev" ]
#  ---> Running in a7ff529c28fe
# Removing intermediate container a7ff529c28fe
#  ---> 1792250adb79
# Successfully built 1792250adb79
# Successfully tagged hello-dock:dev
```

Dado que el nombre del archivo no es `Dockerfile`, debe pasar explícitamente el nombre del archivo usando la `--file` opción. Se puede ejecutar un contenedor usando esta imagen ejecutando el siguiente comando:

```sh
docker container run --rm -dp 3000:3000 --name hello-dock-dev hello-dock:dev

# 21b9b1499d195d85e81f0e8bce08f43a64b63d589c5f15cbbd0b9c0cb07ae268
```

Ahora visite http://127.0.0.1:3000 para ver la `hello-dock` aplicación en acción.

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/size/w1600/2021/01/hello-dock-dev.png" alt="screenshot"/>
</div>

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo trabajar con montajes de enlace en Docker

Si ha trabajado anteriormente con algún marco de JavaScript front-end, debe saber que los servidores de desarrollo en estos marcos generalmente vienen con una función de recarga en caliente. Es decir, si realiza un cambio en su código, el servidor se volverá a cargar, reflejando automáticamente cualquier cambio que haya realizado de inmediato.

Pero si realiza algún cambio en su código en este momento, no verá que su aplicación se ejecute en el navegador. Esto se debe a que está realizando cambios en el código que tiene en su sistema de archivos local, pero la aplicación que está viendo en el navegador reside dentro del sistema de archivos del contenedor.

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/2021/01/local-vs-container-file-system.svg" alt="screenshot"/>
</div>

Para resolver este problema, puede volver a utilizar un montaje de enlace . Con los montajes de enlace, puede montar fácilmente uno de los directorios de su sistema de archivos local dentro de un contenedor. En lugar de hacer una copia del sistema de archivos local, el montaje de enlace puede hacer referencia al sistema de archivos local directamente desde el interior del contenedor.

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/2021/01/bind-mounts.svg" alt="screenshot"/>
</div>

De esta manera, cualquier cambio que realice en su código fuente local se reflejará inmediatamente dentro del contenedor, activando la función de recarga en caliente del `vite` servidor de desarrollo. Los cambios realizados en el sistema de archivos dentro del contenedor también se reflejarán en su sistema de archivos local.

Los montajes de enlace se pueden crear usando la opción `--volume` o `-v` para los comandos `conatiner run` o `container start`. Solo para recordarle, la sintaxis genérica es la siguiente:

```sh
--volume <local file system directory absolute path>:<container file system directory absolute path>:<read write access>
```

Detenga su `hello-dock-dev` contenedor previamente iniciado e inicie un nuevo contenedor ejecutando el siguiente comando:

```sh
docker container run --rm -p 3000:3000 --name hello-dock-dev -v $(pwd):/home/node/app hello-dock:dev

# sh: 1: vite: not found
# npm ERR! code ELIFECYCLE
# npm ERR! syscall spawn
# npm ERR! file sh
# npm ERR! errno ENOENT
# npm ERR! hello-dock@0.0.0 dev: `vite`
# npm ERR! spawn ENOENT
# npm ERR!
# npm ERR! Failed at the hello-dock@0.0.0 dev script.
# npm ERR! This is probably not a problem with npm. There is likely additional logging output above.
# npm WARN Local package.json exists, but node_modules missing, did you mean to install?
```

Tenga en cuenta que `$(pwd) en linux` o `${PWD} en windows` almacena la ruta del directorio actual. Como puede ver, la aplicación no se está ejecutando en absoluto ahora.

Eso es porque aunque el uso de un volumen resuelve el problema de las recargas en caliente, presenta otro problema. Si tiene alguna experiencia previa con Node.js, puede saber que las dependencias de un proyecto de Node.js viven dentro del `node_modules` directorio en la raíz del proyecto.

Ahora que está montando la raíz del proyecto en su sistema de archivos local como un volumen dentro del contenedor, el contenido dentro del contenedor se reemplaza junto con el `node_modules` directorio que contiene todas las dependencias. Esto significa que el `vite` paquete ha desaparecido.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo trabajar con volúmenes anónimos en Docker

Este problema se puede resolver utilizando un volumen anónimo. Un volumen anónimo es idéntico a un montaje de enlace, excepto que no necesita especificar el directorio de origen aquí. La sintaxis genérica para crear un volumen anónimo es la siguiente:

```sh
--volume <container file system directory absolute path>:<read write access>
```

Entonces, el comando final para iniciar el `hello-dock` contenedor con ambos volúmenes debería ser el siguiente:

```sh
docker container run --rm -dp 3000:3000 --name hello-dock-dev -v $(pwd):/home/node/app -v /home/node/app/node_modules hello-dock:dev

# 53d1cfdb3ef148eb6370e338749836160f75f076d0fbec3c2a9b059a8992de8b
```

Aquí, Docker tomará todo el `node_modules` directorio desde el interior del contenedor y lo guardará en algún otro directorio administrado por el demonio de Docker en su sistema de archivos host y montará ese directorio como `node_modules` dentro del contenedor.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo realizar compilaciones de varias etapas en Docker

Si desea construir la imagen en modo de producción, aparecen algunos desafíos nuevos.

En el modo de desarrollo, el `npm run serve` comando inicia un servidor de desarrollo que sirve la aplicación al usuario. Ese servidor no solo sirve los archivos, sino que también proporciona la función de recarga en caliente.

En el modo de producción, el `npm run build` comando compila todo su código JavaScript en algunos archivos HTML, CSS y JavaScript estáticos. Para ejecutar estos archivos, no necesita node ni ninguna otra dependencia de tiempo de ejecución. Todo lo que necesitas es un servidor como `nginx` por ejemplo.

Para crear una imagen donde la aplicación se ejecuta en modo de producción, puede seguir los siguientes pasos:

- Use `node` como imagen base y cree la aplicación.
- Instále `nginx` dentro de la imagen del node y utilícelo para servir los archivos estáticos.
- Cree la imagen final basada en `nginx` y descarte todo `node` lo relacionado.

De esta manera, su imagen solo contiene los archivos que se necesitan y se vuelve realmente útil.

Este enfoque es una construcción de varias etapas. Para realizar una compilación de este tipo, cree una nueva `Dockerfile` dentro `hello-dock` del directorio de su proyecto y coloque el siguiente contenido en él:

```sh
FROM node:lts-alpine as builder

WORKDIR /app

COPY ./package.json ./
RUN npm install

COPY . .
RUN npm run build

FROM nginx:stable-alpine

EXPOSE 80

COPY --from=builder /app/dist /usr/share/nginx/html
```

Como puede ver, se `Dockerfile` parece mucho a los anteriores con algunas rarezas. La explicación de este archivo es la siguiente:

- La línea 1 inicia la primera etapa de la compilación utilizando `node:lts-alpine` como imagen base. La `as builder` sintaxis asigna un nombre a esta etapa para que se pueda hacer referencia a ella más adelante.
- Desde la línea 3 hasta la línea 9, son cosas estándar que has visto muchas veces antes. El `RUN npm run build` comando en realidad compila toda la aplicación y la mete dentro del `/app/dist` directorio donde `/app` está el directorio de trabajo y `/dist` es el directorio de salida predeterminado para `vite` las aplicaciones.
- La línea 11 inicia la segunda etapa de la construcción utilizando `nginx:stable-alpine` como imagen base.
- El servidor NGINX se ejecuta en el puerto 80 de forma predeterminada, por lo que `EXPOSE 80` se agrega la línea.
- La última línea es una `COPY` instrucción. La `--from=builder` parte indica que desea copiar algunos archivos del `builder` escenario. Después de eso, es una instrucción de copia estándar donde `/app/dist` está la fuente y /`usr/share/nginx/html` el destino. El destino utilizado aquí es la ruta del sitio predeterminado para NGINX, por lo que cualquier archivo estático que coloque allí se entregará automáticamente.

Como puede ver, la imagen resultante es una `nginx` imagen base que contiene solo los archivos necesarios para ejecutar la aplicación. Para construir esta imagen, ejecute el siguiente comando:

```sh
docker image build --tag hello-dock:prod .

# Step 1/9 : FROM node:lts-alpine as builder
#  ---> 72aaced1868f
# Step 2/9 : WORKDIR /app
#  ---> Running in e361c5c866dd
# Removing intermediate container e361c5c866dd
#  ---> 241b4b97b34c
# Step 3/9 : COPY ./package.json ./
#  ---> 6c594c5d2300
# Step 4/9 : RUN npm install
#  ---> Running in 6dfabf0ee9f8
# npm WARN deprecated fsevents@2.1.3: Please update to v 2.2.x
#
# > esbuild@0.8.29 postinstall /app/node_modules/esbuild
# > node install.js
#
# npm notice created a lockfile as package-lock.json. You should commit this file.
# npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@~2.1.2 (node_modules/chokidar/node_modules/fsevents):
# npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.1.3: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})
# npm WARN hello-dock@0.0.0 No description
# npm WARN hello-dock@0.0.0 No repository field.
# npm WARN hello-dock@0.0.0 No license field.
#
# added 327 packages from 301 contributors and audited 329 packages in 35.971s
#
# 26 packages are looking for funding
#   run `npm fund` for details
#
# found 0 vulnerabilities
#
# Removing intermediate container 6dfabf0ee9f8
#  ---> 21fd1b065314
# Step 5/9 : COPY . .
#  ---> 43243f95bff7
# Step 6/9 : RUN npm run build
#  ---> Running in 4d918cf18584
#
# > hello-dock@0.0.0 build /app
# > vite build
#
# - Building production bundle...
#
# [write] dist/index.html 0.39kb, brotli: 0.15kb
# [write] dist/_assets/docker-handbook-github.3adb4865.webp 12.32kb
# [write] dist/_assets/index.eabcae90.js 42.56kb, brotli: 15.40kb
# [write] dist/_assets/style.0637ccc5.css 0.16kb, brotli: 0.10kb
# - Building production bundle...
#
# Build completed in 1.71s.
#
# Removing intermediate container 4d918cf18584
#  ---> 187fb3e82d0d
# Step 7/9 : EXPOSE 80
#  ---> Running in b3aab5cf5975
# Removing intermediate container b3aab5cf5975
#  ---> d6fcc058cfda
# Step 8/9 : FROM nginx:stable-alpine
# stable: Pulling from library/nginx
# 6ec7b7d162b2: Already exists
# 43876acb2da3: Pull complete
# 7a79edd1e27b: Pull complete
# eea03077c87e: Pull complete
# eba7631b45c5: Pull complete
# Digest: sha256:2eea9f5d6fff078ad6cc6c961ab11b8314efd91fb8480b5d054c7057a619e0c3
# Status: Downloaded newer image for nginx:stable
#  ---> 05f64a802c26
# Step 9/9 : COPY --from=builder /app/dist /usr/share/nginx/html
#  ---> 8c6dfc34a10d
# Successfully built 8c6dfc34a10d
# Successfully tagged hello-dock:prod
```

Una vez que se haya creado la imagen, puede ejecutar un nuevo contenedor ejecutando el siguiente comando:

```sh
 docker container run --rm --name hello-dock-prod -dp 8080:80 hello-dock:prod

# 224aaba432bb09aca518fdd0365875895c2f5121eb668b2e7b2d5a99c019b953
```

La aplicación en ejecución debe estar disponible en http://127.0.0.1:8080:

<div align="center"> 
  <img src="https://www.freecodecamp.org/news/content/images/size/w1600/2021/01/hello-dock.png" alt="screenshot"/>
</div>

Las compilaciones de varias etapas pueden ser muy útiles si está creando aplicaciones grandes con muchas dependencias. Si se configura correctamente, las imágenes creadas en varias etapas pueden optimizarse y compactarse mucho.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo ignorar archivos innecesarios

El `.dockerignore` archivo contiene una lista de archivos y directorios que se excluirán de las compilaciones de imágenes. Puede encontrar un `.dockerignore` archivo creado previamente en el `hello-dock` directorio.

```sh
.git
*Dockerfile*
*docker-compose*
node_modules
```

Este `.dockerignore` archivo tiene que estar en el contexto de compilación. Los archivos y directorios mencionados aquí serán ignorados por la `COPY` instrucción. Pero si realiza un montaje de vinculación, el `.dockerignore` archivo no tendrá ningún efecto.

<p align="right">(<a href="#top">volver arriba</a>)</p>

## Conceptos básicos de manipulación de red en Docker

Una red en Docker es otro objeto lógico como un contenedor y una imagen. Al igual que los otros dos, hay una gran cantidad de comandos en el `docker network` grupo para manipular redes.

Antes de comenzar me gustaría tomarme un tiempo para analizar la red de puente predeterminada que viene con Docker. Comencemos enumerando todas las redes en su sistema:

```sh
docker network ls

# NETWORK ID     NAME      DRIVER    SCOPE
# c2e59f2b96bd   bridge    bridge    local
# 124dccee067f   host      host      local
# 506e3822bf1f   none      null      local
```

Como puede ver, Docker viene con una red puente predeterminada llamada `bridge` . Cualquier contenedor que ejecute se adjuntará automáticamente a esta red puente:

```sh
docker container run --rm --detach --name hello-dock --publish 8080:80 fhsinchy/hello-dock
# a37f723dad3ae793ce40f97eb6bb236761baa92d72a2c27c24fc7fda0756657d

docker network inspect --format='{{range .Containers}} {{.Name}} {{end}}' bridge
# hello-dock
```

Los contenedores conectados a la red de puente predeterminada pueden comunicarse entre sí mediante direcciones IP que es desaconsejado ya que la IP puede cambiar cada vez que creemos o eliminemos el contenedor, la mejor solución es conectarlas colocándolas bajo una red puente definida por el usuario.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo enumerar redes en Docker (network ls)

Para enumerar las redes en su sistema, ejecute el siguiente comando:

```sh
docker network ls

# NETWORK ID     NAME      DRIVER    SCOPE
# c2e59f2b96bd   bridge    bridge    local
# 124dccee067f   host      host      local
# 506e3822bf1f   none      null      local
```

Debería ver tres redes en su sistema. Ahora mire la `DRIVER` columna de la tabla aquí. Estos controladores se pueden tratar como el tipo de red.

De forma predeterminada, Docker tiene cinco controladores de red. Son los siguientes:

- `bridge` - El controlador de red predeterminado en Docker. Esto se puede usar cuando varios contenedores se ejecutan en modo estándar y necesitan comunicarse entre sí.
- `host` - Elimina el aislamiento de la red por completo. Cualquier contenedor que se ejecuta en una `host` red está básicamente conectado a la red del sistema host.
- `none` - Este controlador deshabilita la red para contenedores por completo. Todavía no he encontrado ningún caso de uso para esto.
- `overlay` - Esto se usa para conectar múltiples demonios Docker entre computadoras.
- ` macvlan` - Permite asignar direcciones MAC a contenedores, haciéndolos funcionar como dispositivos físicos en una red.

También hay complementos de terceros que le permiten integrar Docker con pilas de red especializadas.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo crear un puente definido por el usuario en Docker (network create)

Se puede crear una red usando el `network create` comando. La sintaxis genérica del comando es la siguiente:

```sh
docker network create <network name>
```

Para crear una red con el nombre skynetejecute el siguiente comando:

```sh
docker network create skynet

# 7bd5f351aa892ac6ec15fed8619fc3bbb95a7dcdd58980c28304627c8f7eb070

docker network ls

# NETWORK ID     NAME     DRIVER    SCOPE
# be0cab667c4b   bridge   bridge    local
# 124dccee067f   host     host      local
# 506e3822bf1f   none     null      local
# 7bd5f351aa89   skynet   bridge    local
```

Como puede ver, se ha creado una nueva red con el nombre dado. Actualmente no hay ningún contenedor conectado a esta red. En la siguiente subsección, aprenderá a adjuntar contenedores a una red.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo adjuntar un contenedor a una red en Docker

Hay principalmente dos formas de adjuntar un contenedor a una red. Primero, puede usar el comando de conexión de red para adjuntar un contenedor a una red. La sintaxis genérica del comando es la siguiente:

```sh
docker network connect <network identifier> <container identifier>
```

Para conectar el `hello-dock` contenedor a la `skynet` red, puede ejecutar el siguiente comando:

```sh
docker network connect skynet hello-dock

docker network inspect --format='{{range .Containers}} {{.Name}} {{end}}' skynet

#  hello-dock

docker network inspect --format='{{range .Containers}} {{.Name}} {{end}}' bridge

#  hello-dock
```

Como puede ver en los resultados de los dos `network inspect` comandos, el `hello-dock` contenedor ahora está conectado tanto a la red `skynet` como a la predeterminada `bridge` .

La segunda forma de adjuntar un contenedor a una red es usando la `--network` opción para los comandos `container run` o . `container create` la sintaxis genérica de la opción es la siguiente:

```sh
--network <network identifier>
```

Para ejecutar otro `hello-dock` contenedor conectado a la misma red, puede ejecutar el siguiente comando:

```sh
docker container run --network skynet --rm --name alpine-box -it alpine sh

# lands you into alpine linux shell

/ # ping hello-dock

# PING hello-dock (172.18.0.2): 56 data bytes
# 64 bytes from 172.18.0.2: seq=0 ttl=64 time=0.191 ms
# 64 bytes from 172.18.0.2: seq=1 ttl=64 time=0.103 ms
# 64 bytes from 172.18.0.2: seq=2 ttl=64 time=0.139 ms
# 64 bytes from 172.18.0.2: seq=3 ttl=64 time=0.142 ms
# 64 bytes from 172.18.0.2: seq=4 ttl=64 time=0.146 ms
# 64 bytes from 172.18.0.2: seq=5 ttl=64 time=0.095 ms
# 64 bytes from 172.18.0.2: seq=6 ttl=64 time=0.181 ms
# 64 bytes from 172.18.0.2: seq=7 ttl=64 time=0.138 ms
# 64 bytes from 172.18.0.2: seq=8 ttl=64 time=0.158 ms
# 64 bytes from 172.18.0.2: seq=9 ttl=64 time=0.137 ms
# 64 bytes from 172.18.0.2: seq=10 ttl=64 time=0.145 ms
# 64 bytes from 172.18.0.2: seq=11 ttl=64 time=0.138 ms
# 64 bytes from 172.18.0.2: seq=12 ttl=64 time=0.085 ms

--- hello-dock ping statistics ---
13 packets transmitted, 13 packets received, 0% packet loss
round-trip min/avg/max = 0.085/0.138/0.191 ms
```

Como puede ver, la ejecución `ping hello-dock` desde el interior del `alpine-box` contenedor funciona porque ambos contenedores están bajo la misma red de puente definida por el usuario y la resolución automática de DNS está funcionando.

Tenga en cuenta, sin embargo, que para que funcione la resolución automática de DNS, debe asignar nombres personalizados a los contenedores. Usar el nombre generado aleatoriamente no funcionará.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo separar contenedores de una red en Docker

Puede utilizar el `network disconnect` comando para esta tarea. La sintaxis genérica del comando es la siguiente:

```sh
docker network disconnect <network identifier> <container identifier>
```

Para desconectar el `hello-dock` contenedor de la `skynet` red, puede ejecutar el siguiente comando:

```sh
docker network disconnect skynet hello-dock
```

Al igual que el `network connect` comando, el `network disconnect` comando no da ningún resultado.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo deshacerse de las redes en Docker (network rm)

Al igual que los demás objetos lógicos de Docker, las redes se pueden eliminar con el `network rm` comando. La sintaxis genérica del comando es la siguiente:

```sh
docker network rm <network identifier>
```

Para eliminar la `skynet` red de su sistema, puede ejecutar el siguiente comando:

```sh
docker network rm skynet
```

También puede usar el `network prune` comando para eliminar cualquier red no utilizada de su sistema. El comando también tiene las opciones `-f` o `--force` .

```sh
docker network prune
```

<p align="right">(<a href="#top">volver arriba</a>)</p>

## Cómo convertir en contenedor una aplicación de JavaScript de varios contenedores

En esta sección aprenderá a contener un proyecto completo de varios contenedores. El proyecto con el que se trabajará es simple con la `notes-api` tecnología de Express.js y PostgreSQL.

En este proyecto hay dos contenedores en total que tendrás que conectar usando una red. Aparte de esto, también se dara a conocer sobre conceptos como variables de entorno y volúmenes con nombre.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo ejecutar el servidor de base de datos

El servidor de la base de datos en este proyecto es un servidor PostgreSQL simple y utiliza la [imagen oficial de Postgres](https://hub.docker.com/_/postgres) .

Según los documentos oficiales, para ejecutar un contenedor con esta imagen, debe proporcionar la `POSTGRES_PASSWORD` **variable de entorno**. Además de este, también proporcionaré un nombre para la base de datos predeterminada utilizando la `POSTGRES_DB` variable de entorno. PostgreSQL de forma predeterminada escucha en el puerto `5432` , por lo que también debe publicarlo.

Para ejecutar el servidor de base de datos puede ejecutar el siguiente comando:

```sh
docker container run \
    --detach \
    --name=notes-db \
    --env POSTGRES_DB=notesdb \
    --env POSTGRES_PASSWORD=secret \
    --network=notes-api-network \
    postgres:12

# a7b287d34d96c8e81a63949c57b83d7c1d71b5660c87f5172f074bd1606196dc

docker container ls

# CONTAINER ID   IMAGE         COMMAND                  CREATED              STATUS              PORTS      NAMES
# a7b287d34d96   postgres:12   "docker-entrypoint.s…"   About a minute ago   Up About a minute   5432/tcp   notes-db
```

La `--env` o `-e` opción para los comandos `container run` y `container create` se puede usar para proporcionar variables de entorno a un contenedor. Como puede ver, el contenedor de la base de datos se ha creado correctamente y ahora se está ejecutando.

Aunque el contenedor se está ejecutando, hay un pequeño problema. Las bases de datos como PostgreSQL, MongoDB y MySQL conservan sus datos en un directorio. PostgreSQL usa el `/var/lib/postgresql/data` directorio dentro del contenedor para conservar los datos.

Ahora, ¿qué pasa si el contenedor se destruye por alguna razón? Perderás todos tus datos. Para resolver este problema, se puede utilizar un volumen con nombre.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo trabajar con volúmenes con nombre en Docker

Un volumen con nombre es muy similar a un volumen anónimo excepto que puede hacer referencia a un volumen con nombre usando su nombre.

<p align="right">(<a href="#top">volver arriba</a>)</p>

#### Comó crear un volúmen (volume create)

El `volume create` comando se puede utilizar para crear un volumen con nombre.

La sintaxis genérica del comando es la siguiente:

```sh
docker volume create <volume name>
```

Para crear un volumen llamado `notes-db-data` puede ejecutar el siguiente comando:

```sh
docker volume create notes-db-data

# notes-db-data

```

<p align="right">(<a href="#top">volver arriba</a>)</p>

#### Cómo enumerar volúmenes (volumen ls)

Para listar listar los volúmenes creados puede ejecutar el siguiente comando:

```sh
docker volume ls

# DRIVER    VOLUME NAME
# local     notes-db-data
```

<p align="right">(<a href="#top">volver arriba</a>)</p>

#### Cómo adjuntar un volúmen a un contenedor en Docker (-v)

Este volumen ahora se puede montar `/var/lib/postgresql/data` en el interior del `notes-db` contenedor.

Ahora ejecute un nuevo contenedor y asigne el volumen usando la opción `--volume` o `-v` :

```sh
docker container run \
    -d \
    -v notes-db-data:/var/lib/postgresql/data \
    --name=notes-db \
    -e POSTGRES_DB=notesdb \
    -e POSTGRES_PASSWORD=secret \
    postgres:12

# 37755e86d62794ed3e67c19d0cd1eba431e26ab56099b92a3456908c1d346791
```

Ahora inspeccione el `notes-db` contenedor para asegurarse de que el montaje fue exitoso:

```sh
docker container inspect --format='{{range .Mounts}} {{ .Name }} {{end}}' notes-db

#  notes-db-data
```

Ahora los datos se almacenarán de forma segura dentro del `notes-db-data` volumen y se podrán reutilizar en el futuro. También se puede usar un montaje de enlace en lugar de un volumen con nombre, pero prefiero un volumen con nombre en tales escenarios.

<p align="right">(<a href="#top">volver arriba</a>)</p>

#### Cómo eliminar volúmenes (volume rm)

- **Eliminar uno o más volúmenes específicos**

  Puede eliminar uno o más volúmenes con el comando docker volume rm:

  ```sh
  docker volume rm volume_name volume_name
  ```

- **Eliminar volúmenes pendientes**
  Debido a que el punto de volúmenes debe existir independientemente de los contenedores, cuando se elimina un contenedor un volumen no se elimina automáticamente al mismo tiempo. Cuando un volumen existe y ya no está conectado a ningún contenedor, se denomina “volumen pendiente”. Para ubicarlos y confirmar que desea eliminarlos, puede utilizar el comando `docker volume ls` con un filtro a fin de limitar los resultados a volúmenes pendientes. Cuando esté conforme con la lista, puede eliminarlos con `docker volume prune`:

  Enumerar:

  ```sh
  docker volume ls -f dangling=true
  ```

  Eliminar:

  ```sh
  docker volume prune
  ```

- **Eliminar un contenedor y su volumen**
  Si creó un volumen sin nombre, puede eliminarlo al mismo tiempo que el contenedor utilizando el indicador `-v`. Tenga en cuenta que esto solo funciona con volúmenes sin nombre. Cuando el contenedor se elimina correctamente, se muestra su ID. Tenga en cuenta que no se hace referencia a la eliminación del volumen. Si no tiene nombre, se elimina silenciosamente del sistema. Si se nombra, permanece silenciosamente presente.

  Eliminar:

  ```sh
  docker rm -v container_name
  ```

  <p align="right">(<a href="#top">volver arriba</a>)</p>

## Cómo acceder a los registros desde un contenedor en Docker (logs)

Para ver los registros de un contenedor, puede usar el `container logs` comando. La sintaxis genérica del comando es la siguiente:

```sh
docker container logs <container identifier>
```

Para acceder a los registros desde el `notes-db` contenedor, puede ejecutar el siguiente comando:

```sh
docker container logs notes-db

# The files belonging to this database system will be owned by user "postgres".
# This user must also own the server process.

# The database cluster will be initialized with locale "en_US.utf8".
# The default database encoding has accordingly been set to "UTF8".
# The default text search configuration will be set to "english".
#
# Data page checksums are disabled.
#
# fixing permissions on existing directory /var/lib/postgresql/data ... ok
# creating subdirectories ... ok
# selecting dynamic shared memory implementation ... posix
# selecting default max_connections ... 100
# selecting default shared_buffers ... 128MB
# selecting default time zone ... Etc/UTC
# creating configuration files ... ok
# running bootstrap script ... ok
# performing post-bootstrap initialization ... ok
# syncing data to disk ... ok
#
#
# Success. You can now start the database server using:
#
#     pg_ctl -D /var/lib/postgresql/data -l logfile start
#
# initdb: warning: enabling "trust" authentication for local connections
# You can change this by editing pg_hba.conf or using the option -A, or
# --auth-local and --auth-host, the next time you run initdb.
# waiting for server to start....2021-01-25 13:39:21.613 UTC [47] LOG:  starting PostgreSQL 12.5 (Debian 12.5-1.pgdg100+1) on x86_64-pc-linux-gnu, compiled by gcc (Debian 8.3.0-6) 8.3.0, 64-bit
# 2021-01-25 13:39:21.621 UTC [47] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
# 2021-01-25 13:39:21.675 UTC [48] LOG:  database system was shut down at 2021-01-25 13:39:21 UTC
# 2021-01-25 13:39:21.685 UTC [47] LOG:  database system is ready to accept connections
#  done
# server started
# CREATE DATABASE
#
#
# /usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*
#
# 2021-01-25 13:39:22.008 UTC [47] LOG:  received fast shutdown request
# waiting for server to shut down....2021-01-25 13:39:22.015 UTC [47] LOG:  aborting any active transactions
# 2021-01-25 13:39:22.017 UTC [47] LOG:  background worker "logical replication launcher" (PID 54) exited with exit code 1
# 2021-01-25 13:39:22.017 UTC [49] LOG:  shutting down
# 2021-01-25 13:39:22.056 UTC [47] LOG:  database system is shut down
#  done
# server stopped
#
# PostgreSQL init process complete; ready for start up.
#
# 2021-01-25 13:39:22.135 UTC [1] LOG:  starting PostgreSQL 12.5 (Debian 12.5-1.pgdg100+1) on x86_64-pc-linux-gnu, compiled by gcc (Debian 8.3.0-6) 8.3.0, 64-bit
# 2021-01-25 13:39:22.136 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
# 2021-01-25 13:39:22.136 UTC [1] LOG:  listening on IPv6 address "::", port 5432
# 2021-01-25 13:39:22.147 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
# 2021-01-25 13:39:22.177 UTC [75] LOG:  database system was shut down at 2021-01-25 13:39:22 UTC
# 2021-01-25 13:39:22.190 UTC [1] LOG:  database system is ready to accept connections
```

Evidentemente por el texto en la línea 57, la base de datos está activa y lista para aceptar conexiones desde el exterior. También existe la opción `--follow` o `-f` para el comando que le permite adjuntar la consola a la salida de registros y obtener un flujo continuo de texto.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Ejemplo práctico

Ahora que ha aprendido lo suficiente sobre las redes en Docker, en esta sección aprenderá a contener un proyecto completo de varios contenedores. El proyecto con el que trabajará es simple con la `notes-api` tecnología de Express.js y PostgreSQL.

1.  **Crear una red**
    Para hacerlo, cree una red nombrada notes-api-networken su sistema:

    ```sh
    docker network create notes-api-network
    ```

2.  **Contenedor base de datos**
    Para ejecutar el servidor de base de datos puede ejecutar el siguiente comando:

    ```sh
      docker container run -d --name notes-db -e POSTGRES_DB=notesdb -e POSTGRES_PASSWORD=secret --network notes-api-network postgres:12

      # a7b287d34d96c8e81a63949c57b83d7c1d71b5660c87f5172f074bd1606196dc
    ```

3.  **Contenedor API**

    - Cómo escribir el Dockerfile

      Vaya al directorio donde ha clonado el [código](https://github.com/fhsinchy/docker-handbook-projects) del proyecto. Dentro de allí, ve dentro del `notes-api/api` directorio y crea un nuevo archivo `Dockerfile` . Ponga el siguiente código en el archivo:

      ```sh
      # stage one
      FROM node:lts-alpine as builder

      # install dependencies for node-gyp
      RUN apk add --no-cache python make g++

      WORKDIR /app

      COPY ./package.json .
      RUN npm install --only=prod

      # stage two
      FROM node:lts-alpine

      EXPOSE 3000
      ENV NODE_ENV=production

      USER node
      RUN mkdir -p /home/node/app
      WORKDIR /home/node/app

      COPY . .
      COPY --from=builder /app/node_modules  /home/node/app/node_modules

      CMD [ "node", "bin/www" ]
      ```

      Esta es una construcción de varias etapas. La primera etapa se usa para construir e instalar las dependencias usando `node-gyp` y la segunda etapa es para ejecutar la aplicación. Voy a ir a través de los pasos brevemente:

      - Stage 1 usa `node:lts-alpine` como base y usa `builder` como nombre artístico.
      - En la línea 5, instalamos `python` , `make` y `g++` . La `node-gyp` herramienta requiere estos tres paquetes para ejecutarse.
      - En la línea 7, configuramos `/app` el directorio como `WORKDIR` .
      - En la línea 9 y 10, copiamos el `package.json` archivo `WORKDIR` e instalamos todas las dependencias.
      - La etapa 2 también se usa `node-lts:alpine` como base.
      - En la línea 16, configuramos la `NODE_ENV` variable de entorno en `production` . Esto es importante para que la API funcione correctamente.
      - De la línea 18 a la línea 20, configuramos el usuario predeterminado en `node` , creamos el `/home/node/app` directorio y lo configuramos como WORKDIR.
      - En la línea 22 copiamos todos los archivos del proyecto y en la línea 23 copiamos el `node_modules` directorio del `builder` escenario. Este directorio contiene todas las dependencias integradas necesarias para ejecutar la aplicación.
      - En la línea 25, configuramos el comando predeterminado.

      Para construir una imagen a partir de esto `Dockerfile` , puede ejecutar el siguiente comando:

      ```sh
      docker image build --tag notes-api .

      # Sending build context to Docker daemon  37.38kB
      # Step 1/14 : FROM node:lts-alpine as builder
      #  ---> 471e8b4eb0b2
      # Step 2/14 : RUN apk add --no-cache python make g++
      #  ---> Running in 5f20a0ecc04b
      # fetch http://dl-cdn.alpinelinux.org/alpine/v3.11/main/x86_64/APKINDEX.tar.gz
      # fetch http://dl-cdn.alpinelinux.org/alpine/v3.11/community/x86_64/APKINDEX.tar.gz
      # (1/21) Installing binutils (2.33.1-r0)
      # (2/21) Installing gmp (6.1.2-r1)
      # (3/21) Installing isl (0.18-r0)
      # (4/21) Installing libgomp (9.3.0-r0)
      # (5/21) Installing libatomic (9.3.0-r0)
      # (6/21) Installing mpfr4 (4.0.2-r1)
      # (7/21) Installing mpc1 (1.1.0-r1)
      # (8/21) Installing gcc (9.3.0-r0)
      # (9/21) Installing musl-dev (1.1.24-r3)
      # (10/21) Installing libc-dev (0.7.2-r0)
      # (11/21) Installing g++ (9.3.0-r0)
      # (12/21) Installing make (4.2.1-r2)
      # (13/21) Installing libbz2 (1.0.8-r1)
      # (14/21) Installing expat (2.2.9-r1)
      # (15/21) Installing libffi (3.2.1-r6)
      # (16/21) Installing gdbm (1.13-r1)
      # (17/21) Installing ncurses-terminfo-base (6.1_p20200118-r4)
      # (18/21) Installing ncurses-libs (6.1_p20200118-r4)
      # (19/21) Installing readline (8.0.1-r0)
      # (20/21) Installing sqlite-libs (3.30.1-r2)
      # (21/21) Installing python2 (2.7.18-r0)
      # Executing busybox-1.31.1-r9.trigger
      # OK: 212 MiB in 37 packages
      # Removing intermediate container 5f20a0ecc04b
      #  ---> 637ca797d709
      # Step 3/14 : WORKDIR /app
      #  ---> Running in 846361b57599
      # Removing intermediate container 846361b57599
      #  ---> 3d58a482896e
      # Step 4/14 : COPY ./package.json .
      #  ---> 11b387794039
      # Step 5/14 : RUN npm install --only=prod
      #  ---> Running in 2e27e33f935d
      #  added 269 packages from 220 contributors and audited 1137 packages in 140.322s
      #
      # 4 packages are looking for funding
      #   run `npm fund` for details
      #
      # found 0 vulnerabilities
      #
      # Removing intermediate container 2e27e33f935d
      #  ---> eb7cb2cb0b20
      # Step 6/14 : FROM node:lts-alpine
      #  ---> 471e8b4eb0b2
      # Step 7/14 : EXPOSE 3000
      #  ---> Running in 4ea24f871747
      # Removing intermediate container 4ea24f871747
      #  ---> 1f0206f2f050
      # Step 8/14 : ENV NODE_ENV=production
      #  ---> Running in 5d40d6ac3b7e
      # Removing intermediate container 5d40d6ac3b7e
      #  ---> 31f62da17929
      # Step 9/14 : USER node
      #  ---> Running in 0963e1fb19a0
      # Removing intermediate container 0963e1fb19a0
      #  ---> 0f4045152b1c
      # Step 10/14 : RUN mkdir -p /home/node/app
      #  ---> Running in 0ac591b3adbd
      # Removing intermediate container 0ac591b3adbd
      #  ---> 5908373dfc75
      # Step 11/14 : WORKDIR /home/node/app
      #  ---> Running in 55253b62ff57
      # Removing intermediate container 55253b62ff57
      #  ---> 2883cdb7c77a
      # Step 12/14 : COPY . .
      #  ---> 8e60893a7142
      # Step 13/14 : COPY --from=builder /app/node_modules  /home/node/app/node_modules
      #  ---> 27a85faa4342
      # Step 14/14 : CMD [ "node", "bin/www" ]
      #  ---> Running in 349c8ca6dd3e
      # Removing intermediate container 349c8ca6dd3e
      #  ---> 9ea100571585
      # Successfully built 9ea100571585
      # Successfully tagged notes-api:latest
      ```

      Antes de ejecutar un contenedor con esta imagen, asegúrese de que el contenedor de la base de datos se esté ejecutando y esté adjunto al archivo `notes-api-network` .

      ```sh
      docker container inspect notes-db

      # [
      #     {
      #         ...
      #         "State": {
      #             "Status": "running",
      #             "Running": true,
      #             "Paused": false,
      #             "Restarting": false,
      #             "OOMKilled": false,
      #             "Dead": false,
      #             "Pid": 11521,
      #             "ExitCode": 0,
      #             "Error": "",
      #             "StartedAt": "2021-01-26T06:55:44.928510218Z",
      #             "FinishedAt": "2021-01-25T14:19:31.316854657Z"
      #         },
      #         ...
      #         "Mounts": [
      #             {
      #                 "Type": "volume",
      #                 "Name": "notes-db-data",
      #                 "Source": "/var/lib/docker/volumes/notes-db-data/_data",
      #                 "Destination": "/var/lib/postgresql/data",
      #                 "Driver": "local",
      #                 "Mode": "z",
      #                 "RW": true,
      #                 "Propagation": ""
      #             }
      #         ],
      #         ...
      #         "NetworkSettings": {
      #             ...
      #             "Networks": {
      #                 "bridge": {
      #                     "IPAMConfig": null,
      #                     "Links": null,
      #                     "Aliases": null,
      #                     "NetworkID": "e4c7ce50a5a2a49672155ff498597db336ecc2e3bbb6ee8baeebcf9fcfa0e1ab",
      #                     "EndpointID": "2a2587f8285fa020878dd38bdc630cdfca0d769f76fc143d1b554237ce907371",
      #                     "Gateway": "172.17.0.1",
      #                     "IPAddress": "172.17.0.2",
      #                     "IPPrefixLen": 16,
      #                     "IPv6Gateway": "",
      #                     "GlobalIPv6Address": "",
      #                     "GlobalIPv6PrefixLen": 0,
      #                     "MacAddress": "02:42:ac:11:00:02",
      #                     "DriverOpts": null
      #                 },
      #                 "notes-api-network": {
      #                     "IPAMConfig": {},
      #                     "Links": null,
      #                     "Aliases": [
      #                         "37755e86d627"
      #                     ],
      #                     "NetworkID": "06579ad9f93d59fc3866ac628ed258dfac2ed7bc1a9cd6fe6e67220b15d203ea",
      #                     "EndpointID": "5b8f8718ec9a5ec53e7a13cce3cb540fdf3556fb34242362a8da4cc08d37223c",
      #                     "Gateway": "172.18.0.1",
      #                     "IPAddress": "172.18.0.2",
      #                     "IPPrefixLen": 16,
      #                     "IPv6Gateway": "",
      #                     "GlobalIPv6Address": "",
      #                     "GlobalIPv6PrefixLen": 0,
      #                     "MacAddress": "02:42:ac:12:00:02",
      #                     "DriverOpts": {}
      #                 }
      #             }
      #         }
      #     }
      # ]
      ```

      En mi sistema, el `notes-db` contenedor se está ejecutando, usa el `notes-db-data` volumen y está conectado al `notes-api-network` puente.

      Una vez que esté seguro de que todo está en su lugar, puede ejecutar un nuevo contenedor ejecutando el siguiente comando:

      ```sh
      docker container run -dp 3000:3000 --namenotes-api -e DB_HOST=notes-db -e DB_DATABASE=notesdb -e DB_PASSWORD=secret --network notes-api-network notes-api

      # f9ece420872de99a060b954e3c236cbb1e23d468feffa7fed1e06985d99fb919
      ```

      La `notes-api` aplicación requiere que se establezcan tres variables de entorno. Son los siguientes:

      - `DB_HOST` - Este es el host del servidor de la base de datos. Dado que tanto el servidor de la base de datos como la API están conectados a la misma red de puente definida por el usuario, se puede hacer referencia al servidor de la base de datos utilizando su nombre de contenedor, que es `notes-db` en este caso.
      - `DB_DATABASE` - La base de datos que usará esta API. Al ejecutar el servidor de la base de datos , establecemos el nombre de la base de datos predeterminado para `notesdb` usar la `POSTGRES_DB` variable de entorno. Usaremos eso aquí.
      - `DB_PASSWORD` - Contraseña para conectarse a la base de datos. Esto también se configuró en la subsección Ejecución del servidor de la base `POSTGRES_PASSWORD` de datos mediante la variable de entorno.

      Para verificar si el contenedor se está ejecutando correctamente o no, puede usar el `docker ps` comando:

      ```sh
      docker ps

      # CONTAINER ID   IMAGE         COMMAND                  CREATED          STATUS          PORTS                    NAMES
      # f9ece420872d   notes-api     "docker-entrypoint.s…"   12 minutes ago   Up 12 minutes   0.0.0.0:3000->3000/tcp   notes-api
      # 37755e86d627   postgres:12   "docker-entrypoint.s…"   17 hours ago     Up 14 minutes   5432/tcp                 notes-db
      ```

      El contenedor se está ejecutando ahora. Puede visitar http://127.0.0.1:3000/para ver la API en acción.

      <div align="center"> 
        <img src="https://www.freecodecamp.org/news/content/images/size/w1600/2021/01/bonjour-mon-ami.png" alt="screenshot"/>
      </div>

      La API tiene cinco rutas en total que puedes ver dentro del `/notes-api/api/api/routes/notes.js` archivo.

      Aunque el contenedor se está ejecutando, hay una última cosa que deberá hacer antes de poder comenzar a usarlo. Deberá ejecutar la migración de la base de datos necesaria para configurar las tablas de la base de datos, y puede hacerlo ejecutando `npm run db:migrate` el comando dentro del contenedor.

      <p align="right">(<a href="#top">volver arriba</a>)</p>

### Cómo ejecutar comandos en un contenedor en ejecución (exec)

Para ejecutar un comando dentro de un contenedor en ejecución, deberá usar el `exec` .

La sintaxis genérica del execcomando es la siguiente:

```sh
docker container exec <container identifier> <command>
```

Ejemplo:

Para ejecutar `npm run db:migrate` dentro del `notes-api` contenedor, puede ejecutar el siguiente comando:

```sh
docker container exec notes-api npm run db:migrate

# > notes-api@ db:migrate /home/node/app
# > knex migrate:latest
#
# Using environment: production
# Batch 1 run: 1 migrations
```

En los casos en los que desee ejecutar un comando interactivo dentro de un contenedor en ejecución, deberá usar la `-it` bandera. Como ejemplo, si desea acceder al shell que se ejecuta dentro del `notes-api` contenedor, puede ejecutar siguiendo el comando:

```sh
docker container exec -it notes-api sh

# / # uname -a
# Linux b5b1367d6b31 5.10.9-201.fc33.x86_64 #1 SMP Wed Jan 20 16:56:23 UTC 2021 x86_64 Linux
```

<p align="right">(<a href="#top">volver arriba</a>)</p>

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
