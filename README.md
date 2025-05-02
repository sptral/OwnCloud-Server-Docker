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
    git clone <URL_DEL_TU_REPOSITORIO>
    cd <NOMBRE_DEL_TU_REPOSITORIO>
    ```

    Reemplaza `<URL_DEL_TU_REPOSITORIO>` con la URL de tu repositorio en GitHub y `<NOMBRE_DEL_TU_REPOSITORIO>` con el nombre del directorio donde se clonará el repositorio.

2.  **Revisa el archivo `docker-compose.yml`:**

    El archivo `docker-compose.yml` define los servicios necesarios para Owncloud (generalmente el servidor Owncloud y una base de datos). Puedes abrirlo con un editor de texto para entender su configuración.

    Por defecto, el archivo debería configurar:
    * Un contenedor para Owncloud.
    * Un contenedor para la base de datos (comúnmente MariaDB o PostgreSQL).
    * Volúmenes para persistir los datos de Owncloud y la base de datos.
    * Mapeo de puertos para acceder a la interfaz web de Owncloud.

    **Consideraciones de seguridad:** Para un entorno de producción, es altamente recomendable:
    * Modificar las credenciales de la base de datos por defecto en el archivo `docker-compose.yml` o, mejor aún, utilizando variables de entorno en un archivo `.env`.
    * Configurar un proxy inverso (como Nginx o Traefik) para manejar el tráfico HTTPS y asegurar tu conexión a Owncloud.

## Uso

1.  **Inicia los contenedores:**

    Desde el directorio donde clonaste el repositorio, ejecuta el siguiente comando:

    ```bash
    docker-compose up -d
    ```

    Esto descargará las imágenes de Docker necesarias (si no las tienes localmente) y iniciará los servicios en segundo plano (`-d`).

2.  **Accede a Owncloud:**

    Una vez que los contenedores estén en funcionamiento (puede tardar unos minutos la primera vez), podrás acceder a la interfaz web de Owncloud a través de tu navegador.

    Por defecto, Owncloud suele ser accesible en el puerto `80` o `8080` de la máquina donde ejecutaste Docker Compose. Consulta la sección `ports` del servicio `owncloud` en tu `docker-compose.yml` para confirmar el puerto mapeado.

    Abre tu navegador y navega a:

    ```
    http://localhost[:PUERTO]
    ```

    Reemplaza `[:PUERTO]` con el número de puerto configurado en tu `docker-compose.yml` (por ejemplo, `http://localhost:8080`).

3.  **Configuración inicial de Owncloud:**

    La primera vez que accedas a Owncloud, se te guiará a través de un proceso de configuración inicial. Deberás:
    * Crear una cuenta de administrador.
    * Configurar la conexión a la base de datos (los detalles se encuentran en tu `docker-compose.yml`).

4.  **Detén los contenedores:**

    Para detener los servicios de Owncloud, ejecuta el siguiente comando en el mismo directorio:

    ```bash
    docker-compose down
    ```

    Esto detendrá y eliminará los contenedores, pero los volúmenes de datos persistirán por defecto.

## Configuración adicional

Puedes personalizar la configuración de Owncloud modificando el archivo `docker-compose.yml`. Algunas personalizaciones comunes incluyen:

* **Puertos:** Cambiar los puertos mapeados para evitar conflictos.
* **Volúmenes:** Modificar la ubicación de los volúmenes en tu sistema host.
* **Variables de Entorno:** Configurar Owncloud utilizando variables de entorno (consulta la documentación oficial de la imagen de Docker de Owncloud para ver las variables disponibles).
* **Redes:** Definir redes personalizadas para tus contenedores.

Recuerda reconstruir y reiniciar los contenedores (`docker-compose down` seguido de `docker-compose up -d`) después de realizar cambios en el `docker-compose.yml`.

## Contribuciones

Si encuentras algún problema o tienes sugerencias para mejorar este setup de Docker Compose, no dudes en abrir un "issue" o enviar un "pull request" en este repositorio.

## Licencia

Este proyecto está bajo la Licencia [Especifica tu Licencia, por ejemplo, MIT]. Consulta el archivo `LICENSE` para más detalles.
# OwnCloud-Server-Docker
# OwnCloud-Server-Docker
