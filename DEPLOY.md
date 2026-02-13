# Guía de Despliegue - SecureP2P v2.7

## Requisitos

- Navegador moderno con soporte para Web Crypto API
- Conexión a internet (para PeerJS signaling)
- GitHub Pages o cualquier hosting estático

## Despliegue en GitHub Pages

### 1. Preparar el repositorio

```bash
# Crear nuevo repositorio
git init
git add .
git commit -m "SecureP2P v2.7 - Initial commit"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/securep2p.git
git push -u origin main
