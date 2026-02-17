
# C2-Hunter-Engine 🛡️
---
**C2-Hunter-Engine** es una herramienta de **Threat Intelligence** desarrollada en Python para la auditoría y análisis avanzado de reputación de red. Está diseñada para identificar infraestructuras maliciosas, detectar técnicas de evasión como el "Cloud Masking" y correlacionar indicadores de compromiso (IOCs) en tiempo real.

## 🚀 Capacidades Principales

* **Análisis de Reputación Estricto**: Evalúa IPs mediante la API de AbuseIPDB utilizando un motor de puntuación basado en la confianza y frecuencia de reportes.
* **Detección de Cloud Masking**: Realiza resolución inversa (rDNS) para alertar si un atacante intenta ocultar su actividad tras servicios legítimos como AWS, Azure o Google Cloud.
* **Capa de Inteligencia C2**: Contrasta hostnames contra una lista negra dinámica de dominios de Comando y Control (C2) actualizados.
* **Reportes para SOC**: Genera archivos Excel detallados con niveles de criticidad y notas técnicas listas para la gestión de incidentes.

## 🛠️ Configuración de Seguridad

Para proteger tu infraestructura y llaves de acceso, el motor utiliza **variables de entorno**.

1. **Instalación de dependencias**:
```bash
pip install requests pandas openpyxl

```


2. **Configuración de la API Key**:
Crea un archivo `.env` en la raíz del proyecto (este archivo está excluido por el `.gitignore` por seguridad):
```text
ABUSEIPDB_KEY=tu_api_key_aqui

```


## 📊 Niveles de Decisión

| Nivel | Acción Sugerida | Criterio |
| --- | --- | --- |
| **💀 C2 CONFIRMADO** | 🔴 Bloqueo Inmediato / Aislar | Coincidencia exacta con dominio malicioso. |
| **CRÍTICO** | 🔴 Bloquear / DROP | Confianza de abuso > 80%. |
| **ALTO** | 🟠 Investigar | Actividad sospechosa detectada en los últimos 90 días. |
| **BAJO** | 🟢 Allow | Sin reportes significativos de abuso. |

---

**Nota**: Este proyecto es para fines de investigación y fortalecimiento de posturas de seguridad. No utilizar para fines no autorizados.

---

¿Te gustaría que te ayude a crear el archivo `.gitignore` para asegurar que tu repo esté 100% blindado antes de subirlo?
