# RNDC — Guías y Normatividad 2026

Repositorio de documentación oficial del **Registro Nacional de Despachos de Carga (RNDC)** del Ministerio de Transporte de Colombia. Contiene normatividad vigente, manuales operativos y guías técnicas en formato Markdown, optimizados para consulta, búsqueda y uso con herramientas RAG/LLM.

---

## Tabla de Contenidos

| # | Documento | Versión | Fecha | Tipo |
|---|-----------|---------|-------|------|
| 1 | [Resolución 16075 de 2026](#1-resolución-16075-de-2026) | — | 29 abr 2026 | Normatividad |
| 2 | [Manual Sistema RNDC](#2-manual-sistema-rndc-2022) | — | ago 2022 | Manual general |
| 3 | [Manifiesto Electrónico de Carga](#3-manifiesto-electrónico-de-carga) | V3 | 12 may 2026 | Guía operativa |
| 4 | [Registro de Remesa](#4-registro-de-remesa) | V4 | abr 2025 | Guía operativa |
| 5 | [Retención FOPAT](#5-retención-fopat) | V2 | 20 abr 2026 | Guía operativa |
| 6 | [Monitoreo de Flota](#6-monitoreo-de-flota) | V8 | 24 feb 2026 | Guía técnica |
| 7 | [Uso del Web Service RNDC](#7-uso-del-web-service-rndc) | V4 | — | Guía técnica |
| 8 | [Consulta SICETAC — Portal y Web Service](#8-consulta-sicetac--portal-y-web-service) | — | ago 2021 | Guía técnica |
| 9 | [Factura Electrónica de Transporte](#9-factura-electrónica-de-transporte) | V11 | — | Guía técnica |
| 10 | [Codificación Sistema Armonizado](#10-codificación-sistema-armonizado) | — | — | Referencia |

---

## Documentos

### 1. Resolución 16075 de 2026

**Archivo:** [`resolucion-rndc-16075-2026.md`](./resolucion-rndc-16075-2026.md)

Resolución **20263040016075** del 29 de abril de 2026, expedida por la Ministra de Transporte. Unifica, compila, armoniza y actualiza toda la normatividad aplicable al RNDC. Es el marco regulatorio vigente que reemplaza y consolida resoluciones anteriores.

**Contenido clave:**
- Marco legal y constitucional del transporte público
- Disposiciones sobre el Registro de Contratación Directa en el RNDC
- Modificaciones al Decreto 1079 de 2015

---

### 2. Manual Sistema RNDC 2022

**Archivo:** [`manual-sistema-rndc-2022.md`](./manual-sistema-rndc-2022.md)

Manual de descripción e instrucciones para la operación general del RNDC, anexo a la Resolución 20223040045515 de agosto de 2022. Documento de referencia para todos los actores del sistema.

**Contenido clave:**
- Generalidades y alcance funcional del sistema
- Roles y actores: empresas de transporte, generadores de carga, conductores
- Canales de comunicación (portal web y web service)
- Creación de usuarios y solicitud de alta (principal, dependiente, facturación, consultas)
- Flujos operativos completos del RNDC

---

### 3. Manifiesto Electrónico de Carga

**Archivo:** [`guia-manifiesto-electronico-v3.md`](./guia-manifiesto-electronico-v3.md)

Guía operativa **V3** (12 de mayo de 2026) del Ministerio de Transporte. Describe paso a paso las actividades para expedir el Manifiesto Electrónico de Carga (MEC) a través del portal web y el web service del RNDC.

**Contenido clave:**
- Prerrequisitos para expedir el manifiesto
- Registro del viaje, conductor, vehículo y carga
- Expedición y anulación del manifiesto
- Cumplido del manifiesto y cierre del viaje

---

### 4. Registro de Remesa

**Archivo:** [`guia-registro-remesa-v4.md`](./guia-registro-remesa-v4.md)

Guía **V4** elaborada por el Grupo de Logística del Ministerio de Transporte (aprobada por Juan Felipe Sanabria Saetta y Alexandra Hernández). Explica el proceso de registro de remesas en el sistema RNDC, incluyendo la codificación de subpartida y código arancel.

**Contenido clave:**
- Proceso de registro de remesa vía portal web y XML/web service
- Codificación de mercancías con subpartida arancelaria
- Control de cambios desde 2024

---

### 5. Retención FOPAT

**Archivo:** [`guia-retencion-fopat-v2.md`](./guia-retencion-fopat-v2.md)

Guía **V2** (20 de abril de 2026) del Ministerio de Transporte. Describe las actividades para realizar el registro de la retención FOPAT en el Manifiesto Electrónico de Carga y en el Cumplido del Manifiesto.

**Contenido clave:**
- Concepto y base legal de la retención FOPAT
- Registro de retención al momento de expedir el manifiesto
- Ajuste de retención en el cumplido del manifiesto
- Casos especiales y manejo de errores

---

### 6. Monitoreo de Flota

**Archivo:** [`guia-monitoreo-flota-v8.md`](./guia-monitoreo-flota-v8.md)

Guía **V8** (24 de febrero de 2026) del Ministerio de Transporte. Explica cómo los sistemas de monitoreo de flota (EMF) reportan los tiempos logísticos al RNDC mediante el web service.

**Siglas clave:** EMF (Empresa de Monitoreo de Flota), ETC (Empresa de Transporte de Carga), GEC (Generador de Carga), RMM / RNMM (Registro Nacional de Medios de Monitoreo)

**Contenido clave:**
- Requisitos para empresas de monitoreo habilitadas
- Estructura de los mensajes de reporte (XML)
- Eventos a reportar: cargue, descargue, paradas, incidencias
- Validaciones y códigos de error del web service

---

### 7. Uso del Web Service RNDC

**Archivo:** [`guia-webservice-rndc-v4.md`](./guia-webservice-rndc-v4.md)

Guía **V4** (elaborada por Jairo Vesga, revisada por Edna Lorena Gutiérrez). Referencia técnica para la integración de sistemas externos con el RNDC mediante SOAP/XML.

**Contenido clave:**
- Endpoints y ambientes (pruebas y producción)
- Estructura de los mensajes SOAP
- Operaciones disponibles: registro de manifiesto, cumplido, consultas
- Autenticación y manejo de tokens
- Códigos de respuesta y errores

---

### 8. Consulta SICETAC — Portal y Web Service

**Archivos:**
- [`consulta-sicetac-portal-webservice.md`](./consulta-sicetac-portal-webservice.md)
- [`guia-sicetac-webservice.md`](./guia-sicetac-webservice.md)

Documentación (agosto 2021) sobre cómo consultar los **valores de referencia de costos eficientes de transporte** (SICETAC) desde el RNDC. El sistema alerta a empresas que registren valores por debajo del mínimo SICETAC.

**Contenido clave:**
- Conceptos generales del SICETAC
- Consulta desde el portal web interactivo
- Consulta desde el web service SOAP (ejemplos XML completos)
- Consultas filtradas por tipo de vehículo, ruta y carga
- Manejo de errores

---

### 9. Factura Electrónica de Transporte

**Archivo:** [`guia-factura-electronica-v11.md`](./guia-factura-electronica-v11.md)

Guía **V11** del Grupo de Logística del Ministerio de Transporte sobre la Factura Electrónica de Transporte. Cubre el proceso de emisión y los estándares XML requeridos para la integración con el RNDC.

**Contenido clave:**
- Estructura XML de la factura electrónica de transporte
- Campos obligatorios y opcionales
- Integración con el manifiesto electrónico de carga
- Validaciones y errores comunes

---

### 10. Codificación Sistema Armonizado

**Archivo:** [`codificacion-sistema-armonizado.md`](./codificacion-sistema-armonizado.md)

Documento de referencia (342 páginas, elaborado por Jairo Vesga) con la **Codificación del Sistema Armonizado de Designación y Codificación de Mercancías**. Indispensable para el registro correcto de mercancías en remesas y manifiestos.

**Contenido clave:** Tabla completa de secciones y capítulos del sistema armonizado — desde animales vivos hasta maquinaria e instrumentos de precisión — con los códigos de subpartida arancelaria aplicables al transporte de carga en Colombia.

---

## Contexto

El **RNDC** es el sistema del Ministerio de Transporte de Colombia que registra los despachos de carga por carretera. Es obligatorio para empresas de transporte de carga, generadores de carga y conductores. Permite el seguimiento de manifiestos electrónicos, remesas, retenciones FOPAT y la verificación de tarifas mínimas SICETAC.

- **Entidad responsable:** Ministerio de Transporte — República de Colombia
- **Acceso al sistema:** [rndc.gov.co](https://www.rndc.gov.co)
- **Documentos actualizados a:** Mayo de 2026

---

## Formato

Todos los archivos están en formato **Markdown** (`.md`), convertidos desde los PDF originales publicados por el Ministerio de Transporte y optimizados para uso con herramientas de búsqueda semántica y modelos de lenguaje (RAG/LLM).
