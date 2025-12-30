## 🧪 Forense Linux

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

## Listado de scripts:

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

```bash
git clone https://github.com/<usuario>/dfir-linux-toolkit.git
