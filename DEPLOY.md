# 🚀 Guía de 5 Minutos - Desplegar en GitHub Pages

Tu chat P2P estará online en menos de 5 minutos, sin configuración, sin costos.

## Paso 1: Crear cuenta en GitHub (si no tienes)
1. Ve a https://github.com
2. Click en "Sign up"
3. Sigue el proceso de registro

## Paso 2: Crear nuevo repositorio
1. Click en el botón "+" arriba a la derecha
2. Selecciona "New repository"
3. Nombre del repositorio: `mi-chat-privado` (o el que prefieras)
4. Marca "Public"
5. NO marques "Add a README file"
6. Click en "Create repository"

## Paso 3: Subir el archivo

### Opción A: Desde la web (más fácil)
1. En tu nuevo repositorio, click en "uploading an existing file"
2. Arrastra el archivo `index.html` 
3. En "Commit changes", escribe: "Chat inicial"
4. Click en "Commit changes"

### Opción B: Desde la terminal
```bash
# 1. Abre tu terminal en la carpeta donde está index.html
cd ruta/a/tu/carpeta

# 2. Inicializa git
git init

# 3. Añade el archivo
git add index.html

# 4. Haz commit
git commit -m "Chat P2P inicial"

# 5. Conecta con GitHub (reemplaza TU-USUARIO y TU-REPO)
git branch -M main
git remote add origin https://github.com/TU-USUARIO/TU-REPO.git

# 6. Sube los cambios
git push -u origin main
```

## Paso 4: Activar GitHub Pages
1. En tu repositorio, click en "⚙️ Settings"
2. En el menú lateral izquierdo, busca "Pages"
3. En "Source", selecciona `main` (o `master`)
4. Click en "Save"
5. Espera 1-2 minutos

## Paso 5: ¡Accede a tu chat!
Tu URL será:
```
https://TU-USUARIO.github.io/TU-REPOSITORIO/
```

Por ejemplo:
```
https://juanperez.github.io/mi-chat-privado/
```

## 🎉 ¡Listo!
Ahora puedes compartir esta URL con quien quieras para chatear de forma segura.

## 📱 Compartir
- Comparte la URL con tus contactos
- Ellos también podrán acceder sin necesidad de cuenta
- Funciona en cualquier dispositivo con navegador

## 🔄 Actualizar el chat
Si haces cambios al código:

```bash
git add index.html
git commit -m "Descripción del cambio"
git push
```

Espera 1-2 minutos y los cambios estarán en vivo.

## ⚠️ Notas importantes
- El repositorio debe ser "Public" para usar GitHub Pages gratis
- GitHub Pages puede tardar hasta 10 minutos en activarse la primera vez
- Si cambias el nombre del repositorio, cambiará la URL

## 🆘 Problemas comunes

**"404 - Page not found"**
- Verifica que GitHub Pages esté activado en Settings
- Espera unos minutos más, puede tardar
- Asegúrate de que el archivo se llame exactamente `index.html`

**"No aparece la opción Pages en Settings"**
- El repositorio debe ser Public
- Debe haber al menos un commit

**"La página no carga"**
- Verifica la URL: debe ser `https://usuario.github.io/repositorio/`
- Limpia el caché del navegador (Ctrl+F5)

## 💡 Consejos
- Usa un nombre de repositorio fácil de recordar y compartir
- Puedes tener múltiples repositorios con GitHub Pages (un chat por repo)
- Cada repositorio tendrá su propia URL
- Es gratis e ilimitado para repositorios públicos
- Puedes compartir la URL directamente con quien quieras chatear

## 🎉 ¡A usar!

Una vez desplegado:
1. Abre la URL en tu navegador
2. Ingresa tu nombre
3. Crea una sala → Se genera contraseña (ej: "K2M9")
4. Comparte la contraseña con tu contacto
5. Tu contacto abre la misma URL → Unirse → Pega contraseña
6. ¡Listo! Ya están chateando de forma segura

La mejor parte: **tus contactos NO necesitan cuenta de GitHub**, solo la URL que les compartas.
