## 🧪 Forense Linux

Enlace al libro: https://goo.su/qSdaC5

Esta sección contiene los **scripts, utilidades y recursos prácticos** asociados al libro **Forense Linux**, cuyo objetivo es proporcionar una **aproximación rigurosa, técnica y reproducible al análisis forense en sistemas GNU/Linux**.

El contenido aquí recopilado está diseñado para acompañar al lector en la **aplicación práctica de técnicas forenses reales**, cubriendo desde la adquisición de evidencias hasta su análisis y correlación, siempre bajo criterios de **integridad, trazabilidad y validez técnica**.

Los scripts y herramientas incluidos permiten:
- Automatizar tareas repetitivas en procesos forenses.
- Estandarizar procedimientos de análisis.
- Reducir el error humano durante la adquisición y el tratamiento de evidencias.
- Facilitar la comprensión práctica de los conceptos explicados en el libro.

Todo el material se ha desarrollado siguiendo principios fundamentales del análisis forense digital:
- **No alteración de la evidencia**
- **Reproducibilidad de los resultados**
- **Documentación exhaustiva del proceso**
- **Separación clara entre adquisición y análisis**

Cada herramienta que se liste a continuación estará acompañada, cuando corresponda, de:
- Descripción técnica de su propósito.
- Contexto de uso dentro de una investigación forense.
- Advertencias y limitaciones.
- Referencias al capítulo del libro donde se explica su uso.

> ⚠️ **Aviso importante**  
> Los scripts y herramientas de esta sección deben utilizarse **exclusivamente en entornos controlados, sistemas propios o con autorización expresa**. Su uso indebido puede comprometer evidencias o vulnerar la legislación vigente.

Esta sección se irá ampliando y actualizando conforme evolucione el contenido del libro y las técnicas forenses en entornos Linux.



# Linux Forensic Triage
**DFIR Live Response Script – Usage Guide**



## Descripción

`linux_triage.sh` es un **script de triaje forense para sistemas Linux** diseñado para **respuestas rápidas ante incidentes de seguridad**.  
Permite recoger evidencia relevante en sistemas en funcionamiento (*live response*), de forma **estructurada, trazable y con control de integridad**.

Este script está pensado como **primera acción DFIR**, no como sustituto de un análisis forense completo.



## Objetivos del triaje

- Obtener una **visión rápida del estado del sistema**
- Identificar **indicadores tempranos de compromiso (IOCs)**
- Preservar evidencia para análisis posterior
- Facilitar decisiones rápidas en fases iniciales del incidente



## Requisitos

- Sistema Linux (probado en Debian/Ubuntu/RHEL/Rocky/Alma)
- Shell: `bash`
- Ejecución recomendada como **root**
- Utilidades estándar del sistema (`ps`, `ip`, `ss`, `find`, `tar`, etc.)

> No requiere instalación de dependencias externas.



## Advertencia importante

**La ejecución en vivo modifica el sistema** (lecturas, procesos, accesos a disco).  
Esto es inherente al *live response* y debe documentarse correctamente.



## Instalación

Clona el repositorio o copia el script:

git clone https://github.com/<usuario>/dfir-linux-toolkit.git

---

# DFIR Timeline Generator (Linux)
**timeline.sh – Forensic Timeline Creation**



## Descripción

`timeline.sh` es un **script de generación de timelines forenses para sistemas Linux**, diseñado para **análisis post-triaje** dentro de procesos de **Digital Forensics & Incident Response (DFIR)**.

Su objetivo es **correlacionar eventos en el tiempo** (filesystem, logs, procesos y autenticación) para facilitar la **reconstrucción de la actividad del sistema** durante un incidente de seguridad.

El script genera un **timeline unificado en formato CSV**, fácil de analizar con herramientas estándar (Excel, Timesketch, Splunk, Elastic, etc.).



## Objetivos del timeline

- Reconstruir cronológicamente la actividad del sistema
- Correlacionar artefactos procedentes del triaje forense
- Identificar **patrones de ataque**, persistencia y movimientos laterales
- Apoyar la toma de decisiones durante la investigación



## Requisitos

- Sistema Linux
- `bash`
- Utilidades estándar:
  - `find`
  - `stat`
  - `date`
  - `awk`
  - `ps`
  - `last`
  - `journalctl` (si systemd)
- Ejecución recomendada como **root**

> No requiere dependencias externas.



## Advertencia importante

**El timeline no indicated causalidad ni culpabilidad**, únicamente correlación temporal.  
Debe interpretarse siempre junto con otras evidencias DFIR.



## Instalación

Ubicar el script dentro del repositorio DFIR:

chmod +x timeline.sh

---

# acquire_disk_memory.sh

Script de **adquisición forense primaria** para sistemas GNU/Linux que permite realizar:

- 📀 **Copia bit a bit de un disco** (adquisición física)
- 🧠 **Captura opcional de memoria RAM** mediante LiME
- 🔐 **Verificación criptográfica** de las evidencias generadas
- 📝 **Registro detallado del proceso** para trazabilidad forense

Este script está diseñado como herramienta de apoyo al libro **Forense Linux** y sigue principios básicos de **informática forense defensiva**.

---

## 🎯 Objetivo forense

El propósito de este script es **preservar evidencias digitales** minimizando la alteración del sistema y generando artefactos verificables que puedan ser utilizados en:

- Análisis forense técnico
- Investigación de incidentes
- Laboratorios docentes
- Ejercicios de entrenamiento forense

La adquisición se realiza siguiendo un enfoque **best effort**, priorizando:
- Integridad de la evidencia
- Reproducibilidad
- Documentación automática del proceso

---

## ⚙️ Funcionalidades principales

- Adquisición completa de dispositivos de bloque (`dd` bit a bit)
- Registro de:
  - Modelo y número de serie del dispositivo
  - Tamaño exacto en bytes
  - Marca temporal UTC
- Cálculo de **hash SHA-256** de todas las evidencias
- Captura opcional de memoria RAM usando **LiME**
- Separación clara entre evidencias, logs y hashes

---

## 📋 Requisitos

### Generales
- Ejecución como **root**
- Sistema GNU/Linux
- Espacio suficiente en el directorio de salida

### Comandos requeridos
- `dd`
- `sha256sum`
- `lsblk`
- `blockdev`
- `insmod` (solo si se captura memoria)
- `lsmod` (solo si se captura memoria)

### Captura de memoria
- Módulo **LiME (`lime.ko`)** compilado para el kernel en ejecución

---

## 🚀 Uso

sudo ./acquire_disk_memory.sh --disk /dev/sdX --out /ruta/salida


