# Discord User Monitor (Self-Bot)

⚠️ **ADVERTENCIA CRÍTICA** ⚠️

Esta aplicación es un **SELF-BOT** que automatiza una cuenta de usuario de Discord.

## ⛔ RIESGOS Y ADVERTENCIAS

- ❌ **VIOLA LOS TÉRMINOS DE SERVICIO DE DISCORD**
- ❌ **PUEDE RESULTAR EN BAN PERMANENTE DE TU CUENTA**
- ❌ **DISCORD DETECTA Y BANEA SELF-BOTS ACTIVAMENTE**
- ❌ **PODRÍAS PERDER TU CUENTA PARA SIEMPRE**

**Uso bajo tu propio riesgo. Los desarrolladores no se hacen responsables de ninguna consecuencia.**

Referencia: [Términos de Servicio de Discord](https://discord.com/terms) - Sección sobre automatización de cuentas de usuario.

---

## ¿Por qué usar esto si es tan peligroso?

Esta herramienta está diseñada para **uso educacional** y para entender cómo funcionan los self-bots. Si solo quieres monitorear usuarios, **usa un bot oficial** que es completamente legal.

## Características

- **Monitoreo en tiempo real** de usuarios (amigos + servidores)
- **Cambios de estado**: En línea, Ausente, No molestar, Desconectado
- **Actividad en canales de voz**: Entrada, salida, cambios de canal, duración
- **Mensajes**: Detecta cuando un usuario envía mensajes
- **Actividades**: Juegos, Spotify, streaming, etc.
- **Historial completo**: Almacena todos los eventos con timestamps
- **No necesita permisos de servidor**: Usa tu propia cuenta

## Ventaja vs Bot oficial

| Característica | Self-Bot (esta app) | Bot oficial |
|---------------|---------------------|-------------|
| Monitorear amigos directos | ✅ Sí | ❌ No |
| Monitorear sin permisos de servidor | ✅ Sí | ❌ No (necesita invitación) |
| Legal según Discord ToS | ❌ NO | ✅ Sí |
| Riesgo de ban | ⚠️ MUY ALTO | ✅ Ninguno |

## Instalación

1. Descarga o clona este proyecto
2. Abre una terminal en la carpeta del proyecto
3. Instala las dependencias:

```bash
npm install
```

## Cómo obtener tu Token de Discord

⚠️ **Tu token es equivalente a tu contraseña. NUNCA lo compartas con nadie.**

### Método 1: Discord Web (Recomendado)

1. Abre Discord en tu navegador: https://discord.com/app
2. Presiona **F12** para abrir DevTools
3. Ve a la pestaña **Console**
4. Pega este código y presiona Enter:

```javascript
window.webpackChunkdiscord_app.push([[Math.random()],{},e=>{m=[];for(let c in e.c)m.push(e.c[c])}]);m.find(m=>m?.exports?.default?.getToken!==void 0).exports.default.getToken()
```

5. Copia el token que aparece (sin las comillas)

### Método 2: Discord App

1. Abre Discord Desktop
2. Presiona **Ctrl + Shift + I** (Windows) o **Cmd + Option + I** (Mac)
3. Ve a la pestaña **Console**
4. Usa el mismo código de arriba

## Uso

1. **Inicia la aplicación**:

```bash
npm start
```

2. **Primera vez**:
   - Pega el token de tu cuenta de Discord
   - Haz clic en "Conectar con mi Cuenta"
   - La aplicación iniciará sesión como TÚ

3. **Monitorear usuarios**:
   - Ve a la pestaña "Todos los Usuarios"
   - Verás tus amigos + todos los usuarios de tus servidores
   - Busca el usuario que quieres monitorear
   - Haz clic en "Monitorear"

4. **Ver eventos**:
   - Ve a la pestaña "Monitoreados"
   - Haz clic en "Ver Eventos" de cualquier usuario
   - Verás todo el historial de actividad

## Lo que monitorea

El self-bot registra automáticamente:

### 1. Cambios de estado
- En línea → Ausente
- Ausente → No molestar
- No molestar → Desconectado
- Etc.

### 2. Actividad en canales de voz
- Usuario se une a un canal
- Usuario sale de un canal (con duración de permanencia)
- Usuario se cambia de canal
- Usuario se mutea/desmutea
- Usuario activa/desactiva cámara

### 3. Mensajes
- Cuando un usuario envía un mensaje en canales de texto
- En qué servidor y canal
- Si tiene archivos adjuntos
- **NO guarda el contenido** (por privacidad)

### 4. Actividades
- Juegos (ej: "Jugando League of Legends")
- Streaming
- Escuchando Spotify
- Otras actividades personalizadas

## Estructura del Proyecto

```
DiscordUserRecord/
├── main.js           # Proceso principal de Electron
├── bot.js            # Lógica del self-bot (discord.js-selfbot-v13)
├── index.html        # Interfaz de usuario
├── renderer.js       # Lógica del frontend
├── package.json      # Dependencias
└── README.md         # Este archivo
```

## Almacenamiento de Datos

Los datos se guardan localmente usando `electron-store`:

- **Token de usuario**: Se guarda para reconexión automática
- **Usuarios monitoreados**: Lista de IDs de usuarios
- **Eventos**: Historial completo de actividad (últimos 1000 eventos por usuario)

**Ubicación del archivo**:
- Windows: `%APPDATA%/discorduserrecord/config.json`
- macOS: `~/Library/Application Support/discorduserrecord/config.json`
- Linux: `~/.config/discorduserrecord/config.json`

## Tipos de Eventos

| Evento | Descripción | Información guardada |
|--------|-------------|---------------------|
| **STATUS_CHANGE** | Cambio de estado | Estado anterior y nuevo |
| **VOICE_JOIN** | Se une a voz | Canal, servidor, timestamp |
| **VOICE_LEAVE** | Sale de voz | Canal, servidor, duración |
| **VOICE_MOVE** | Cambia de canal | Canal origen, canal destino |
| **VOICE_MUTE** | Se mutea/desmutea | Estado del micrófono |
| **VOICE_VIDEO** | Activa/desactiva cámara | Estado de cámara |
| **MESSAGE_SENT** | Envía un mensaje | Canal, servidor, longitud |
| **ACTIVITY_START** | Inicia actividad | Tipo de actividad |

## Seguridad

- ⚠️ El token se guarda localmente (sin encriptar)
- ⚠️ No se envía información a servidores externos
- ⚠️ El código es open-source y puedes revisarlo
- ⚠️ **NUNCA compartas tu token con nadie**
- ⚠️ **NUNCA subas el archivo de configuración a GitHub**

## Detección y Prevención de Bans

Discord detecta self-bots mediante:

1. **Patrones de comportamiento** - Actividad no humana
2. **User-Agent** - Conexiones desde librerías no oficiales
3. **Reportes** - Otros usuarios te reportan
4. **Análisis de tráfico** - Mensajes masivos, spam, etc.

### Cómo minimizar riesgos (NO garantizado):

- ✅ No envíes mensajes automáticos
- ✅ No hagas spam
- ✅ Usa solo para monitoreo pasivo
- ✅ No uses en cuentas importantes
- ✅ Usa una cuenta secundaria si es posible

## Solución de Problemas

### "Error: Incorrect login details"
- Verifica que el token sea correcto
- El token puede expirar si cambias tu contraseña
- Obtén un nuevo token

### "El self-bot no detecta estados"
- Asegúrate de estar en servidores comunes con el usuario
- El usuario debe tener la presencia visible

### "No aparecen mis amigos"
- Asegúrate de haber copiado el token correctamente
- Verifica que tengas amigos agregados en Discord

## Alternativa Legal: Bot Oficial

Si quieres evitar riesgos, considera usar un **bot oficial de Discord**:

1. Crear bot en https://discord.com/developers/applications
2. Activar intents privilegiados (PRESENCE, MEMBERS, MESSAGE CONTENT)
3. Invitar bot a tus servidores
4. Usar discord.js en lugar de discord.js-selfbot-v13

**Limitación**: Solo funciona en servidores donde puedas invitar el bot.

## Tecnologías Utilizadas

- **Electron** - Framework para aplicaciones de escritorio
- **discord.js-selfbot-v13** - Librería para self-bots (NO OFICIAL)
- **electron-store** - Almacenamiento persistente local

## Licencia

ISC

## Disclaimer Legal

Esta aplicación es solo para **fines educativos e investigación**. El uso de self-bots viola los Términos de Servicio de Discord.

**Al usar esta herramienta, aceptas que**:
- Entiendes los riesgos de ban permanente
- No responsabilizarás a los desarrolladores
- Usarás esto bajo tu propio riesgo
- No la usarás para acosar, stalkear o dañar a otros

**Los desarrolladores NO se hacen responsables de**:
- Bans de cuenta
- Pérdida de datos
- Consecuencias legales
- Cualquier otro daño derivado del uso de esta herramienta

## Referencias

- [Discord Terms of Service](https://discord.com/terms)
- [Discord Developer Policy](https://discord.com/developers/docs/policies-and-agreements/developer-policy)
- [Why Self-Bots are Bad](https://support.discord.com/hc/en-us/articles/115002192352)

---

**Recuerda: Si no estás seguro, NO LO USES. Hay alternativas legales.**
