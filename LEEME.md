# Nexora 67 · By Inno-Vsion

Contenido (todo en la raíz, sin carpetas): `index.html`, `manifest.webmanifest`, `sw.js`, los iconos PNG y `.nojekyll`.

## 1. Subir a GitHub y publicar
1. Crea un repositorio (por ejemplo `nexora`) y sube **todo el contenido** de esta carpeta a la raíz, incluido `.nojekyll`.
2. Settings → Pages → Source: *Deploy from a branch* → `main` / `(root)`.
3. Tu app queda en `https://TU-USUARIO.github.io/nexora/`.
   Los archivos usan rutas relativas, así que funciona dentro de esa subcarpeta.

## 2. Probarla como app
Abre el enlace en Chrome (Android) → menú ⋮ → *Instalar app*. Se abre en pantalla completa, sin URL.

## 3. Generar la APK
**Opción fácil: PWABuilder**
1. Entra en pwabuilder.com y pega la URL de GitHub Pages.
2. Revisa que Manifest y Service Worker salgan en verde → *Package for stores* → Android.
3. Pon el id de paquete (ej. `com.innovsion.nexora`), nombre `Nexora 67`, y deja *Display mode* en Fullscreen.
4. Descarga el ZIP: trae el `.apk` firmado para pruebas y el `.aab` para Play Store. **Guarda el archivo de firma (keystore)**: sin él no podrás actualizar la app.
5. Para que no aparezca la barra de URL, sube el `assetlinks.json` que te entrega PWABuilder a `/.well-known/assetlinks.json` (con GitHub Pages de usuario raíz, es decir un repo `TU-USUARIO.github.io`).

**Opción alternativa: Capacitor** (APK local con Android Studio) si prefieres no depender de una URL.

## 4. Al publicar una actualización
Cambia `BUILD` en `sw.js` (ej. `nexora-67-b2`) para que los celulares tomen la versión nueva.

## Sobre "que nada quede expuesto"
- Los datos del negocio se guardan solo en el dispositivo; no hay servidor ni claves dentro del código.
- La app ya trae una política de seguridad (CSP) que bloquea conexiones a sitios no autorizados, silencia la consola y desactiva menú contextual y arrastre.
- Un HTML/JS siempre se puede inspeccionar: la protección real está en no incluir secretos en el código. Si más adelante añades claves de API o pagos, deben ir en un servidor.
