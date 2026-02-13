# 🔐 Chat P2P Cifrado - Sin Servidor

Un chat seguro y privado que funciona completamente en el navegador, sin necesidad de servidores, backends ni bases de datos.

## ✨ Características

- **🔒 Cifrado de extremo a extremo**: Usa WebRTC cifrado con conexión P2P directa
- **🚫 Sin servidor propio**: No requiere backend, solo usa PeerJS público para señalización
- **🌐 Solo navegador**: Todo funciona en un solo archivo HTML
- **📱 Responsive**: Funciona en escritorio y móvil
- **🎨 Interfaz moderna**: Diseño limpio y super fácil de usar
- **⚡ Tiempo real**: Mensajes instantáneos P2P
- **🆓 100% Gratis**: Usa infraestructura pública de PeerJS
- **📦 Un solo archivo**: Todo en un HTML de ~20KB
- **🔑 Sistema de salas simple**: Contraseñas de 4 caracteres fáciles de compartir

## 🔐 Seguridad

### Cifrado automático:
1. **WebRTC DTLS**: Cifrado de transporte (automático)
2. **SRTP**: Cifrado de canal de datos (automático)
3. **Conexión P2P directa**: Sin intermediarios que puedan leer tus mensajes
4. **Sin almacenamiento**: Los mensajes solo existen en memoria

### Tecnología PeerJS:
- **Servidor de señalización**: Solo se usa para establecer la conexión inicial (no ve los mensajes)
- **Conexión directa**: Una vez conectados, los mensajes van de navegador a navegador
- **Sin logs**: Los mensajes nunca pasan por ningún servidor

### Lo que NO se almacena:
- ❌ Mensajes (se pierden al cerrar el navegador)
- ❌ Historial de conversaciones
- ❌ Información de usuario
- ❌ Logs de actividad

## 🚀 Uso Rápido

### Opción 1: Abrir localmente
1. Descarga el archivo `index.html`
2. Abre el archivo en tu navegador (Chrome, Firefox, Edge)
3. ¡Listo!

### Opción 2: Desplegar en GitHub Pages (Recomendado)

#### Paso 1: Crear repositorio
```bash
# Crea un nuevo repositorio en GitHub
# Por ejemplo: "mi-chat-privado"
```

#### Paso 2: Subir el archivo
```bash
git init
git add index.html
git commit -m "Chat P2P inicial"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/mi-chat-privado.git
git push -u origin main
```

#### Paso 3: Activar GitHub Pages
1. Ve a tu repositorio en GitHub
2. Click en `Settings` (Configuración)
3. En el menú lateral, click en `Pages`
4. En `Source`, selecciona `main` branch
5. Click en `Save`
6. Espera 1-2 minutos

Tu chat estará disponible en:
```
https://TU-USUARIO.github.io/mi-chat-privado/
```

## 📖 Cómo Usar el Chat

### Flujo super simple en 3 pasos:

**Paso 1: Ingresa tu nombre**
- Abre el chat en tu navegador
- Escribe tu nombre
- Click "Continuar"

**Paso 2a: Si quieres CREAR una sala**
1. Click en "🔑 Crear nueva sala"
2. Se genera automáticamente una contraseña de 4 caracteres (ej: "K2M9")
3. Click en "📋 Copiar contraseña"
4. Comparte esa contraseña con tu contacto (WhatsApp, email, etc.)
5. Click "Continuar"
6. Espera a que tu contacto se una

**Paso 2b: Si quieres UNIRTE a una sala**
1. Click en "🚪 Unirme a una sala"
2. Pega la contraseña que te compartieron (ej: "K2M9")
3. Click "Unirse"
4. ¡Listo! Se conectará automáticamente

**Paso 3: ¡A chatear!**
- Verás un mensaje cuando tu contacto se una
- Los mensajes se envían en tiempo real
- Todo está cifrado automáticamente

### 📝 Notas importantes:
- ✅ Ambas personas deben estar online simultáneamente
- ✅ La contraseña es de solo 4 caracteres (fácil de compartir)
- ✅ Solo 2 personas por sala
- ❌ No hay historial (se pierde al cerrar el navegador)
- ❌ Para nueva conversación, crear nueva sala

## 🛠️ Cómo Funciona

### Tecnología: PeerJS + WebRTC

PeerJS simplifica el uso de WebRTC para conexiones P2P:

```
Navegador A  ←→  Servidor PeerJS  ←→  Navegador B
   (tú)         (solo señalización)      (contacto)
                        ↓
                Conexión establecida
                        ↓
Navegador A  ←――――――――――――――――――――→  Navegador B
   (tú)      Conexión P2P directa      (contacto)
              (mensajes cifrados)
```

### Flujo de conexión:

1. **Pantallas de usuario**:
   - Nombre → Crear/Unirse → Chat

2. **Crear sala**:
   - Se genera contraseña aleatoria de 4 caracteres
   - Esta contraseña es el "Peer ID"
   - El host se registra en el servidor PeerJS con ese ID

3. **Unirse a sala**:
   - El cliente introduce la contraseña
   - Se conecta al Peer ID correspondiente
   - Servidor PeerJS facilita el intercambio de información

4. **Conexión P2P establecida**:
   - Los navegadores negocian conexión directa
   - Una vez establecida, el servidor PeerJS ya no participa
   - Los mensajes van directamente entre navegadores
   - Todo cifrado con WebRTC (DTLS + SRTP)

