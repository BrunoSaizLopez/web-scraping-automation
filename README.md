# 🕷️ Web Scraping Automation

> Sistema automatizado de extracción de datos web para captura, procesamiento y exportación de información de catálogos, licitaciones, ofertas comerciales y cualquier fuente web estructurada.

---

## 📋 Descripción del proyecto

Este proyecto implementa un **pipeline de scraping automatizado** que accede a portales web (incluyendo sitios con autenticación y sesiones), extrae información relevante de forma sistemática, la procesa con IA cuando es necesario y la exporta a los sistemas de destino del cliente.

El sistema está diseñado para ejecutarse de forma recurrente y desatendida, notificando al equipo con los resultados de cada ejecución.

---

## 🎯 Casos de uso

- **Seguimiento de licitaciones y proyectos** — Monitorización de portales de contratación pública o privada para detectar nuevas oportunidades relevantes.
- **Exportación de catálogos** — Extracción periódica de catálogos de productos, precios y disponibilidad de proveedores o competidores.
- **Agregación de datos de mercado** — Consolidación de información dispersa en múltiples webs en una única fuente estructurada.
- **Alertas de nuevas publicaciones** — Detección y notificación de nuevos registros que cumplan criterios de interés.

---

## 🏗️ Arquitectura general

```
Trigger programado / manual
        │
        ▼
  Plataforma de automatización
        │
        ▼
  Motor de scraping (navegador headless)
        │
   ┌────┴────────────────────────┐
   │                             │
Autenticación              Extracción de datos
en portal web              (paginación, filtros)
   │                             │
   └────────────┬────────────────┘
                ▼
       Procesamiento / limpieza
                │
        ┌───────┴───────┐
        │               │
   Análisis IA     Estructuración
   (opcional)      de datos
        │               │
        └───────┬───────┘
                ▼
         Destino de salida
     ┌──────────┴──────────┐
     │                     │
Google Sheets /        Email de resumen
Base de datos          con resultados
```

### Componentes principales

| Componente | Rol |
|-----------|-----|
| Scheduler | Disparo periódico del proceso (diario, semanal, etc.) |
| Navegador headless | Renderizado completo de páginas web con soporte JavaScript |
| Gestor de sesión | Login y mantenimiento de sesión autenticada en portales |
| Extractor | Navegación por el sitio y captura de datos por selectores |
| Procesador IA | Enriquecimiento o clasificación de datos extraídos (opcional) |
| Exportador | Volcado de datos a Google Sheets, CSV, base de datos, etc. |
| Notificador | Envío de resumen por email con los resultados de la ejecución |

---

## ✨ Funcionalidades destacadas

- 🔐 **Soporte para portales con login** — gestión completa de sesión autenticada
- 🖥️ **Navegador headless con JavaScript** — compatible con webs modernas de una sola página (SPA)
- 📄 **Paginación automática** — recorre múltiples páginas hasta capturar todos los registros
- 🧹 **Limpieza y normalización de datos** — los datos se estructuran y limpian antes de exportar
- 🤖 **Enriquecimiento con IA** (opcional) — clasificación, resumen o extracción semántica de los datos capturados
- 📊 **Exportación directa a hojas de cálculo** — datos listos para usar, sin procesamiento adicional
- 📬 **Notificación automática** con resumen de la ejecución y métricas (registros encontrados, novedades, errores)
- ♻️ **Ejecución recurrente y desatendida** — sin intervención manual una vez configurado

---

## 🔧 Stack tecnológico

- **Orquestación**: plataforma de automatización de flujos (no-code / low-code)
- **Motor de scraping**: navegador headless basado en Chromium con API Puppeteer
- **Procesamiento IA**: API de LLM para análisis semántico de contenido (cuando aplica)
- **Almacenamiento**: Google Sheets como destino principal; adaptable a base de datos
- **Notificaciones**: email automatizado con resumen de resultados

> ℹ️ Los nombres específicos de portales, clientes, credenciales y selectores de producción no se incluyen en este repositorio público por razones de confidencialidad.

---

## 🔑 Aprendizajes técnicos destacados

- Los navegadores headless basados en Puppeteer requieren sintaxis específica distinta a otras bibliotecas de automatización de navegador (Playwright, Selenium).
- El mantenimiento de sesión entre pasos del pipeline es crítico: las cookies y tokens deben propagarse correctamente entre nodos del flujo.
- La paginación dinámica (botones "cargar más" en lugar de URLs paginadas) requiere interacción con el DOM, no solo peticiones HTTP.
- Separar la fase de extracción de la fase de procesamiento/exportación facilita el mantenimiento y la depuración.
- Para webs con autenticación robusta, simular un comportamiento humano (delays entre acciones, user-agent real) mejora la fiabilidad.

---

## 📈 Resultados y beneficios

| Métrica | Impacto |
|--------|---------|
| Tiempo de recopilación | De horas (manual) a minutos (automatizado) |
| Frecuencia | Ejecución configurable: diaria, semanal, bajo demanda |
| Cobertura | 100% de los registros disponibles, sin omisiones por cansancio |
| Formato | Datos directamente utilizables, sin limpieza manual posterior |

---


## ⚠️ Consideraciones éticas y legales

Este proyecto se implementa siempre respetando:
- Los **términos de servicio** del sitio web objetivo
- La normativa de **protección de datos** aplicable (RGPD / LOPD)
- El fichero **robots.txt** del sitio
- Tasas de solicitud **razonables** para no interferir con el servicio

Se recomienda revisar la legalidad del scraping en cada caso de uso específico.

---

## 🚀 Estado del proyecto

![Estado](https://img.shields.io/badge/estado-en%20producción-brightgreen)
![Tipo](https://img.shields.io/badge/tipo-proyecto%20cliente-blue)
![Idioma](https://img.shields.io/badge/idioma-español-orange)

---

## 👤 Autor

**Bruno Sáiz** — Desarrollador e integrador de soluciones de IA  
Especializado en automatización de procesos, scraping y agentes de IA para entornos empresariales.

---

*Este repositorio es de carácter público y orientativo. El código de producción, credenciales, URLs, selectores específicos y nombres de clientes son confidenciales y no están incluidos.*
