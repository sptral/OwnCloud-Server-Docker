# Owncloud con Docker Compose

Este repositorio contiene un archivo `docker-compose.yml` para desplegar una instancia de Owncloud utilizando Docker. Esto facilita la puesta en marcha de tu propia nube personal de forma rápida y sencilla.

## Prerrequisitos

Antes de comenzar, asegúrate de tener instalado lo siguiente en tu sistema:

* **Docker:** [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/)
* **Docker Compose:** Generalmente viene incluido con las versiones recientes de Docker Desktop. Si no es así, puedes instalarlo siguiendo las instrucciones aquí: [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)
* **Git:** [https://git-scm.com/book/en/v2/Getting-Started-Installing-Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

## Configuración

1.  **Clona el repositorio:**

    ```bash
    git clone https://github.com/sptral/OwnCloud-Server-Docker.git
    cd OwnCloud-Server-Docker
    ```


2.  **Revisa el archivo `docker-compose.yml`:**

    El archivo `docker-compose.yml` define los servicios necesarios para Owncloud. Puedes abrirlo con un editor de texto para entender su configuración. Tienen comentarios las partes que deben modificarse.

    Por defecto, el archivo debería configurar:
    * Un contenedor para Owncloud.
    * Un contenedor para la base de datos Mariadb.
    * Volúmenes para persistir los datos de Owncloud y la base de datos.
    * Mapeo de puertos para acceder a la interfaz web de Owncloud.

## Uso

1.  **Inicia los contenedores:**

    Desde el directorio donde clonaste el repositorio, ejecuta el siguiente comando:

    ```bash
    docker compose up -d
    ```

    Esto descargará las imágenes de Docker necesarias (si no las tienes localmente) y iniciará los servicios en segundo plano (`-d`).

2.  **Accede a Owncloud:**

    Una vez que los contenedores estén en funcionamiento (puede tardar unos minutos la primera vez), podrás acceder a la interfaz web de Owncloud a través de tu navegador.

    Por defecto, Owncloud suele ser accesible en el puerto `8585` de la máquina donde ejecutaste Docker Compose. Debido a lo cual se debe de usar la ip que corresponde al equipo.


    Abre tu navegador y navega a:

    ```
    http://<localhost>:8585
    ```

    **Nota:** Es necesario sustituir `<localhost>` por la ip que corresponde al equipo en el que se instalaron los contenedores.


4.  **Configuración inicial de Owncloud:**

    La primera vez que accedas a Owncloud, se debera ingresar con los datos del administrador (usuario y contraseña).

5.  **Para mantener encendidos siempre los contenedores, utilizar el siguiente comando:**

     ```bash
    docker update --restart unless-stopped Owncloud-Server
    docker update --restart unless-stopped Owncloud-Mariadb
    docker update --restart unless-stopped Owncloud-Redis
    ```
6.  **Detén y elimina los contenedores:**

    Para detener los servicios de Owncloud, ejecuta el siguiente comando en el mismo directorio:

    ```bash
    docker compose down
    ```

    Esto detendrá y eliminará los contenedores, pero los volúmenes de datos persistirán por defecto. Debido a lo cual deberá realizarse con precausión.
# OwnCloud-Server-Docker
