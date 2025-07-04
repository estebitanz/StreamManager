Este es un programa de libre uso, desarrollado y subido por el autor Eztbn.


#StreamManager: Gestión de Inventario de Cuentas de Streaming
StreamManager Pro es una aplicación de escritorio moderna y robusta, desarrollada en Python, diseñada para vendedores y gestores de cuentas de streaming. Permite llevar un control total sobre el inventario de cuentas, gestionar alquileres a múltiples usuarios y asegurar la información sensible de manera profesional.

La aplicación cuenta con una interfaz gráfica intuitiva y un sistema de monetización seguro a través de claves premium validadas por una API remota.

✨ Características Principales
Gestión de Inventario: Añade, edita y elimina cuentas de tu inventario (Netflix, Spotify, etc.) de forma centralizada.

Sistema de Alquileres Múltiples: Alquila una misma cuenta a varios usuarios simultáneamente y lleva un control preciso de quién la está usando.

Historial de Ventas: Mantén un registro detallado de todos los alquileres, con información del comprador, fechas y un ID único por transacción.

Dashboard de Análisis: Visualiza estadísticas clave de tu negocio de un vistazo: total de cuentas, disponibles, y número de alquileres activos.

Notificaciones Inteligentes: Recibe alertas de los alquileres que están próximos a vencer para poder gestionar las renovaciones a tiempo.

Seguridad Robusta:

Encriptación de Contraseñas: Todas las contraseñas de las cuentas se guardan cifradas en la base de datos local.

API Remota para Claves Premium: Las claves de activación de la membresía Premium se validan contra un servidor seguro en la nube, asegurando que no puedan ser extraídas o robadas del programa cliente.

Interfaz Moderna: Diseño limpio y profesional con temas claro y oscuro, desarrollado con CustomTkinter.

Búsqueda y Filtrado: Encuentra rápidamente cualquier cuenta o alquiler gracias a las barras de búsqueda integradas.

🛠️ Tecnologías Utilizadas
Aplicación Cliente (Escritorio):

Lenguaje: Python 3

Interfaz Gráfica: CustomTkinter

Base de Datos Local: SQLite con SQLAlchemy

Comunicación API: requests

Servidor API (Backend):

Framework: Flask

Base de Datos Remota: SQLite (alojada en el servidor)

Despliegue: Render (usando Gunicorn)

🏗️ Arquitectura del Proyecto
Este proyecto utiliza una arquitectura cliente-servidor para garantizar la seguridad del sistema de monetización:

El Cliente (StreamManagerApp): Es la aplicación de escritorio que los usuarios instalan. Gestiona la interfaz, el inventario de cuentas y la base de datos local (stream_manager.db), que solo contiene la información de las cuentas del usuario.

El Servidor (StreamManager_API): Es una API REST desplegada en la nube (Render). Su única responsabilidad es almacenar y validar las claves Premium en su propia base de datos segura (keys.db). El cliente nunca tiene acceso a la lista completa de claves.

🚀 Cómo Empezar
Para poner en marcha el proyecto, necesitarás configurar tanto el servidor como el cliente.

1. Configuración del Servidor API
Clona el repositorio de la API desde GitHub.

Genera la base de datos de claves: Abre una terminal en la carpeta de la API y ejecuta python generate_api_keys.py <numero_de_claves> para crear el archivo keys.db.

Sube los archivos a un nuevo repositorio de GitHub (privado), asegurándote de incluir el archivo keys.db generado.

Despliega en Render:

Crea un nuevo "Web Service" en Render y conéctalo a tu repositorio.

Usa los siguientes comandos de configuración:

Build Command: pip install -r requirements.txt

Start Command: gunicorn api_server:app

Copia la URL que te proporciona Render al finalizar el despliegue.

2. Configuración de la Aplicación Cliente
Clona el repositorio de la aplicación cliente.

Instala las dependencias:

pip install customtkinter Pillow pyperclip requests SQLAlchemy

Configura la URL de la API:

Abre el archivo gui.py.

Busca la variable API_URL y reemplaza la URL de ejemplo por la que copiaste de tu servidor en Render.

Ejecuta la aplicación:

python main.py

La primera vez que se ejecute, se crearán los archivos locales stream_manager.db y secret.key.

🖼️ Capturas de Pantalla
(Aquí puedes añadir imágenes de tu aplicación en funcionamiento para hacer el README más atractivo).

[Imagen del Dashboard]

[Imagen de la sección de Cuentas]

[Imagen del Historial de Ventas]
