# 💬 Panel de Control de Chat - Aurelio

Sistema completo de control de chat con identificación automática de clientes e interfaz de administración en tiempo real.

## 🚀 Características Principales

### ✨ Identificación Automática de Clientes
- **Detección automática** de dispositivo, navegador y sistema operativo
- **Generación de nombres únicos** con formato: `[DISPOSITIVO] [NAVEGADOR] desde [CIUDAD] (#[CONTADOR])`
- **Información técnica completa**: resolución, conexión, idioma, zona horaria
- **Geolocalización** aproximada (ciudad/país)
- **IDs únicos** anónimos para sesiones

### 🎛️ Panel de Administración
- **Diseño moderno** de 2 columnas (sidebar + área principal)
- **Lista de conversaciones** activas con información en tiempo real
- **Chat seleccionado** con historial completo de mensajes
- **Información expandible** de cada cliente
- **Indicadores visuales** de estado online/offline

### 🔄 Tiempo Real
- **Integración Pusher** con canal 'chataurelio'
- **Recepción automática** de mensajes nuevos
- **Envío bidireccional** de respuestas
- **Notificaciones sonoras** para mensajes nuevos
- **Contadores** de mensajes no leídos

### 📱 Responsive Design
- **Adaptable** a diferentes tamaños de pantalla
- **Iconos específicos** por tipo de dispositivo
- **Estados visuales** diferenciados (usuario, operador, AI)
- **Auto-scroll** en mensajes nuevos

## 📁 Archivos del Sistema

### `control.html`
Panel principal de administración con todas las funcionalidades avanzadas:
- Sistema de identificación automática de clientes
- Interface de 2 columnas con sidebar y área principal
- Gestión de múltiples conversaciones simultáneas
- Información técnica expandible de cada cliente
- Notificaciones sonoras y visuales

### `client-demo.html`
Página de demostración que simula un cliente conectándose:
- Detección automática de información del navegador/dispositivo
- Generación automática de nombre único
- Envío de información técnica al panel de control
- Interface de chat funcional para pruebas

### `functions/enviar.js`
Función Netlify actualizada que maneja:
- Mensajes bidireccionales entre cliente y operador
- Información técnica de dispositivos
- Integración con OpenAI para respuestas automáticas
- Headers CORS mejorados

## 🛠️ Configuración y Uso

### 1. Variables de Entorno (Netlify)
```bash
PUSHER_APP_ID=tu_app_id
PUSHER_KEY=46e53dfe6f8d93182aaa
PUSHER_SECRET=tu_secret
PUSHER_CLUSTER=us2
OPENAI_API_KEY=tu_openai_key
```

### 2. Acceso al Panel de Control
Navega a `control.html` para acceder al panel de administración:
- Se conectará automáticamente al canal Pusher
- Mostrará conversaciones en tiempo real
- Permitirá responder a clientes directamente

### 3. Prueba con Cliente Demo
Abre `client-demo.html` en otro navegador/dispositivo:
- Se detectará automáticamente la información del cliente
- Aparecerá en el panel de control con nombre único
- Puedes enviar mensajes de prueba

## 📊 Formato de Datos

### Información del Cliente
```javascript
{
    device: "iPhone",           // Tipo de dispositivo
    browser: "Safari",          // Navegador
    browserVersion: "17.2",     // Versión del navegador
    os: "iOS 17.2.1",          // Sistema operativo
    screen: "414x896",          // Resolución de pantalla
    pixelRatio: 3,              // Densidad de píxeles
    location: "Madrid, España", // Ubicación geográfica
    timezone: "Europe/Madrid",  // Zona horaria
    language: "es-ES",          // Idioma
    connection: "5G",           // Tipo de conexión
    timestamp: "2025-01-25T03:00:55Z"
}
```

### Nombre Generado Automáticamente
```
iPhone Safari desde Madrid, España (#001)
Desktop Chrome desde Barcelona, España (#002)
Android Chrome desde Valencia, España (#003)
```

## 🎨 Interfaz Visual

### Lista de Conversaciones (Sidebar)
- 📱 **Iconos por dispositivo**: iPhone, Android, Desktop, etc.
- 🟢 **Indicador de estado**: Online/Offline
- 🔴 **Contador de mensajes**: Nuevos mensajes no leídos
- 📍 **Ubicación**: Ciudad/país del cliente
- ℹ️ **Información expandible**: Detalles técnicos completos

### Área de Chat Principal
- 💬 **Header dinámico**: Información del cliente seleccionado
- 📝 **Mensajes diferenciados**: Usuario (azul), Operador (verde), AI (gris)
- ⏰ **Timestamps**: Hora de cada mensaje
- 🔄 **Auto-scroll**: Automático hacia mensajes nuevos
- ✍️ **Campo de respuesta**: Con envío directo

### Indicadores de Estado
- 🟢 **Cliente online**: Punto verde + "En línea"
- 🔴 **Mensajes nuevos**: Contador rojo con número
- 📱 **Información de dispositivo**: Icono + tipo + navegador
- 📍 **Ubicación**: Icono + ciudad/país

## 🔧 Funcionalidades Técnicas

### Detección Automática
```javascript
ClientDetector.detectDevice(userAgent)    // iPhone, Android, Desktop
ClientDetector.detectBrowser(userAgent)   // Chrome, Safari, Firefox
ClientDetector.detectOS(userAgent)        // iOS, Android, Windows
ClientDetector.getLocationInfo()          // Madrid, España
```

### Generación de IDs Únicos
- **Hash de UserAgent**: Para evitar duplicados
- **Timestamp**: Para unicidad temporal
- **Hash de pantalla**: Para diferenciación adicional
- **Resultado**: ID anónimo de 32 caracteres

### Gestión de Sesiones
- **LocalStorage**: Mantiene conversaciones activas
- **Estado en tiempo real**: A través de Pusher
- **Notificaciones**: Audio y visual para nuevos mensajes
- **Auto-reconexión**: Manejo automático de desconexiones

## 🔐 Seguridad y Privacidad

### Datos Anónimos
- ❌ **Sin IPs**: Solo hash de información técnica
- ❌ **Sin datos personales**: Solo información del navegador/dispositivo
- ✅ **IDs únicos**: Generados algorítmicamente
- ✅ **Ubicación aproximada**: Solo ciudad/país

### GDPR Compliance
- **Datos mínimos**: Solo lo necesario para el funcionamiento
- **Anonimización**: Hashes en lugar de datos directos
- **Transparencia**: Información visible para el usuario
- **Control**: Datos solo durante la sesión activa

## 🚀 Deployment

### Netlify
1. Conecta el repositorio a Netlify
2. Configura las variables de entorno
3. Deploy automático con cada push
4. URL: `tu-sitio.netlify.app/control.html`

### Testing Local
```bash
# Servidor HTTP simple para pruebas
python3 -m http.server 8000
# Luego accede a:
# http://localhost:8000/control.html
# http://localhost:8000/client-demo.html
```

## 📞 Soporte

Para más información o soporte técnico, consulta la documentación del proyecto o contacta al equipo de desarrollo.

---

**Versión**: 2.0  
**Última actualización**: Enero 2025  
**Compatibilidad**: Todos los navegadores modernos