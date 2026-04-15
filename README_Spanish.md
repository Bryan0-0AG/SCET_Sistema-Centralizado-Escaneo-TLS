# 🔐 TCSS - TLS Centralized Scanning System

> Herramienta de monitoreo y análisis de certificados TLS/SSL para múltiples dominios, con dashboard interactivo y clasificación de riesgos en tiempo real.

---

## 📋 Descripción

**TCSS** es una aplicación Python que centraliza el escaneo de certificados TLS en una lista de dominios, analiza su configuración de seguridad (versión TLS, cifrados, fecha de vencimiento, emisor) y presenta los resultados en un dashboard web interactivo construido con **Plotly Dash**.

El sistema clasifica automáticamente el nivel de riesgo de cada dominio (`BAJO`, `MEDIO`, `ALTO`, `CRÍTICO`) según los cifrados detectados y la proximidad del vencimiento del certificado, permitiendo a equipos de seguridad tomar decisiones rápidas y priorizadas.

---

## 🗂️ Estructura del proyecto

```
TCSS_TLS-Centralized-Scanning-System/
│
├── main.py                  # Punto de entrada — lanza el dashboard en localhost:8050
├── config.py                # Configuración global (puertos, cifrados, colores, rutas)
├── Prueba_paginas.py        # Prototipo de navegación multi-página con Dash
│
├── scanner/                 # Módulo de escaneo TLS
├── domain/                  # Gestión y registro de dominios
├── dashboard/               # Componentes del dashboard Dash
└── storage/
    ├── TLS.SCAN_Domains.csv        # Resultados históricos de escaneos
    └── Registered_Domains.json    # Listado de dominios a monitorear
```

---

## ⚙️ Funcionalidades

- **Escaneo multi-puerto**: Analiza los puertos más relevantes en seguridad (443, 80, 22, 445, 3389, 21, 8080).
- **Clasificación de cifrados**: Detecta automáticamente cifrados inseguros (`RC4`, `DES`, `3DES`, `NULL`, `EXPORT`), moderados (`AES128`, `SHA1`) y seguros (`AES256`, `CHACHA20`, `SHA256`).
- **Niveles de riesgo con colores**: Visualización intuitiva con código de color por nivel de riesgo.
- **Dashboard interactivo**: Interfaz web con tabla de resultados, filtros y navegación entre secciones (Dashboard, Tabla, Admin).
- **Persistencia de resultados**: Los escaneos se guardan en CSV y JSON para consulta histórica.
- **Zona horaria configurable**: Timestamps ajustados a `America/Bogota` por defecto.

---

## 🚀 Instalación y uso

### Requisitos

- Python 3.8+
- Las siguientes librerías (instalar con `pip`):

```bash
pip install dash plotly pytz
```

### Ejecutar el dashboard

```bash
python main.py
```

Luego abre tu navegador en:

```
http://127.0.0.1:8050
```

---

## 📊 Clasificación de riesgos

| Nivel    | Color       | Criterio                                      |
|----------|-------------|-----------------------------------------------|
| BAJO     | 🟢 Verde    | Cifrados seguros, certificado vigente          |
| MEDIO    | 🟡 Naranja  | Cifrados moderados o vencimiento próximo       |
| ALTO     | 🟠 Naranja oscuro | Cifrados débiles detectados              |
| CRÍTICO  | 🔴 Rojo     | Cifrados inseguros o certificado vencido       |

---

## 📁 Almacenamiento de datos

Los resultados se guardan automáticamente con las siguientes columnas:

| Columna        | Descripción                            |
|----------------|----------------------------------------|
| Dominio        | Nombre del dominio escaneado           |
| Fecha scan     | Fecha y hora del escaneo               |
| TLS            | Versión del protocolo TLS detectada    |
| Vence en       | Días restantes para vencimiento        |
| Emisor         | Autoridad certificadora (CA)           |
| Cifrado        | Suite de cifrado detectada             |
| Riesgo         | Nivel de riesgo clasificado            |
| Observaciones  | Notas adicionales del análisis         |

---

## 🛠️ Tecnologías utilizadas

- **Python** — Lenguaje principal
- **Plotly Dash** — Framework para el dashboard web interactivo
- **pytz** — Manejo de zonas horarias
- **CSV / JSON** — Almacenamiento liviano de resultados

---

## 📄 Licencia

Este proyecto está bajo la licencia **MIT**. Consulta el archivo [LICENSE](LICENSE) para más detalles.

---

## 👤 Autor

**Bryan0-0AG**  
Proyecto personal de ciberseguridad y monitoreo de infraestructura TLS.