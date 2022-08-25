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
    <img src="images/docker.png" alt="Logo" width="150" height="90">
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
        <li><a href="#que-es-una-imagen-focker?">Que es una imagen Docker</a></li>
        <li><a href="#descripción-general-de-la-arquitectura-de-Docker">Descripción general de la arquitectura de Docker</a></li>
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

**`Docker`** es una implementación de este tipo. Es una plataforma de contenedorización de código abierto que le permite contener sus aplicaciones, compartirlas mediante registros públicos o privados y también organizarlas.

## Conceptos básicos de Docker

### Hello World en DockeR

Abre la terminal y ejecuta el siguiente comando:

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

La imagen hello-world es un ejemplo de contenedorización mínima con Docker. Tiene un solo programa compilado a partir de un archivo hello.c responsable de imprimir el mensaje que estás viendo en tu terminal.

Ahora en su terminal, puede usar el docker ps -acomando para ver todos los contenedores que se están ejecutando actualmente o se han ejecutado en el pasado:

```sh
docker ps -a

# CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS                     PORTS               NAMES
# 128ec8ceab71        hello-world         "/hello"            14 seconds ago      Exited (0) 13 seconds ago                      exciting_chebyshev
```

En la salida:

- `CONTAINER ID` – Se ejecuta una identificación del contenedor con ID `128ec8ceab71` .

- `IMAGE` – Usa la imagen `hello-worl` .

- `STATUS` – Tiene `Exited (0) 13 seconds ago` donde el `(0)` código de salida significa que no se produjo ningún error durante el tiempo de ejecución del contenedor.

- `NAMES` - se ejecutó un contenedor llamado `exciting_chebyshev`

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

En el bloque de código anterior, ejecuté el uname -acomando en mi sistema operativo host para imprimir los detalles del kernel. Luego, en la siguiente línea, ejecuté el mismo comando dentro de un contenedor que ejecuta Alpine Linux .

Como puede ver en el resultado, el contenedor está usando el kernel de mi sistema operativo host. Esto demuestra que los contenedores virtualizan el sistema operativo host en lugar de tener un sistema operativo propio.

<p align="right">(<a href="#top">volver arriba</a>)</p>

### Que es una imagen Docker

Las imágenes son archivos autónomos de varias capas que actúan como plantilla para crear contenedores. Son como una copia congelada de solo lectura de un contenedor. Las imágenes se pueden intercambiar a través de registros.

En el pasado, diferentes motores de contenedores tenían diferentes formatos de imagen. Pero más tarde, la Open Container Initiative (OCI) definió una especificación estándar para imágenes de contenedores que cumplen los principales motores de contenedores que existen. Esto significa que una imagen creada con Docker se puede usar con otro tiempo de ejecución como Podman sin ningún problema adicional.

Los contenedores son solo imágenes en estado de ejecución. Cuando obtiene una imagen de Internet y ejecuta un contenedor con esa imagen, esencialmente crea otra capa temporal de escritura encima de las anteriores de solo lectura.

Este concepto se volverá mucho más claro en las próximas secciones de este libro. Pero por ahora, tenga en cuenta que las imágenes son archivos de solo lectura de varias capas que contienen su aplicación en el estado deseado.

<p align="right">(<a href="#top">volver arriba</a>)</p>

## Descripción general de la arquitectura de Docker

Ahora que se ha familiarizado con la mayoría de los conceptos fundamentales relacionados con la creación de contenedores y Docker, es hora de que comprenda cómo se diseñó Docker como software.

El motor consta de tres componentes principales:

1. **Docker Daemon:** El daemon ( `dockerd`) es un proceso que sigue ejecutándose en segundo plano y espera comandos del cliente. El daemon es capaz de administrar varios objetos Docker.
2. **Docker Client:** El cliente ( `docker`) es un programa de interfaz de línea de comandos principalmente responsable de transportar los comandos emitidos por los usuarios.
3. **API REST:** La API REST actúa como un puente entre el daemon y el cliente. Cualquier comando emitido usando el cliente pasa a través de la API para llegar finalmente al daemon.

Según los documentos oficiales:

> "Docker utiliza una arquitectura cliente-servidor. El cliente de Docker se comunica con el demonio de Docker , que hace el trabajo pesado de construir, ejecutar y distribuir sus contenedores de Docker".

Ahora es el momento de que entiendas cómo todas estas piezas del rompecabezas que acabas de aprender funcionan en armonía. Antes de sumergirme en la explicación de lo que realmente sucede cuando ejecuta el docker run hello-worldcomando, permítame mostrarle un pequeño diagrama que hice:

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

Si hay una versión más nueva de la imagen disponible en el registro público, el daemon recuperará la imagen nuevamente. Esa `:latest` es una etiqueta. Las imágenes suelen tener etiquetas significativas para indicar versiones o compilaciones. Aprenderá sobre esto con mayor detalle más adelante.

<p align="right">(<a href="#top">volver arriba</a>)</p>

<p align="right">(<a href="#top">volver arriba</a>)</p>
