# 🔐 Chat P2P Cifrado - Sin Servidor

Un chat seguro y privado que funciona completamente en el navegador, sin necesidad de servidores, backends ni bases de datos.

## ✨ Características

- **🔒 Cifrado de extremo a extremo**: Usa DTLS-SRTP (estándar WebRTC) + conexión P2P directa
- **🚫 Sin servidor**: No hay backend, no hay almacenamiento, no hay logs
- **🌐 Solo navegador**: Todo funciona en HTML/JavaScript vanilla
- **📱 Responsive**: Funciona en escritorio y móvil
- **🎨 Interfaz moderna**: Diseño limpio y fácil de usar
- **⚡ Tiempo real**: Mensajes instantáneos sin latencia de servidor
- **🆓 Gratis**: Usa servidores STUN públicos de Google
- **📦 Un solo archivo**: Todo en un HTML de 15KB

## 🔐 Seguridad

### Cifrado multicapa:
1. **DTLS 1.2/1.3**: Cifrado de transporte WebRTC (automático)
2. **SRTP**: Cifrado de medios (automático)
3. **Conexión P2P directa**: Sin intermediarios, sin servidores que puedan espiar
4. **Sin almacenamiento**: Los mensajes solo existen en memoria del navegador

### Lo que NO se almacena:
- ❌ Mensajes
- ❌ Metadatos
- ❌ IPs (excepto temporalmente para establecer conexión)
- ❌ Logs de conversación
- ❌ Información de usuario

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

### Para iniciar una conversación:

**Persona A (Host):**
1. Abre el chat en tu navegador
2. Click en "Crear nueva sala"
3. Se generará un código
4. Copia el código (botón "📋 Copiar código")
5. Envía el código a tu contacto por cualquier medio (WhatsApp, email, etc.)
6. Espera a que tu contacto te envíe su código de respuesta
7. Pega el código de respuesta en el campo correspondiente
8. Click en "Conectar"
9. ¡Listo! Ya pueden chatear

**Persona B (Cliente):**
1. Abre el chat en tu navegador
2. Click en "Unirse a sala existente"
3. Pega el código que recibiste de tu contacto
4. Click en "Generar código de respuesta"
5. Copia el código generado
6. Envía este código a tu contacto
7. ¡Listo! Ya pueden chatear

### Notas importantes:
- Ambas personas deben estar online simultáneamente
- Si se cierra el navegador, se pierde la conversación (no hay historial)
- Para una nueva conversación, hay que generar nuevos códigos

## 🛠️ Cómo Funciona

### Tecnología WebRTC
WebRTC (Web Real-Time Communication) permite comunicación P2P directa entre navegadores:

```
Navegador A  ←→  Navegador B
   (tú)            (contacto)
```

### Flujo de conexión:

1. **Señalización manual**: 
   - Los códigos que se intercambian son "descripciones SDP"
   - Contienen información para establecer la conexión P2P
   - Se intercambian manualmente (no hay servidor de señalización)

2. **Servidor STUN**:
   - Solo se usa para descubrir tu IP pública
   - Ayuda a atravesar NAT/firewalls
   - Es público y no ve tus mensajes

3. **Conexión directa**:
   - Una vez establecida, los mensajes van directo entre navegadores
   - Cifrados con DTLS-SRTP (estándar WebRTC)
   - El servidor STUN ya no participa

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

### Cambiar servidores STUN:
Edita la variable `iceServers` en el código:
```javascript
const iceServers = [
    { urls: 'stun:stun.l.google.com:19302' },
    // Agrega más servidores STUN aquí
];
```

### Servidores STUN públicos gratuitos:
- Google: `stun:stun.l.google.com:19302`
- Mozilla: `stun:stun.services.mozilla.com`
- OpenRelay: `stun:openrelay.metered.ca:80`

### Cambiar colores:
Busca en el CSS la sección de gradientes:
```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

## ❓ Preguntas Frecuentes

**P: ¿Es realmente seguro?**
R: Sí. WebRTC usa cifrado DTLS-SRTP por estándar. Los mensajes van directo entre navegadores sin pasar por servidores.

**P: ¿Necesito instalar algo?**
R: No. Solo un navegador moderno (Chrome, Firefox, Edge, Safari).

**P: ¿Funciona en móviles?**
R: Sí, perfectamente en Chrome y Safari móvil.

**P: ¿Puedo chatear con alguien en otra red?**
R: Sí, funciona entre cualquier red gracias a los servidores STUN.

**P: ¿Se guardan los mensajes?**
R: No. Todo está en memoria. Al cerrar el navegador, se pierde todo.

**P: ¿Puedo usarlo sin internet?**
R: No. Se necesita internet para la conexión P2P inicial (servidores STUN).

**P: ¿Por qué tengo que intercambiar códigos manualmente?**
R: Para evitar tener un servidor de señalización que podría comprometer la privacidad.

**P: ¿Qué pasa si cierra uno de los navegadores?**
R: Se desconecta la conversación. Hay que generar nuevos códigos para reconectar.

**P: ¿Pueden chatear más de 2 personas?**
R: En esta versión básica, no. Pero es posible implementarlo (ver "Mejoras Futuras").

## 🆚 Comparación con otras soluciones

| Característica | Este Chat | Signal/WhatsApp | Matrix Server | Jitsi |
|---|---|---|---|---|
| Sin servidor propio | ✅ | ❌ | ❌ | ❌ |
| Sin registro | ✅ | ❌ | ❌ | ✅ |
| Sin abrir puertos | ✅ | ✅ | ❌ | ❌ |
| Cifrado E2E | ✅ | ✅ | ✅ | ✅ |
| Gratis | ✅ | ✅ | ✅ | ✅ |
| Historial | ❌ | ✅ | ✅ | ❌ |
| Apps móviles nativas | ❌ | ✅ | ✅ | ✅ |
| Videollamadas | ❌ | ✅ | ❌ | ✅ |

## 📝 Licencia

MIT License - Usa, modifica y comparte libremente.

## 🤝 Contribuciones

¿Ideas para mejorar? ¡Pull requests bienvenidos!

## ⚠️ Disclaimer

Este es un proyecto educativo. Para uso en producción con requisitos críticos de seguridad, considera soluciones profesionales auditadas como Signal o Matrix con servidores propios.

## 📚 Recursos Adicionales

- [WebRTC Documentation](https://webrtc.org/)
- [MDN WebRTC Guide](https://developer.mozilla.org/en-US/docs/Web/API/WebRTC_API)
- [WebRTC Security](https://webrtcsecurity.github.io/)

---

**Hecho con ❤️ para la privacidad digital**
