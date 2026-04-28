# 🏴‍☠️ Hundir la Flota Pirata — App Android

Guía completa para convertir el juego en una app Android instalable.

---

## 📁 Estructura del proyecto

```
hundir-pirata/
├── package.json
├── capacitor.config.json
├── README.md
└── www/
    └── index.html   ← aquí va el archivo del juego (hundir_la_flota_pirata.html)
```

---

## ✅ Requisitos previos (instalar una sola vez)

| Herramienta | Descarga | Para qué sirve |
|---|---|---|
| Node.js (v18+) | https://nodejs.org | Ejecutar npm y Capacitor |
| Android Studio | https://developer.android.com/studio | Compilar el APK |
| JDK 17 | Incluido con Android Studio | Necesario para compilar |

Después de instalar Android Studio, abre el SDK Manager y asegúrate de tener instalado:
- Android SDK Platform 34
- Android SDK Build-Tools 34

---

## 🚀 Pasos para generar el APK

### 1. Prepara la carpeta del proyecto

```bash
# Crea la carpeta www y copia el HTML del juego dentro
mkdir www
cp /ruta/a/hundir_la_flota_pirata.html www/index.html
```

### 2. Instala las dependencias

```bash
npm install
```

### 3. Añade la plataforma Android

```bash
npx cap add android
```

### 4. Sincroniza los archivos web con Android

```bash
npx cap sync
```

> Ejecuta este comando CADA VEZ que modifiques el HTML del juego.

### 5. Abre Android Studio

```bash
npx cap open android
```

### 6. Genera el APK en Android Studio

En Android Studio:
1. Espera a que Gradle termine de sincronizar (barra de progreso abajo)
2. Menú: **Build → Build Bundle(s) / APK(s) → Build APK(s)**
3. Cuando termine, aparece una notificación abajo a la derecha
4. Haz clic en **"locate"** para encontrar el APK

El APK estará en:
```
android/app/build/outputs/apk/debug/app-debug.apk
```

### 7. Instala en tu móvil Android

Transfiere el `.apk` a tu móvil (por USB, WhatsApp, Drive, email...) y ábrelo.

> En el móvil, puede que necesites activar **"Instalar apps de fuentes desconocidas"** en:
> Ajustes → Seguridad → Instalar apps desconocidas

---

## 🔄 Flujo de trabajo para actualizaciones

Cuando quieras actualizar el juego (cambiar algo en el HTML):

```bash
# 1. Copia el nuevo HTML
cp /ruta/nueva/hundir_la_flota_pirata.html www/index.html

# 2. Sincroniza con Android
npx cap sync

# 3. Vuelve a compilar desde Android Studio
```

---

## 📱 Para subir a Google Play (opcional, más adelante)

Si en el futuro quieres publicarla en Google Play, necesitarás:
1. Crear una cuenta de desarrollador (pago único de ~25€)
2. Generar un APK firmado: Build → Generate Signed Bundle/APK
3. Crear un keystore (Android Studio te guía paso a paso)
4. Subir el APK firmado en https://play.google.com/console

---

## 🐛 Problemas frecuentes

**Error: "ANDROID_HOME not set"**
→ Abre Android Studio, ve a Settings → Android SDK y copia la ruta del SDK. Añádela como variable de entorno `ANDROID_HOME`.

**Error: "Gradle sync failed"**
→ En Android Studio: File → Invalidate Caches → Restart

**El APK no se instala en el móvil**
→ Activa "Fuentes desconocidas" en los ajustes de seguridad del móvil.

---

## ℹ️ Info del proyecto

- Juego original en Python: https://github.com/RobertoCantero82/hundir_la_flota_edicion_pirata
- Versión web/Android: traducción 1:1 de la lógica Python a JavaScript
- Framework: Capacitor 6 (Ionic)
- Compatibilidad: Android 6.0+ (API 23+)
