Java Version Manager for PowerShell (Windows)

Mini gestor de versiones de Java para Windows inspirado en SDKMAN, implementado en PowerShell.

Permite:

Detectar automáticamente cualquier JDK instalado

Listar versiones disponibles

Cambiar versión solo en la sesión actual

Establecer versión por defecto (usuario o sistema)

Instalar automáticamente con winget si no está presente

🚀 Características

🔎 Detección automática de JDKs instalados

📦 Instalación automática mediante winget (Eclipse Temurin)

🔄 Cambio de versión en:

Sesión actual

Usuario (persistente)

Máquina completa (requiere admin)

🧼 Limpieza automática del PATH

🖥 Compatible con PowerShell 5+ y PowerShell 7+

📦 Requisitos

Windows 10/11

PowerShell

winget disponible en el sistema

Comprobar winget:

winget --version
📁 Instalación
1️⃣ Abrir el perfil de PowerShell
notepad $PROFILE

Si el perfil no existe:

New-Item -ItemType File -Path $PROFILE -Force
2️⃣ Copiar el script completo dentro del perfil

Guardar y cerrar.

3️⃣ Reiniciar PowerShell

Cerrar todas las terminales y abrir una nueva.

🛠 Uso
Listar JDKs detectados
switch-java list
Ver versión actual
switch-java current
Cambiar versión (solo sesión actual)
switch-java 21

Por defecto el scope es Session.

Cambiar versión persistente para el usuario
switch-java 21 -Scope User

Requiere cerrar y abrir terminal.

Cambiar versión para todo el sistema
switch-java 21 -Scope Machine

Requiere PowerShell en modo Administrador.

⚙️ Alcances disponibles
Scope	Persistencia	Requiere Admin
Session	No	No
User	Sí (usuario)	No
Machine	Sí (global)	Sí
📦 Instalación automática

Si ejecutas:

switch-java 17

Y Java 17 no está instalado, el script intentará instalar:

EclipseAdoptium.Temurin.17.JDK

usando:

winget install --id EclipseAdoptium.Temurin.17.JDK -e
🔍 Cómo funciona la detección

El script:

Busca en:

C:\Program Files\Eclipse Adoptium

C:\Program Files\Java

C:\Program Files\Microsoft

Verifica que exista:

bin\java.exe

Ejecuta:

java -version

Extrae la versión real automáticamente.

No depende del nombre de la carpeta.

🧠 Casos de uso recomendados
Desarrollo moderno (Java 21 principal)
switch-java 21 -Scope User
Proyecto legacy puntual
switch-java 8
Servidor o máquina de build
switch-java 21 -Scope Machine
🧹 Notas importantes

El cambio en User o Machine requiere reiniciar la terminal.

El modo Machine necesita PowerShell como Administrador.

El script limpia automáticamente rutas Java antiguas del PATH.

🔮 Posibles mejoras futuras

Soporte para múltiples vendors (Oracle, Microsoft, etc.)

Detección automática por proyecto (.java-version)

Cambio automático al hacer cd

Alias rápidos (j8, j21)

Autocompletado dinámico de versiones

Exportación como módulo PowerShell

📄 Licencia

Uso libre para entornos personales y profesionales.
