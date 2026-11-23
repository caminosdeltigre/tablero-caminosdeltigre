# Caminos del Tigre · Tablero (versión para GitHub Pages)

Archivos:
- **index.html**: el tablero completo (portafolio, fichas, mapas, hitos, compromisos, riesgos, fotos, modo presentación, PDF, PowerPoint, matriz Excel). Trae los datos con corte al 23-nov-2026.
- **config.js**: define si el tablero funciona en modo local o compartido.
- **firestore.rules**: reglas de seguridad para el modo compartido.

## 1. Publicarlo en GitHub Pages
1. En github.com: «+» › «New repository». Nombre: `caminos-del-tigre`. Marque «Public» y «Add a README file». «Create repository».
2. «Add file» › «Upload files». Arrastre **index.html** y **config.js** (los dos). «Commit changes».
3. «Settings» › «Pages». En «Branch» elija `main` y `/ (root)`. «Save».
4. En 1 o 2 minutos aparece el enlace: `https://SU-USUARIO.github.io/caminos-del-tigre/`.

Así ya funciona en **modo local**: se puede editar todo, pero los cambios quedan solo en el navegador de cada persona.
Para pasar datos de un equipo a otro: «Descargar respaldo» en uno y «Restaurar respaldo» en el otro.

## 2. Modo compartido (todos ven y editan lo mismo) · Firebase, plan gratuito
1. Entre a https://console.firebase.google.com con una cuenta de Google › «Crear un proyecto» (`caminos-del-tigre`). Puede desactivar Google Analytics.
2. **Base de datos**: menú «Compilación» › «Firestore Database» › «Crear base de datos». Ubicación: la más cercana (por ejemplo `southamerica-east1` o `us-east1`). Inicie en **modo de producción**.
   Luego, pestaña «Reglas»: pegue el contenido de **firestore.rules** y «Publicar».
3. **Inicio de sesión**: «Compilación» › «Authentication» › «Comenzar». Active **Google** y **Correo electrónico/contraseña**.
   En «Configuración» › «Dominios autorizados» › «Agregar dominio»: `SU-USUARIO.github.io`.
4. **Configuración**: ícono de engranaje › «Configuración del proyecto» › «Tus apps» › ícono `</>` (web) › registre la app (sin Hosting). Copie el bloque `firebaseConfig`.
5. Abra **config.js**, reemplace `null` por ese bloque (vea el ejemplo dentro del archivo) y vuelva a subirlo a GitHub («Add file» › «Upload files» › «Commit changes»).
6. Abra el enlace, ingrese y presione **«Cargar datos iniciales»** (aparece una sola vez, cuando la base está vacía).

Recomendado: limitar el acceso a correos del INVÍAS (instrucción dentro de firestore.rules).

## Actualizar el tablero
Para una versión nueva del tablero, suba el nuevo **index.html** con el mismo nombre. En modo compartido los datos no se pierden, porque viven en Firebase.

## Notas
- Fotos y mapas se guardan comprimidos dentro de la base (no requiere Firebase Storage).
- Al ser un repositorio público, cualquiera puede ver el código y los datos iniciales que trae index.html. En modo compartido, los datos actualizados solo los ven usuarios con sesión.
