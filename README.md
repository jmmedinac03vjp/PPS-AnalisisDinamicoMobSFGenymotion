# Análisis Dinámico de APK con MobSF y Genymotion: InsecureBankv2

Este repositorio documenta el proceso para realizar un análisis dinámico de la aplicación Android vulnerable **InsecureBankv2** usando **Mobile Security Framework (MobSF)** junto con el emulador **Genymotion**.

## Índice

1. [¿Qué es MobSF?](#1-qué-es-mobsf)  
2. [Obtener InsecureBankv2](#2-obtener-insecurebankv2)  
3. [Instalar MobSF](#3-instalar-mobsf)  
4. [Acceder a MobSF](#4-Acceder-a-mobsf)  
5. [¿Qué es Genymotion?](#5-qué-es-genymotion)  
6. [Instalar Genymotion](#6-instalar-genymotion)  
7. [Emular un dispositivo móvil](#7-emular-un-dispositivo-móvil)  
8. [Ejecutar InsecureBankv2 en el emulador](#8-ejecutar-insecurebankv2-en-el-emulador)  
9. [Análisis dinámico de la aplicación](#9-análisis-dinámico-de-la-aplicación)  
9.  [Interpretación de los resultados](#10-interpretación-de-los-resultados)

---
## 1. ¿Qué es MobSF?

**Mobile Security Framework (MobSF)** es una herramienta automatizada todo en uno para análisis de seguridad de aplicaciones móviles (Android/iOS/Windows). MobSF permite realizar análisis **estático**, **dinámico** y **basado en API**, y está especialmente diseñado para pruebas de seguridad móviles en entornos DevSecOps.

### Características principales:

- Análisis estático de APK, AAB, IPA y código fuente.
- Análisis dinámico (sandbox automatizado).
- Análisis de binarios y API REST.
- Informes detallados de seguridad y recomendaciones.

> Sitio oficial: https://mobsf.github.io/docs/

---

## 2. Obtener InsecureBankv2

**InsecureBankv2** es una aplicación vulnerable desarrollada con fines educativos para practicar análisis y explotación de fallos en apps móviles.

### Pasos:

1. Clona el repositorio oficial:
   ```bash
   git clone https://github.com/dineshshetty/Android-InsecureBankv2.git
   ```

2. Compila el APK con Android Studio o utiliza una versión precompilada (si está disponible).
  Puedes descargarla desde el repositorio git del desarrollador: <https://github.com/dineshshetty/Android-InsecureBankv2/blob/master/InsecureBankv2.apk>
> ⚠️ **Nota:** Esta aplicación es intencionadamente insegura. No la instales en dispositivos personales o en entornos de producción.

---

## 3. Instalar MobSF

Puedes ejecutar MobSF localmente utilizando Docker o de forma manual. A continuación, se muestra el método recomendado (Docker):

### Opción 1: Usar Docker (recomendado)

```bash
git clone https://github.com/MobSF/Mobile-Security-Framework-MobSF.git
cd Mobile-Security-Framework-MobSF
docker build -t mobsf .
docker run -it -p 8000:8000 mobsf
```

También puedes hacerlo directamente  levantando la imagen de dockerhub:

```bash
docker run -it --rm -p 8000:8000 opensecurity/mobile-security-framework-mobsf:latest
```
![](images/image1.png)

Como hemos creado un contenedor interactivo, `docker run -it`, el terminal quedará abierto. En él podremos ver

### Opción 2: Instalación manual

Sigue la guía oficial en: https://mobsf.github.io/docs/#/installation

---

## 4. Acceder a MobSF

Una vez iniciado MobSF (ya sea por Docker o manualmente), accede a través de tu navegador:

>  <http://localhost:8000>

En la pantalla de autenticación usamos el usuario `mobsf` y la contraseña por defecto: `mobsf`.

![](images/image2.png)


Verás la interfaz web de MobSF, lista para analizar APKs.

![](images/image3.png)
---

## 5. ¿Qué es Genymotion?

**Genymotion** es un emulador de Android que permite ejecutar máquinas virtuales de diferentes versiones y dispositivos. Es muy útil para realizar pruebas de seguridad móvil en entornos controlados.

> Sitio oficial: https://www.genymotion.com/

---

## 6. Instalar Genymotion

1. Regístrate en [Genymotion](https://www.genymotion.com/account/create/).
2. Descarga la versión para tu sistema operativo.
3. Instálalo y, si es necesario, también VirtualBox.
4. Inicia sesión con tu cuenta de Genymotion.

---

## 7. Emular un dispositivo móvil

1. Crea una nueva máquina virtual Android (preferiblemente Android 7.0 o superior con ARM o x86).
2. Asegúrate de que tenga habilitado **ADB**.
3. Inicia la máquina virtual.

---

## 8. Ejecutar InsecureBankv2 en el emulador

1. Usa `adb` para instalar el APK en el emulador:
```bash
adb install InsecureBankv2.apk
```

2. Verifica que la app aparece en el emulador y se puede abrir correctamente.

---

## 9. Análisis dinámico de la aplicación

1. Accede a MobSF en `http://localhost:8000`.
2. Selecciona la opción **Dynamic Analyzer**.
3. Asegúrate de que MobSF detecta el dispositivo emulado vía ADB.
4. Carga el APK de InsecureBankv2.
5. Sigue las instrucciones para iniciar el análisis dinámico.

> MobSF lanzará la app en el emulador y empezará a registrar comportamiento, tráfico, uso de permisos, etc.

---

## 9. Interpretación de los resultados

El informe dinámico incluirá información como:

- **Permisos en tiempo de ejecución**.
- **Tráfico de red y endpoints detectados**.
- **Interacciones con el sistema**.
- **Análisis de logs, broadcasts, servicios, etc.**
- **Captura de tráfico HTTPS (si está configurado con proxy o CA)**.

---

## 📘 Recursos adicionales

- [MobSF Documentation](https://mobsf.github.io/docs/)
- [Genymotion User Guide](https://docs.genymotion.com/)
- [InsecureBankv2 GitHub](https://github.com/dineshshetty/Android-InsecureBankv2)

---

## ⚠️ Disclaimer

Este proyecto es solo para fines educativos. No uses estas herramientas sobre apps sin autorización expresa.

---

## Autor

Repositorio creado por [TuNombre], para prácticas de análisis dinámico de seguridad móvil en el contexto de PPS (Prácticas Profesionales Supervisadas).
