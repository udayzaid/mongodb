## Configuración de MongoDB en Docker

Este repositorio contiene los pasos detallados para configurar y ejecutar MongoDB dentro de un contenedor Docker en un sistema Windows, así como la creación de una base de datos y colecciones utilizando MongoDB Compass.
Requisitos Previos

## Antes de comenzar, asegúrate de tener lo siguiente instalado:

    Docker: Para ejecutar contenedores y manejar imágenes.
    Docker Compose: Para la orquestación de múltiples contenedores (si es necesario).
    MongoDB Compass: Herramienta gráfica para gestionar bases de datos MongoDB.
    Git: Para clonar el repositorio y manejar el control de versiones (opcional).

## Paso 1: Descargar la imagen de MongoDB 

    Abre tu terminal o consola de comandos en PowerShell.

    Ejecuta el siguiente comando para descargar la imagen oficial de MongoDB:

    - docker pull mongo -

    Esto descargará la última versión de la imagen de MongoDB.

## Paso 2: Crear un contenedor con MongoDB

Ahora vamos a crear un contenedor para ejecutar MongoDB.

    Ejecuta el siguiente comando para crear y correr el contenedor de MongoDB en PowerShell:

    - docker run --name mongo-container -d -p 27017:27017 mongo -

    Explicación de los parámetros:
        --name mongo-container: Le da un nombre al contenedor (puedes usar cualquier nombre).
        -d: Ejecuta el contenedor en segundo plano.
        -p 27017:27017: Mapea el puerto 27017 del contenedor al puerto 27017 de tu máquina local (este es el puerto por defecto de MongoDB).
        mongo: Es la imagen de MongoDB que descargamos.

    Importante: Si te sale un error en este paso, asegúrate de haber abierto el programa Docker Desktop en tu sistema. Espera a que la interfaz gráfica se ejecute correctamente y luego repite el paso 2.

## Paso 3: Verificar que el contenedor está corriendo

Para asegurarte de que el contenedor se ha creado correctamente y está en ejecución, usa el siguiente comando:

- docker ps -

Esto te mostrará una lista de los contenedores en ejecución. Deberías ver algo como esto:

CONTAINER ID   IMAGE   COMMAND                  CREATED        STATUS        PORTS                      NAMES
d3c6bcf9a58d   mongo   "docker-entrypoint.s…"   2 minutes ago  Up 2 minutes  0.0.0.0:27017->27017/tcp   mongo-container

## Paso 4: Verificar en Docker Desktop

Verifica que el contenedor y la imagen se hayan levantado correctamente en la interfaz de Docker Desktop. Si todo está bien, el contenedor MongoDB debería aparecer en la lista de contenedores en ejecución.
## Paso 5: Conectar a MongoDB con MongoDB Compass

Ahora, conecta a tu contenedor MongoDB usando MongoDB Compass.

    Abrir MongoDB Compass: Si aún no lo has abierto, simplemente ejecuta MongoDB Compass en tu máquina.

    Conectar a MongoDB: En la pantalla de inicio de MongoDB Compass, encontrarás un formulario para conectar. Los datos que necesitas son los siguientes:
        Host: localhost
        Puerto: 27017
        Autenticación: Si tu base de datos tiene autenticación habilitada, necesitarás las credenciales (nombre de usuario y contraseña). Si no tienes autenticación, puedes dejar esos campos vacíos.

    Tu configuración debería verse así:
        Host: localhost
        Puerto: 27017
        Base de datos: Puedes dejarlo vacío para conectarte al servidor y explorar todas las bases de datos.

    Notas importantes:
        Si tu contenedor de MongoDB está corriendo en un puerto diferente o si estás usando algún tipo de autenticación, necesitarás ajustar los parámetros en Compass.
        Si tienes problemas de conexión, asegúrate de que el contenedor de MongoDB está en funcionamiento y escuchando en el puerto 27017.

Acciones Básicas en MongoDB Compass

Con MongoDB Compass, puedes realizar varias acciones básicas de administración de bases de datos y colecciones de manera visual:
## 1. Crear una nueva base de datos

    Si aún no tienes una base de datos, puedes crear una desde Compass.
    En la pantalla principal de MongoDB Compass, una vez conectado, verás una lista de bases de datos en tu servidor.
    En la parte superior izquierda, deberías ver un botón que dice "Create Database". Haz clic en ese botón.
    Luego, proporciona un nombre para tu nueva base de datos y una colección inicial (por ejemplo, "usuarios").
    Haz clic en "Create Database".

## 2. Crear una colección

Las colecciones son el equivalente a las tablas en bases de datos relacionales. Puedes crear una colección dentro de tu base de datos.

    Si ya tienes una base de datos seleccionada, haz clic en ella.
    Dentro de la base de datos, deberías ver un botón que dice "Create Collection". Haz clic en ese botón.
    Proporciona el nombre de la colección, como "usuarios", y haz clic en "Create".

## 3. Insertar documentos

Los documentos en MongoDB son objetos de datos en formato JSON (o BSON). Para agregar un documento a tu colección:

    Dentro de la colección que has creado, haz clic en "Insert Document".

    Se abrirá un editor donde puedes escribir un documento JSON. Por ejemplo, puedes insertar un documento de usuario como:

    {
        "nombre": "Juan",
        "apellido": "Pérez",
        "edad": 30,
        "email": "juan.perez@email.com"
    }

    Haz clic en "Insert" para agregarlo a la colección.

## 4. Realizar consultas

MongoDB utiliza consultas en formato JSON para obtener datos. Puedes escribir consultas para encontrar documentos en tu colección.

    Dentro de la colección, haz clic en la pestaña "Find" para realizar consultas.

    Por ejemplo, si quieres encontrar todos los usuarios cuyo apellido sea "Pérez", puedes escribir:

    { "apellido": "Pérez" }

    Haz clic en "Find" y Compass te mostrará los documentos que coinciden con esa consulta.

Con MongoDB Compass, podrás administrar y explorar tu base de datos de manera más visual y sencilla.