### Servidores usados:

- **Servidor PeerJS público** (0.peerjs.com):
  - Solo para señalización inicial
  - Ayuda a establecer la conexión P2P
  - NO ve ni almacena mensajes
  - Gratuito y de código abierto

## 🔒 Estado del Cifrado Postcuántico

**Actualización Febrero 2025:**
- WebRTC usa DTLS 1.3 que soporta cipher suites postcuánticos
- Los navegadores modernos (Chrome 137+, Firefox 123+) ya tienen soporte preliminar
- El cifrado actual (ECDHE + AES-256) sigue siendo muy seguro

## 🌟 Mejoras Futuras Posibles

### Versión avanzada con características adicionales:
- [ ] Videollamadas P2P
- [ ] Compartir archivos
- [ ] Múltiples participantes (rooms)
- [ ] Persistencia con IndexedDB (local)
- [ ] Capa adicional de cifrado AES-256 personalizado
- [ ] QR codes para compartir códigos fácilmente
- [ ] Tema oscuro

## 🔧 Personalización

### Cambiar servidor PeerJS:
Si quieres usar tu propio servidor PeerJS, edita esta línea en el código:
```javascript
peer = new Peer(id, {
    host: '0.peerjs.com',  // Cambia esto
    secure: true,
    port: 443
});
```

### Servidores PeerJS públicos alternativos:
- PeerJS oficial: `0.peerjs.com`
- Puedes montar tu propio servidor: https://github.com/peers/peerjs-server

### Cambiar longitud de contraseña:
Busca la función `generatePassword()` y cambia el número:
```javascript
for (let i = 0; i < 4; i++) {  // Cambia 4 por el número que quieras
```

### Cambiar colores:
Busca en el CSS la sección de gradientes:
```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

## ❓ Preguntas Frecuentes

**P: ¿Es realmente seguro?**
R: Sí. WebRTC usa cifrado DTLS-SRTP por estándar. Los mensajes van directo entre navegadores. El servidor PeerJS solo ayuda a establecer la conexión inicial, no ve los mensajes.

**P: ¿Necesito instalar algo?**
R: No. Solo un navegador moderno (Chrome, Firefox, Edge, Safari).

**P: ¿Funciona en móviles?**
R: Sí, perfectamente en Chrome y Safari móvil.

**P: ¿Puedo chatear con alguien en otra red/país?**
R: Sí, funciona entre cualquier red del mundo.

**P: ¿Se guardan los mensajes?**
R: No. Todo está en memoria. Al cerrar el navegador, se pierde todo.

**P: ¿Necesito cuenta o registro?**
R: No. Solo un nombre (que puede ser inventado) y listo.

**P: ¿La contraseña es segura con solo 4 caracteres?**
R: Es suficiente para uso casual. Con 36 caracteres posibles (A-Z, 0-9) hay 1,679,616 combinaciones. Para más seguridad, puedes modificar el código para usar más caracteres.

**P: ¿Qué pasa si dos personas usan la misma contraseña?**
R: El segundo usuario que intente crear una sala con la misma contraseña verá un error. Cada contraseña puede usarse solo una vez por sesión.

**P: ¿Qué pasa si cierra uno de los navegadores?**
R: Se desconecta la conversación. Hay que crear una nueva sala para reconectar.

**P: ¿Pueden chatear más de 2 personas?**
R: En esta versión básica, no. Pero PeerJS soporta múltiples conexiones, así que es posible implementarlo.

**P: ¿Funciona sin internet?**
R: No. Se necesita internet para conectar al servidor PeerJS y establecer la conexión P2P.

## 🆚 Comparación con otras soluciones

| Característica | Este Chat | Signal/WhatsApp | Matrix Server | Discord |
|---|---|---|---|---|
| Sin servidor propio | ✅ | ❌ | ❌ | ❌ |
| Sin registro | ✅ | ❌ | ❌ | ❌ |
| Sin abrir puertos | ✅ | ✅ | ❌ | ✅ |
| Cifrado E2E | ✅ | ✅ | ✅ | ❌ |
| Gratis | ✅ | ✅ | ✅ | ✅ |
| Historial | ❌ | ✅ | ✅ | ✅ |
| Apps móviles nativas | ❌ | ✅ | ✅ | ✅ |
| Múltiples usuarios | ❌ | ✅ | ✅ | ✅ |
| Setup en 5 min | ✅ | ❌ | ❌ | ✅ |
| Open source | ✅ | Parcial | ✅ | ❌ |

## 📝 Licencia

MIT License - Usa, modifica y comparte libremente.

## 🤝 Contribuciones

¿Ideas para mejorar? ¡Pull requests bienvenidos!

## ⚠️ Disclaimer

Este es un proyecto educativo. Para uso en producción con requisitos críticos de seguridad, considera soluciones profesionales auditadas como Signal o Matrix con servidores propios.

## 📚 Recursos Adicionales

- **PeerJS Documentation**: https://peerjs.com/docs/
- **PeerJS Server (para autoalojar)**: https://github.com/peers/peerjs-server
- **WebRTC Documentation**: https://webrtc.org/
- **MDN WebRTC Guide**: https://developer.mozilla.org/en-US/docs/Web/API/WebRTC_API

---

**Hecho con ❤️ para la privacidad digital**
