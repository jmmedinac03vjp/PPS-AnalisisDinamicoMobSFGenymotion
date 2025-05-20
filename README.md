# Análisis Dinámico de APK con MobSF y Genymotion: InsecureBankv2

Este repositorio documenta el proceso para realizar un análisis dinámico de la aplicación Android vulnerable **InsecureBankv2** usando **Mobile Security Framework (MobSF)** junto con el emulador **Genymotion**.

## Índice

1. [¿Qué es MobSF?](#1-qué-es-mobsf)  
2. [¿Qué es Genymotion?](#2-qué-es-genymotion)  
3. [Obtener InsecureBankv2](#3-obtener-insecurebankv2)  
4. [Instalar Genymotion](#4-instalar-genymotion)  
5. [Emular un dispositivo móvil](#5-emular-un-dispositivo-móvil)  
6. [Ejecutar InsecureBankv2 en el emulador](#6-ejecutar-insecurebankv2-en-el-emulador)  
7. [Instalar MobSF](#7-instalar-mobsf)  
8. [Análisis dinámico de la aplicación](#8-análisis-dinámico-de-la-aplicación)  
9. [Interpretación de los resultados](#9-interpretación-de-los-resultados)

---

## 1. ¿Qué es MobSF?

**Mobile Security Framework (MobSF)** es una herramienta de análisis de seguridad para aplicaciones móviles (Android/iOS/Windows). Permite realizar análisis **estático**, **dinámico** y **basado en API** de forma automatizada.

> Más información: https://mobsf.github.io/docs/

---

## 2. ¿Qué es Genymotion?

**Genymotion** es un emulador de Android que permite ejecutar máquinas virtuales de diferentes versiones y dispositivos. Es muy útil para realizar pruebas de seguridad móvil en entornos controlados.

> Sitio oficial: https://www.genymotion.com/

---

## 3. Obtener InsecureBankv2

InsecureBankv2 es una aplicación vulnerable con fines educativos.

```bash
git clone https://github.com/dineshshetty/Android-InsecureBankv2.git
```

Compila el APK con Android Studio o utiliza una versión ya compilada si está disponible.

---

## 4. Instalar Genymotion

1. Regístrate en [Genymotion](https://www.genymotion.com/account/create/).
2. Descarga la versión para tu sistema operativo.
3. Instálalo y, si es necesario, también VirtualBox.
4. Inicia sesión con tu cuenta de Genymotion.

---

## 5. Emular un dispositivo móvil

1. Crea una nueva máquina virtual Android (preferiblemente Android 7.0 o superior con ARM o x86).
2. Asegúrate de que tenga habilitado **ADB**.
3. Inicia la máquina virtual.

---

## 6. Ejecutar InsecureBankv2 en el emulador

1. Usa `adb` para instalar el APK en el emulador:
```bash
adb install InsecureBankv2.apk
```

2. Verifica que la app aparece en el emulador y se puede abrir correctamente.

---

## 7. Instalar MobSF

### Opción recomendada: Docker

```bash
git clone https://github.com/MobSF/Mobile-Security-Framework-MobSF.git
cd Mobile-Security-Framework-MobSF
docker build -t mobsf .
docker run -it --privileged -p 8000:8000 mobsf
```

> El modo dinámico necesita que el contenedor tenga acceso a dispositivos de red y a `adb`.

---

## 8. Análisis dinámico de la aplicación

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
