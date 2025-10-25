# Discord User Monitor

## Descripción

Discord User Monitor es una aplicación de escritorio para monitorear la actividad de usuarios específicos en Discord. Funciona como un "self-bot", utilizando tu propio token de cuenta de Discord para observar eventos en tiempo real.

**Nota:** El uso de self-bots va en contra de los Términos de Servicio de Discord y puede resultar en la suspensión de tu cuenta. Úsalo bajo tu propio riesgo.

## Características

- **Monitoreo de Actividad:** Rastrea una variedad de eventos de los usuarios que elijas:
    - Cambios de estado (en línea, ausente, no molestar, desconectado).
    - Actividad de juego o aplicaciones.
    - Mensajes enviados en servidores compartidos.
    - Conexión y desconexión de canales de voz.
    - Cambios de estado en voz (silenciado, ensordecido).
- **Interfaz Gráfica:** Una interfaz de usuario de escritorio fácil de usar para gestionar los usuarios monitoreados y ver los eventos.
- **Base de Datos Local:** Todos los eventos se guardan en una base de datos local (SQLite) en tu computadora para que puedas revisarlos más tarde.
- **Visor de Servidores y Miembros:** Explora los servidores en los que te encuentras y sus listas de miembros.

## Instalación

1.  Ve a la sección de **Releases** en este repositorio de GitHub.
2.  Descarga el archivo `setup.exe` más reciente.
3.  Ejecuta el instalador y sigue las instrucciones.

## Uso

1.  **Obtén tu token de Discord:**
    - Abre Discord en tu navegador web.
    - Presiona `Ctrl+Shift+I` para abrir las herramientas de desarrollador.
    - Activa la vista de dispositivo móvil (generalmente un ícono de un teléfono y una tablet en la esquina superior izquierda de las herramientas de desarrollador).
    - Recarga la página (`Ctrl+R` o `F5`).
    - Ve a la pestaña `Application` (Aplicación).
    - En el menú de la izquierda, despliega `Local Storage` y selecciona la URL de Discord.
    - En el filtro, escribe `token`.
    - Copia el valor que aparece, **sin las comillas**. Este es tu token.
    - **¡No compartas este token con nadie!**

2.  **Inicia la aplicación:**
    - Abre Discord User Monitor desde el menú de inicio o el acceso directo del escritorio.
    - Pega tu token en el campo de texto y haz clic en "Conectar".
    - Una vez conectado, verás la información de tu perfil.

3.  **Monitorea a un usuario:**
    - Haz clic en "Ver Servidores".
    - Selecciona un servidor de la lista y haz clic en "Ver Miembros".
    - Busca al usuario que deseas monitorear y haz clic en el botón "Monitorear".
    - El usuario se agregará a tu lista de monitoreados en la pantalla principal.

4.  **Visualiza Eventos:**
    - En la pantalla principal, haz clic en "Ver Eventos" junto a un usuario monitoreado para ver su actividad reciente.
    - Haz clic en "Ver Todos los Eventos" para ver una cronología de todos los eventos de todos los usuarios monitoreados.

## Tecnologías Utilizadas

-   **Electron:** Para crear la aplicación de escritorio.
-   **Discord.js-selfbot-v13:** Para interactuar con la API de Discord.
-   **Better-sqlite3:** Para la base de datos local.
-   **HTML, CSS, JavaScript:** Para la interfaz de usuario.
