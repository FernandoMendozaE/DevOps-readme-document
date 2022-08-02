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
        <li><a href="#cómo-maquina-virtual-local-con-vagrant">Cómo máquina virtual local con Vagrant</a>
          <ul>
            <li><a href="#agregar-dominio-a-su-archivo-de-hosts">Agregar dominio a su archivo de hosts</a>
          </ul>
        </li>
        <li><a href="#instalar-nginx">Instalar NGINX</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
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

```
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

```
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

```
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

```
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
