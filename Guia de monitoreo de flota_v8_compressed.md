---
title: "Guía de Monitoreo de Flota – Reporte de Tiempos Logísticos a través de Sistemas de Monitoreo de Flota al RNDC"
source: "Guia_de_monitoreo_de_flota_v8_compressed.pdf"
version: "08"
issuer: "Ministerio de Transporte – República de Colombia"
date_issued: "2026-02-24"
date_converted: "2026-05-24"
total_sections: 18
siglas_clave: ["EMF", "ETC", "GEC", "RMM", "RNMM", "RNDC"]
---

# Guía de Monitoreo de Flota

**Reporte de tiempos logísticos a través de sistemas de monitoreo de flota al RNDC**
Versión 08 — 24 de febrero de 2026
Ministerio de Transporte — República de Colombia

---

## Tabla de Contenidos

- [Control de Cambios](#control-de-cambios)
- [Antecedentes](#antecedentes)
- [1. Ámbito de Aplicación – Alcance](#1-ámbito-de-aplicación--alcance)
- [2. Definiciones](#2-definiciones)
- [3. Solicitud de Usuario de Empresa de Monitoreo de Flota en RNDC](#3-solicitud-de-usuario-de-empresa-de-monitoreo-de-flota-en-rndc)
- [4. Parametrización de Empresa de Monitoreo de Flota por parte de la Empresa de Transporte](#4-parametrización-de-empresa-de-monitoreo-de-flota-por-parte-de-la-empresa-de-transporte)
- [5. Parametrización de Geocercas](#5-parametrización-de-geocercas)
- [6. Sedes Módulo de Terceros – Coordenadas Georreferenciadas](#6-sedes-módulo-de-terceros--coordenadas-georreferenciadas)
- [7. Expedición de Remesa](#7-expedición-de-remesa)
  - [7.1 Remesa "Mercancía Consolidada"](#71-remesa-mercancía-consolidada)
  - [7.2 Modificaciones en la Remesa](#72-modificaciones-en-la-remesa)
- [8. Expedición de Manifiesto Electrónico de Carga](#8-expedición-de-manifiesto-electrónico-de-carga)
- [9. Consulta para Empresas de Monitoreo de Flota](#9-consulta-para-empresas-de-monitoreo-de-flota)
- [10. Registro Monitoreo de Manifiesto (RMM)](#10-registro-monitoreo-de-manifiesto-rmm)
  - [10.1 Ajuste Registro de Monitoreo de Manifiesto](#101-ajuste-registro-de-monitoreo-de-manifiesto)
- [11. Registro de Novedades Monitoreo de Manifiesto (RNMM)](#11-registro-de-novedades-monitoreo-de-manifiesto-rnmm)
- [12. Distribución de Tiempos Logísticos Reales en Remesas](#12-distribución-de-tiempos-logísticos-reales-en-remesas)
- [13. Cumplido Inicial de Remesa](#13-cumplido-inicial-de-remesa)
- [14. Cumplido de Remesa](#14-cumplido-de-remesa)
- [15. Diccionario de Errores](#15-diccionario-de-errores)
- [16. Plan de Contingencia RNDC](#16-plan-de-contingencia-rndc)
- [17. Estadísticas de Información de la Empresa de Monitoreo de Flota](#17-estadísticas-de-información-de-la-empresa-de-monitoreo-de-flota)
- [18. Consultas para la EMF](#18-consultas-para-la-emf)

---

## Control de Cambios

| Fecha | Modificación |
|---|---|
| 29/09/2025 | Estructuración de guía de tiempos logísticos a través de sistemas de Monitoreo de Flota. |
| 08/10/2025 | Se actualiza el ámbito de aplicación, actualización definiciones de Horas de espera para el cargue, Horas de cargue, Horas totales de cargue, Horas de espera para el descargue, Horas de descargue, Horas totales de descargue y Horas logísticas de acuerdo con Decreto 1017 de 2025. |
| 29/10/2025 | Se define de acuerdo al alcance que las remesas de tipo de operación mercancía consolidada, cambios en la cita pactada de cargue y descargue, y cambio de sede en descargue. Modificación de tiempos logísticos en el cumplido de la remesa. |
| 04/11/2025 | Se incluye IP a donde se comunican las empresas de monitoreo: `rndcws.mintransporte.gov.co:8080/ws`. |
| 12/11/2025 | Ajuste de tiempos logísticos a nivel de manifiesto en la opción de Monitoreo de manifiesto con acceso desde portal interactivo RNDC 2, numeral 10.1. Actualización de validaciones para cambios de fecha pactada en cargue y descargue y actualización de ejemplos XML para cada caso. Actualización de tiempo de envío de RMM por parte de la EMF. |
| 19/11/2025 | Complemento del RMM – numeral 10.1 ajuste a tiempos logísticos; se incluye paso a paso de portal interactivo y ejemplo XML. |
| 03/12/2025 | Actualización de etiquetas para el proceso de modificaciones de la remesa y ajuste de registro de monitoreo de manifiesto. Se crea una nueva consulta para EMF para consulta de manifiestos por número de radicado. |
| 24/02/2026 | Inclusión de IP para la consulta de manifiestos a monitorear. Nuevas consultas de manifiestos autorizados para EMF (`ULTIMAHORA`, `ID`). Generación de puntos de control en el ajuste de RMM por parte de la ETC. |

---

## Antecedentes

El Ministerio de Transporte ha reglamentado desde el año 2013 la operación del transporte de carga pública por carretera. A través del Registro Nacional de Despachos de Carga (en adelante "RNDC"), el sistema opera como plataforma de información, permitiendo a cada empresa de transporte habilitada la expedición de manifiestos de carga.

Como parte de los datos que cada empresa de transporte debe reportar y enviar al Ministerio de Transporte, se encuentran los **tiempos logísticos del viaje**, los cuales hacen parte del Cumplido de la Remesa y del Cumplido del Manifiesto:

- **Cumplido de la Remesa**: constancia de entrega de la mercancía al destino final.
- **Cumplido del Manifiesto**: certificación o liquidación final de todos los gastos involucrados en el viaje.

En este sentido, conforme con lo dispuesto en el artículo 1 de la Resolución 377 de 2013 y la Resolución 20223040045515 de 2022 ("Por la cual se actualiza el sistema del Registro Nacional de Despachos de Carga -RNDC y se dictan otras disposiciones..."), específicamente en el Manual de Descripción e Instrucciones para la Operación General del RNDC, numeral 5.3.3 — Registro cumplido de manifiesto electrónico de carga —, se establece que: "La empresa de transporte habilitada, persona natural o jurídica, deberá diligenciar de forma obligatoria en el sistema del Registro Nacional de Despachos de Carga -RNDC-, todos los datos requeridos en el registro Cumplido de Manifiesto Electrónico de Carga, a más tardar dentro de los 5 días hábiles contados a partir de la fecha de entrega de la mercancía registrada en el Cumplido de Remesa Terrestre de Carga (...)."

La Resolución 20243040058015 de noviembre de 2024 establece que las empresas de servicio público de transporte de carga deberán realizar de manera obligatoria el reporte en el RNDC de los datos relacionados con los **tiempos reales (fecha y hora) ejecutados de cargue y descargue** de la mercancía mediante el uso de sistemas de monitoreo de flota, a partir del 30 de noviembre de 2025, de acuerdo con las condiciones, criterios técnicos y metodología que para tal efecto expida el ministro de transporte.

La empresa de transporte deberá autorizar ante el RNDC a la empresa que preste el servicio de monitoreo de flota para que, a su nombre, sea quien reporte al sistema RNDC los datos relacionados (llegada lugar del cargue, salida lugar del cargue, llegada lugar del descargue y salida lugar del descargue).

Los datos de **fecha y hora de entrada al lugar de cargue y entrada al lugar de descargue** podrán ser reportados por la empresa de transporte al RNDC a través del portal interactivo y/o WebService y/o aplicación "RNDC Transportador".

---

## 1. Ámbito de Aplicación – Alcance

El reporte de tiempos logísticos a través de Sistemas de monitoreo de Flota aplica de manera inicial para las siguientes operaciones:

**Tipos de manifiesto que aplican:**
- Carga general
- Multiparada
- Ida y regreso

**Tipos de remesa terrestre de carga que aplican** (siempre y cuando NO realicen operaciones de recolección y/o distribución):
- General
- Contenedor cargado
- Contenedor vacío
- Mercancía consolidada

**No aplica para:**
- Manifiestos de Varios viajes en el día
- Viaje Vacío
- Registros de viaje Municipal

---

## 2. Definiciones

**Punto de Control:** espacio definido mediante coordenadas georreferenciadas en el cual se efectúan los procesos de cargue y/o descargue de mercancía y puntos intermedios en el tránsito. La empresa de monitoreo deberá capturar y reportar los tiempos logísticos reales en cada punto de control.

Cada punto de control para cargue y descargue deberá tener una cita previa para que el conductor llegue puntual y la empresa de monitoreo tenga una fecha y hora de referencia. Los puntos de control intermedio los define el Ministerio de Transporte y no tendrán fecha y hora de cita. Cada punto de control debe tener bien definidas sus coordenadas georreferenciadas.

**Evento de monitoreo:** novedades que pueden presentar las empresas de monitoreo de flota antes y durante la operación y el reporte de los tiempos logísticos reales de los manifiestos autorizados por la empresa de transporte.

**Registro Monitoreo de Manifiesto (RMM):** reporte de los datos relacionados con la fecha y hora realmente ejecutadas para cada uno de los siguientes eventos: llegada al lugar del cargue, salida del lugar del cargue, llegada al lugar del descargue y salida del lugar del descargue.

El reporte de la información será por medio de interoperabilidad en el sistema de información vía WebService. El registro de monitoreo de manifiesto **se deberá enviar al RNDC después de que el vehículo salga del punto de control.**

**Registro de Novedades Monitoreo de Manifiesto (RNMM):** registro con la relación de la novedad de monitoreo por la cual no se puede realizar el registro de tiempos logísticos reales de los puntos de control de los manifiestos autorizados.

**Geocerca:** delimitación virtual o perímetro aplicado a una zona o espacio geográfico para separarlo de su entorno. Las geocercas pueden tener forma geométrica definida (circular, rectangular, etc.) o patrones irregulares de acuerdo con la necesidad, aumentando la precisión. Esta delimitación se realiza conjuntamente entre el generador de carga, la empresa de transporte y la empresa de monitoreo de flota.

**Horas de espera para el cargue:** tiempo transcurrido desde el momento en que el vehículo se encuentra disponible en el lugar señalado por la Empresa de Transporte para realizar la actividad de cargue, hasta el momento de inicio del cargue. En caso de que el vehículo llegue antes de la hora programada, el tiempo de espera se contará a partir de la hora de la cita programada.

**Horas de cargue:** tiempo transcurrido desde el momento que inicia la actividad de cargue de la mercancía al vehículo hasta que este sale cargado del lugar.

**Horas totales de cargue:** sumatoria de las horas de espera para el cargue y las horas de cargue.

**Horas de espera para el descargue:** tiempo transcurrido desde el momento en que el vehículo se encuentra disponible en el lugar señalado por la Empresa de Transporte para la actividad de descargue, hasta que inicia el descargue. En caso de que el vehículo llegue antes de la hora programada, el tiempo de espera se contará a partir de la hora de la cita programada.

**Horas de descargue:** tiempo transcurrido desde el momento que inicia la actividad de descargue de la mercancía del vehículo hasta que sale descargado del lugar.

**Horas totales de descargue:** sumatoria de las horas de espera para el descargue y las horas de descargue.

**Horas logísticas:** sumatoria de las horas totales del cargue y las horas totales del descargue.

### Siglas

| Sigla | Significado |
|---|---|
| EMF | Empresa de Monitoreo de Flota |
| ETC | Empresa de Transporte de Carga |
| GEC | Generador de Carga |
| RMM | Registro Monitoreo de Manifiesto |
| RNMM | Registro de Novedades de Monitoreo de Manifiesto |

---

## 3. Solicitud de Usuario de Empresa de Monitoreo de Flota en RNDC

*Proceso que realiza la Empresa de Monitoreo de Flota.*

Cada Empresa Monitoreo de Flota (EMF) que desee enviar la información de tiempos logísticos al RNDC debe solicitar usuario mediante el portal interactivo RNDC2, diligenciando cada uno de los campos y anexando el certificado de existencia y representación de Cámara de Comercio. Este certificado **no puede tener una vigencia mayor a treinta (30) días calendario** de su expedición.

Portal: [Portal Logístico de Colombia](https://rndc2.mintransporte.gov.co/) — opción **Solicitar Usuario**.

<!-- Imagen: Pantalla del portal RNDC con menú desplegable mostrando opciones: Iniciar Sesión, Solicitar Usuario, Restaurar Contraseña, Actualizar eMail y Otros Datos. -->

<!-- Imagen: Formulario de solicitud de usuario con campos: Tipo de empresa, Número de Identificación, Nombre o Razón Social, Dirección, País (COLOMBIA), Municipio, email de verificación judicial, Nombres y apellidos del Representante Legal, Nombre del Contacto en la empresa, Certificado de existencia y Representación Legal, archivos adjuntos. -->

Si toda la información adjuntada en la solicitud del usuario es correcta, mediante correo electrónico se asigna un usuario y contraseña inicial, la cual puede cambiar en cualquier momento.

Una vez asignado el usuario en RNDC, la EMF debe administrar usuarios creando un **usuario tipo 2 (usuario de monitoreo)**, el cual tendrá todos los permisos para consulta y envío de información. Esto se realiza en el módulo **Herramientas >> Administración de usuarios**, opción de creación de usuario dependiente tipo 2.

Cuando el monitoreo lo realiza la propia empresa de transporte, también aplica la creación de usuario tipo 2 (usuario de monitoreo) para el reporte de tiempos logísticos reales.

> **Recomendación:** La información del usuario dependiente tipo 2 debe ser información institucional de la empresa (correo corporativo), de modo que ante cambios de personal se pueda restablecer el usuario.

**Regla importante:** Cada empresa de monitoreo de flota debe tener su usuario principal y usuarios dependientes de monitoreo. **No debe usar usuarios de las Empresas de Transporte** a las cuales va a realizar el monitoreo de manifiestos.

<!-- Imagen: Portal RNDC2 con menú Herramientas desplegado, mostrando opciones: Administrar Usuarios, InformacionEmpresa. Panel lateral con Mesa de Ayuda: Tel. 3240800, Lunes a Viernes 8 AM – 5PM, servicioalciudadano@mintransporte.gov.co, Ministerio de Transporte – Grupo de Logística, Calle 24 # 60-50 Piso 9, C.C. Gran Estación II, Bogotá, Colombia. -->

### Endpoints de conexión para empresas de monitoreo

**Consulta de manifiestos a monitorear (Unidad 9):**
```
http://plc.mintransporte.gov.co:8080/
```
Habilitada para consulta de manifiestos a monitorear. Parámetros: `<tipo>9</tipo>` `<procesoid>4</procesoid>`

**Envío de WebService (RMM y RNMM):**
```
rndcws.mintransporte.gov.co:8080/ws
```
Permite extraer el archivo WSDL donde se encuentra la URL correcta para el envío del WebService y los dos parámetros requeridos para la tecnología SOAP. Desde esta IP se pueden realizar: RMM (procesoid 60–68) y RNMM (procesoid 46).

---

## 4. Parametrización de Empresa de Monitoreo de Flota por parte de la Empresa de Transporte

*Proceso que realiza la Empresa de Transporte.*

En el módulo **Herramientas >> Información Empresa Transportadora** del portal RNDC2, la empresa de transporte (ETC) puede parametrizar una EMF como característica predeterminada de la empresa, definiendo un NIT estándar de EMF para el registro de tiempos logísticos reales.

La actualización solo puede realizarse a través del portal interactivo RNDC2. El usuario autorizado para realizar cambios en este módulo es el **usuario maestro (Tipo 6)**, asignado a la empresa de transporte.

<!-- Imagen: Formulario de "Empresa de Transporte" en RNDC con campos: Usuario, Tipo Usuario (1), Código Disp., Identificación, Nombre Empresa (MINISTERIO DE TRANSPORTE), Tipo Identificación (N), Estado Empresa (ACTIVA), Territorial (AMAZONAS), Dirección Empresa (MINTRANSPORTE), Municipio (BOGOTA BOGOTA D.C. – 11001000), Correo Alertas, Nombre Representante Legal (MINISTRO), Nombre Contacto (JAIRO VESGA M.), Observaciones Contacto (EMPRESA DE PRUEBAS), campo "Empresa Monitoreo Flota" resaltado en rojo, Afiliado al Gremio, Aceptación Electrónica e/m Titular del Manifiesto. -->

Al parametrizar la EMF como predeterminada, la ETC **no necesita enviar el NIT de la EMF en cada manifiesto de carga**. En caso de no incluirla como predeterminada, la ETC deberá digitar el NIT de la EMF cada vez que expida un manifiesto.

Si en una operación puntual se utilizará una EMF diferente a la predeterminada, la ETC debe registrar el NIT de esa EMF específica en la expedición del manifiesto.

### Empresa de Transporte con Sistemas de Monitoreo Propios

El NIT de la EMF y el NIT de la ETC **podrá ser el mismo**, siempre y cuando se diligencie el certificado establecido por el Ministerio de Transporte en el que la ETC certifica las condiciones técnicas de la herramienta tecnológica propia utilizada para el monitoreo de flota y la calidad de la información de datos que serán registrados en el RNDC como tiempos logísticos reales. Este formato debe estar firmado por el representante legal de la empresa de transporte.

Una vez aprobada la solicitud por parte del RNDC, la empresa de transporte debe parametrizar el NIT estándar en el módulo de información empresa transportadora para posteriormente crear usuarios de tipo monitoreo **(USUARIO TIPO 2)**.

> **Restricción:** Empresas de transporte con certificado de cumplimiento de condiciones técnicas **NO pueden** hacer monitoreo de flota a otra empresa de transporte.

El Ministerio de Transporte realiza seguimiento y análisis de la información suministrada. En caso de identificar mala calidad de los datos, realizará reporte a la **Superintendencia de Transporte** para que ejerza sus competencias de vigilancia, inspección y control.

---

## 5. Parametrización de Geocercas

Para la identificación, definición y realización de geocercas para cada punto de control, se entenderá que es un **trabajo conjunto** entre la empresa de transporte (ETC), los generadores de carga (GEC) y la empresa de monitoreo de flota (EMF).

La exactitud en la creación de geocercas permitirá aumentar la precisión para la identificación de los tiempos logísticos reales, delimitando puntos cercanos que puedan afectar la calidad de los datos en los momentos de entrada y salida de la geocerca.

Con el avance del reporte de tiempos logísticos a través de herramientas de monitoreo de flota, el RNDC recopilará información de las geocercas definidas en los puntos de control. Se definirá un proceso técnico para la entrega de esta información por parte de las EMF y las ETC, con trabajo articulado con generadores de carga.

A partir de esta información el RNDC construirá un **maestro de geocercas de puntos de control**. En una segunda fase del proyecto, este maestro será entregado a las EMF por cada punto de control, mejorando el proceso de registro de tiempos logísticos y la eficiencia en operaciones de transporte.

---

## 6. Sedes Módulo de Terceros – Coordenadas Georreferenciadas

Las coordenadas georreferenciadas (latitud y longitud) de los puntos de cargue y descargue son vitales para el éxito del registro por parte de las empresas de monitoreo. Las herramientas disponibles en internet pueden proveer coordenadas a partir de la dirección y municipio, siempre y cuando la dirección se encuentre normalizada.

El RNDC define puntos centrales de cada municipio, identificando geocercas y validando las coordenadas de cada sede de cargue y/o descargue. Las coordenadas se registran en el módulo **"Registrar terceros y conductores"**.

Los datos de latitud y longitud son validados contra la geocerca definida para cada municipio. En caso de no tener una geocerca definida, se tomará un **rango estándar de 10 km**. Cada municipio de Colombia tiene asociada una coordenada georreferenciada de un punto central al casco urbano, consultable por maestros: **DIVIPOLA**.

> **Nota:** Si la distancia entre la ubicación del tercero y el punto central del municipio es mayor a la geocerca, es porque el municipio del tercero corresponde a una vereda y no a la cabecera municipal. En ese caso, se debe averiguar el código de la vereda y digitarlo en lugar de la cabecera.

Para las ETC que usan WebServices, los nombres de los campos son `LATITUD` y `LONGITUD` para la ubicación de la sede de cargue y/o descargue.

### Ejemplo XML: Creación de Tercero con coordenadas

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuario1</username>
    <password>password1</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>11</procesoid>
  </solicitud>
  <variables>
    <numnitempresatransporte>1111</numnitempresatransporte>
    <codtipoidtercero>n</codtipoidtercero>
    <numidtercero>1111</numidtercero>
    <nomidtercero>xxxx</nomidtercero>
    <codmunicipiorndc>11001000</codmunicipiorndc>
    <codsedetercero>001</codsedetercero>
    <nomsedetercero>SEDE1</nomsedetercero>
    <latitud>4.645811</latitud>
    <longitud>-74.102716</longitud>
  </variables>
</root>
```

En sedes que implementan **zonas de enturnamiento** en una posición geográfica diferente a donde se realizan las operaciones de cargue o descargue, se deben incluir las coordenadas georreferenciadas de la zona de enturnamiento mediante las etiquetas:

```xml
<direccionenturnamiento>...</direccionenturnamiento>
<latitudenturnamiento>...</latitudenturnamiento>
<longitudenturnamiento>...</longitudenturnamiento>
```

### Ejemplo XML: Creación de Tercero con zona de enturnamiento

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuario1</username>
    <password>password1</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>11</procesoid>
  </solicitud>
  <variables>
    <numnitempresatransporte>1111</numnitempresatransporte>
    <codtipoidtercero>n</codtipoidtercero>
    <numidtercero>1111</numidtercero>
    <nomidtercero>xxxx</nomidtercero>
    <codmunicipiorndc>11001000</codmunicipiorndc>
    <codsedetercero>001</codsedetercero>
    <nomsedetercero>sede1</nomsedetercero>
    <latitud>4.645811</latitud>
    <longitud>-74.102716</longitud>
    <direccionenturnamiento>111</direccionenturnamiento>
    <latitudenturnamiento>1111</latitudenturnamiento>
    <longitudenturnamiento>1111</longitudenturnamiento>
  </variables>
</root>
```

> **Nota:** Los terminales portuarios son los más comunes en el uso de zonas de enturnamiento, generalmente para operaciones con carga de granel líquido y sólido, en lugar de asignación de citas individuales a cada vehículo.

### Cómo identificar coordenadas georreferenciadas para una sede

Una forma de obtener las coordenadas es usando Google Maps (https://www.google.com/maps):

1. Escribir la dirección en el campo de búsqueda, incluyendo municipio y departamento. Ejemplo: `calle 24 60-50 Bogotá`.
2. Hacer clic en la lupa; el software muestra la ubicación con un marcador rojo.
3. Con el mouse sobre el marcador rojo, hacer **clic derecho** y seleccionar **"¿Qué hay aquí?"**.
4. En la parte inferior aparece un cuadro con las coordenadas georreferenciadas.

Ejemplo de resultado: `4.645811, -74.102716` — el primer dato es la **latitud** y el segundo la **longitud**. Para Colombia, la longitud **siempre debe ser un dato negativo**.

Después de grabar las coordenadas al Tercero, la sede queda habilitada como posible punto de cargue o descargue de una remesa. El RNDC enviará automáticamente esas coordenadas a la empresa de monitoreo de flota.

---

## 7. Expedición de Remesa

*Proceso que realiza la Empresa de Transporte.*

> *La presente Guía de tiempos logísticos aplica para los manifiestos de carga que contengan remesas terrestres de carga: general, Contenedor cargado, contenedor vacío y mercancía consolidada, siempre y cuando no realicen operaciones de recolección y/o distribución.*

En la expedición de la remesa se digita el código de la sede del punto de control y el sistema RNDC consulta los siguientes datos:

1. Nombre
2. Dirección
3. Municipio
4. Coordenadas Georreferenciadas
5. Dirección zona de enturnamiento *(opcional)*
6. Coordenadas Georreferenciadas zona de enturnamiento *(opcional)*

Así mismo se debe identificar para cada punto de control su respectiva **fecha y hora de cita** con su tiempo pactado de espera:

1. **Fecha y hora cita** (hora militar con horas y minutos).

**La fecha y hora de la cita es un dato clave** y de relevancia en la implementación de esta metodología. Debe ser de estricto cumplimiento por cada uno de los actores, mejorando las prácticas en las operaciones de transporte e impactando de manera positiva la eficiencia y los costos logísticos. Son el parámetro de referencia para el cálculo de los tiempos logísticos reales.

> **⚠️ IMPORTANTE:** La diferencia entre la cita programada para el cargue y la cita programada para el descargue deberá ser acorde a la distancia y tiempo de tránsito entre el punto de cargue y descargue. La empresa de transporte y el titular del manifiesto de carga deberán acordar el reconocimiento económico de tiempos adicionales a través del contrato de vinculación, y reflejarse al momento de expedir y cumplir el manifiesto de carga.

2. **Tiempo pactado** (horas y minutos). Aplica para las operaciones de cargue y descargue.

### Ejemplo XML: Expedición de Remesa

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuario1</username>
    <password>password1</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>3</procesoid>
  </solicitud>
  <variables>
    <numnitempresatransporte>1111</numnitempresatransporte>
    <consecutivoremesa>1111</consecutivoremesa>
    <codsederemitente>001</codsederemitente>
    <codsededestinatario>002</codsededestinatario>
    <horaspactocarga>2</horaspactocarga>
    <minutospactocarga>25</minutospactocarga>
    <horaspactodescargue>1</horaspactodescargue>
    <minutospactodescargue>53</minutospactodescargue>
    <fechacitapactadacargue>2025/07/11</fechacitapactadacargue>
    <horacitapactadacargue>08:15</horacitapactadacargue>
    <fechacitapactadadescargue>2025/07/12</fechacitapactadadescargue>
    <horacitapactadadescargueremesa>07:35</horacitapactadadescargueremesa>
  </variables>
</root>
```

### Código de error relacionado

| Código | Observación |
|---|---|
| REM502 | Falta una de las coordenadas georreferenciadas para los puntos de cargue o descargue; la empresa de monitoreo de flota las necesita para realizar el seguimiento satelital. |

---

### 7.1 Remesa "Mercancía Consolidada"

De acuerdo con el ámbito de aplicación de la presente metodología, en esta primera fase las remesas de tipo de operación **"Mercancía Consolidada"** que realicen operaciones de recolección y/o distribución en dos o más puntos o sedes **no aplican** el reporte de tiempos logísticos a través de sistemas de monitoreo de flota.

En caso de expedir una remesa de tipo "Mercancía Consolidada" con **un único punto de cargue y/o un único punto de descargue**, sí deben realizar el reporte de tiempos logísticos a través de sistemas de monitoreo de flota.

Para las remesas con tipo de operación "Mercancía Consolidada" se implementa el campo **"Tipo de consolidación"**, con las siguientes opciones:

**R — Recolección en varios puntos (dos o más puntos)**
- Tiempos logísticos a través de sistemas de monitoreo de flota para el punto de Descargue.
- Para la operación de cargue, la ETC debe registrar el tiempo logístico en el cumplido de la remesa y debe ser un valor mayor a cero (0). El sistema mostrará como tiempo: 1 hora.

**D — Distribución en varios puntos (dos o más puntos)**
- Tiempos logísticos a través de sistemas de monitoreo de flota para el punto de Cargue.
- Para la operación de descargue, la ETC debe registrar el tiempo logístico en el cumplido de la remesa y debe ser un valor mayor a cero (0). El sistema mostrará como tiempo: 1 hora.

**A — Ambas: recolección y distribución (dos o más puntos)**
- No aplica los tiempos a través de sistemas de monitoreo de flota.
- Para la operación mixta, la ETC debe registrar el tiempo logístico de cargue y descargue en el cumplido de la remesa y debe ser un valor mayor a cero (0). El sistema mostrará como tiempo: 1 hora.

**N — Normal: un punto de cargue y un punto de descargue**
- Tiempos logísticos a través de sistemas de monitoreo de flota para el punto de Cargue y para el punto de Descargue.

### Ejemplo XML: Remesa Consolidada

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuario1</username>
    <password>password1</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>3</procesoid>
  </solicitud>
  <variables>
    <numnitempresatransporte>1111</numnitempresatransporte>
    <consecutivoremesa>111</consecutivoremesa>
    <codoperaciontransporte>P</codoperaciontransporte>
    <tipoconsolidada>A</tipoconsolidada>
    <horaspactocarga>2</horaspactocarga>
    <minutospactocarga>30</minutospactocarga>
    <horaspactodescargue>2</horaspactodescargue>
    <minutospactodescargue>45</minutospactodescargue>
    <fechacitapactadacargue>2025/07/11</fechacitapactadacargue>
    <horacitapactadacargue>08:15</horacitapactadacargue>
  </variables>
</root>
```

---

### 7.2 Modificaciones en la Remesa

Se contemplan las modificaciones que afectan el monitoreo y reporte de tiempos logísticos reales al RNDC. Para el detalle completo de procesos y validaciones, consultar la **Guía de Modificaciones de Remesa**.

**Cambios que afectan las operaciones de cargue y/o descargue:**

| Código | Tipo de cambio |
|---|---|
| 1 | Cambio Cita de Cargue |
| 2 | Cambio Cita de Descargue |
| 3 | Cambio Sede de Descargue |
| 4 | Cambio de Generador de Carga |

Una vez realizados los cambios, el RNDC informa los cambios a la empresa de monitoreo y al titular del manifiesto:
- **Titular de Manifiesto:** mediante correo electrónico registrado en la app RNDC Transportador. Si el titular no tiene usuario en RNDC, el correo se envía a la información registrada en el módulo de terceros.
- **EMF:** mediante la etiqueta especial `<ajuste>`, enviada en la próxima consulta de manifiestos a monitorear.

#### Cita de Cargue

El RNDC permite cambiar la fecha y hora de la cita de cargue bajo las siguientes condiciones:

1. La remesa debe pertenecer a un manifiesto de carga.
2. La remesa **NO** puede tener cumplido inicial de remesa para el punto de control.
3. La nueva fecha y hora debe ser futura y con más de 1 hora de diferencia con respecto a la fecha y hora del sistema.
4. El aviso al titular de manifiesto debe ser mínimo con **1 hora de anticipación** respecto a la cita pactada.
5. El sistema permite el cambio aun con un RNMM existente. Solo notifica a la EMF en caso de ser novedad tipo (1).

Para operaciones con nodo portuario y citas en línea por módulo INSIDE, el RNDC hace el cambio automáticamente. Se implementa la **"Consulta de manifiestos con cargue en puerto sin cita"** para auditoría por la ETC.

**Cálculo de tiempos logísticos y valores SICE-TAC — puntos de control múltiples:**
- **Primer punto de control:** los tiempos logísticos se consideran a partir de la nueva fecha y hora de la cita, sin importar si es anterior o posterior a la cita inicial.
- **A partir del segundo punto de control:** el RNDC tiene en cuenta la primera fecha y hora pactada. La nueva cita debe ser posterior al primer punto de control.

Se debe relacionar el **motivo del cambio de cita**:

| Etiqueta WebService | Motivo | Efecto en reconocimiento económico |
|---|---|---|
| `<motivocambio>1</motivocambio>` | Incumplimiento por parte del generador de carga | Desde la fecha y hora de la cita pactada o programada |
| `<motivocambio>2</motivocambio>` | Incumplimiento por parte del titular de manifiesto | Desde la NUEVA fecha y hora de la cita |

El RNDC permite más de un cambio para la cita de cargue siempre que se cumplan las condiciones.

#### Ejemplo XML: Cambio de Cita de Cargue

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuario1</username>
    <password>password1</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>38</procesoid>
  </solicitud>
  <variables>
    <numnitempresatransporte>1111</numnitempresatransporte>
    <consecutivoremesa>11</consecutivoremesa>
    <codigocambio>1</codigocambio>
    <motivocambio>1</motivocambio>
    <fechacitapactadacargue>01/01/2025</fechacitapactadacargue>
    <horacitapactadacargue>10:00</horacitapactadacargue>
  </variables>
</root>
```

#### Lugar de Cargue

> **Restricción:** No se puede cambiar la sede de cargue. Si se requiere cambio, se debe **anular la remesa**.

#### Fecha Cita de Descargue

El RNDC permite cambiar la fecha y hora de la cita de descargue bajo las siguientes condiciones:

1. La remesa debe pertenecer a un manifiesto de carga.
2. La remesa **NO** puede tener cumplido inicial de remesa para el punto de control de descargue.
3. La remesa **SÍ** puede tener Cumplido inicial de remesa para el punto de cargue.
4. La nueva fecha y hora debe ser futura y con más de 1 hora de diferencia con respecto a la fecha y hora del sistema.
5. La nueva fecha y hora debe ser futura y con **máximo 24 horas de diferencia** con respecto a la fecha y hora del sistema.
6. El sistema permite el cambio aun con un RNMM existente. Solo notifica a la EMF en caso de ser novedad tipo (1).

Para operaciones con nodo portuario y citas en línea por módulo INSIDE, el RNDC hace el cambio automáticamente. Se implementa la **"Consulta de manifiestos con descargue en puerto sin cita"** para auditoría.

Se debe relacionar el mismo esquema de motivos de cambio que para la cita de cargue (`<motivocambio>1</motivocambio>` o `<motivocambio>2</motivocambio>`).

#### Ejemplo XML: Cambio de Cita de Descargue

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuario1</username>
    <password>password1</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>38</procesoid>
  </solicitud>
  <variables>
    <numnitempresatransporte>1111</numnitempresatransporte>
    <consecutivoremesa>11</consecutivoremesa>
    <codigocambio>2</codigocambio>
    <motivocambio>2</motivocambio>
    <fechacitapactadadescargue>01/01/2025</fechacitapactadadescargue>
    <horacitapactadadescargue>10:00</horacitapactadadescargue>
  </variables>
</root>
```

#### Lugar de Descargue

El lugar de descargue **se puede modificar solo si el código de municipio NO cambia**. Si cambia el municipio, se debe anular la remesa.

#### Ejemplo XML: Cambio de Sede de Descargue

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuario1</username>
    <password>password1</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>38</procesoid>
  </solicitud>
  <variables>
    <numnitempresatransporte>1111</numnitempresatransporte>
    <consecutivoremesa>11</consecutivoremesa>
    <codigocambio>3</codigocambio>
    <codtipoiddestinatario>1</codtipoiddestinatario>
    <numiddestinatario>2</numiddestinatario>
    <codsededestinatario>1</codsededestinatario>
  </variables>
</root>
```

#### Ejemplo XML: Cambio de Generador de Carga

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuario1</username>
    <password>password1</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>38</procesoid>
  </solicitud>
  <variables>
    <numnitempresatransporte>1111</numnitempresatransporte>
    <consecutivoremesa>11</consecutivoremesa>
    <codigocambio>5</codigocambio>
    <codsedepropietario>1</codsedepropietario>
    <numidpropietario>1235</numidpropietario>
    <tipoidpropietario>N</tipoidpropietario>
  </variables>
</root>
```

#### Anulación de Remesa

Si la remesa ya tiene reporte de tiempos logísticos reales, **NO podrá ser anulada**. Previamente se deben anular los registros de tiempos logísticos reales. Esta anulación no se le informa a la EMF.

---

## 8. Expedición de Manifiesto Electrónico de Carga

*Proceso que realiza la Empresa de Transporte.*

> *El reporte de tiempos logísticos a través de Sistemas de monitoreo de Flota aplica de manera inicial para aquellas operaciones de transporte amparadas bajo el tipo de manifiesto de carga general, Multiparada, ida y regreso.*

En la expedición del manifiesto electrónico de carga se debe digitar el **NIT de la EMF**, siempre y cuando no tenga definido un NIT estándar en la funcionalidad "Información empresa transportadora".

Para las ETC que usan WebService, el nombre del campo es: `<nitmonitoreoflota>`

### Ejemplo XML: Expedición de Manifiesto de Carga

*(Solo se relacionan las etiquetas relevantes para la aplicación de la presente guía.)*

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuario1</username>
    <password>password1</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>4</procesoid>
  </solicitud>
  <variables>
    <numnitempresatransporte>1111</numnitempresatransporte>
    <nummanifiestocarga>1111</nummanifiestocarga>
    <fechaexpedicionmanifiesto>01/01/2025</fechaexpedicionmanifiesto>
    <numplaca>abc111</numplaca>
    <numplacaremolque>s1213</numplacaremolque>
    <numidconductor>111</numidconductor>
    <numidconductor2>1111</numidconductor2>
    <nitmonitoreoflota>1111</nitmonitoreoflota>
    <remesasman procesoid="43">
      <remesa>
        <consecutivoremesa>1</consecutivoremesa>
      </remesa>
      <remesa>
        <consecutivoremesa>2</consecutivoremesa>
      </remesa>
      <remesa>
        <consecutivoremesa>3</consecutivoremesa>
      </remesa>
    </remesasman>
  </variables>
</root>
```

### Códigos de error en expedición de manifiesto

| Código | Descripción |
|---|---|
| MAN007 | La empresa de transporte no registra NIT de la empresa de monitoreo para el reporte de tiempos logísticos. |
| MAN065 | La empresa de transporte no ha cargado en el RNDC el certificado de cumplimiento de condiciones técnicas. |
| MAN066 | La empresa de monitoreo de flota no existe en el RNDC. |

> **Nota:** MAN065 aplica cuando la empresa de transporte relaciona su mismo NIT para el envío de tiempos logísticos reales a través de Sistemas de Monitoreo de Flota (Módulo de Información Empresa).

### Anulación del Manifiesto Electrónico de Carga

Una vez expedido el manifiesto, se aplican las siguientes condiciones para permitir la anulación:

1. Si el manifiesto ya tiene RMM, el sistema **anula automáticamente los RMM** con causal "Anulación de Manifiesto".
2. Si el manifiesto tiene RNMM, el sistema **anula automáticamente los RNMM** con causal "Anulación de Manifiesto".
3. Si el manifiesto no tiene RMM pero la EMF ya está informada, el RNDC enviará en la próxima solicitud de información una marca para notificar la anulación.
   - Si el RNDC recibe un RMM de un manifiesto anulado y la EMF **NO** está informada: el sistema no entrega radicado y devuelve error `"MANIFIESTO ANULADO"`.
   - Si el RNDC recibe un RMM de un manifiesto anulado y la EMF **SÍ** está informada: el sistema no entrega radicado y devuelve error `"EN CONSULTA PREVIA SE NOTIFICO ANULACION DEL MANIFIESTO"`.

### Transbordos No Planeados

Se consideran transbordos no planeados los eventos en que, por condiciones que afectan directamente al vehículo, no se culmina la operación de transporte del manifiesto original y se debe generar un nuevo manifiesto de carga para el vehículo que terminará la operación.

El manifiesto inicial solo reportará los puntos de control que se hayan cumplido antes de la novedad que origina el transbordo. Una vez expedido el segundo manifiesto, el RNDC informará la novedad a la EMF en la próxima consulta, con el propósito de suspender el monitoreo al vehículo inicial. El segundo manifiesto reportará los puntos de control pactados con fecha y hora posteriores al evento que produce el transbordo.

---

## 9. Consulta para Empresas de Monitoreo de Flota

*Proceso que realiza la Empresa de Monitoreo de Flota.*

La EMF debe solicitar al RNDC la lista de manifiestos en los que ha sido autorizada por las ETC para hacer la labor de monitoreo. Esta consulta se realiza **únicamente por medio del WebService**.

> **Restricción de frecuencia:** El ciclo de repetición entre solicitud y solicitud **no podrá ser inferior a 5 minutos**, con el fin de evitar sobrecargas innecesarias en el RNDC.

La EMF puede realizar cinco tipos de consultas:

### Tipo 1 — Nuevos manifiestos desde la última consulta

Solicita los manifiestos autorizados desde la última vez que consultó la EMF, que no sean mayores a 24 horas de expedidos.

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuariogps</username>
    <password>passwordgps</password>
  </acceso>
  <solicitud>
    <tipo>9</tipo>
    <procesoid>4</procesoid>
  </solicitud>
  <documento>
    <numidgps>9999999999</numidgps>
    <manifiestos>NUEVOS</manifiestos>
  </documento>
</root>
```

### Tipo 2 — Todos los manifiestos autorizados en las últimas 24 horas

Útil cuando la empresa de monitoreo tiene dudas en la transmisión de datos. **Solo se puede hacer una vez cada 24 horas.**

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuariogps</username>
    <password>passwordgps</password>
  </acceso>
  <solicitud>
    <tipo>9</tipo>
    <procesoid>4</procesoid>
  </solicitud>
  <documento>
    <numidgps>9999999999</numidgps>
    <manifiestos>TODOS</manifiestos>
  </documento>
</root>
```

### Tipo 3 — Manifiestos consultados previamente en la última hora

Útil cuando hay dudas en la transmisión de datos reciente.

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuariogps</username>
    <password>passwordgps</password>
  </acceso>
  <solicitud>
    <tipo>9</tipo>
    <procesoid>4</procesoid>
  </solicitud>
  <documento>
    <numidgps>9999999999</numidgps>
    <manifiestos>ULTIMAHORA</manifiestos>
  </documento>
</root>
```

### Tipo 4 — Números de radicado de manifiestos autorizados en las últimas 24 horas

Devuelve únicamente los números de radicado, útil para verificar autorizaciones.

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuariogps</username>
    <password>passwordgps</password>
  </acceso>
  <solicitud>
    <tipo>9</tipo>
    <procesoid>4</procesoid>
  </solicitud>
  <documento>
    <numidgps>9999999999</numidgps>
    <manifiestos>ID</manifiestos>
  </documento>
</root>
```

### Tipo 5 — Consulta por número de radicado de manifiesto específico

Obtiene información de los puntos de control de un único manifiesto usando el número de radicado como llave única.

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuariogps</username>
    <password>passwordgps</password>
  </acceso>
  <solicitud>
    <tipo>9</tipo>
    <procesoid>4</procesoid>
  </solicitud>
  <documento>
    <numidgps>9999999999</numidgps>
    <ingresoidmanifiesto>123456789</ingresoidmanifiesto>
  </documento>
</root>
```

### Información que envía el RNDC a la EMF

Por cada manifiesto autorizado, el RNDC devuelve:

1. Número Radicado de Manifiesto (llave única)
2. Consecutivo de Manifiesto
3. Placa Vehículo (automotor)
4. Código secuencial del punto de control
5. Dirección del punto de control
6. Municipio del punto de control
7. Coordenadas georreferenciadas del punto de control
8. Fecha y hora cita de llegada al punto de control
9. Tiempo pactado en el punto de control (dato numérico sin decimales, equivalente a minutos)

El RNDC envía mínimo 1 punto de control por manifiesto. El punto de cargue puede llevar código secuencial 1, el de descargue código 2, y así sucesivamente. La fecha y hora de la cita puede llegar vacía para puntos de control intermedios definidos por el Ministerio de Transporte.

### Ejemplo XML: Respuesta del RNDC a la EMF

```xml
<?xml version="1.0" encoding="iso-8859-1" ?>
<root>
  <documento>
    <ingresoidmanifiesto>123456789</ingresoidmanifiesto>
    <numnitempresatransporte>9999999999</numnitempresatransporte>
    <nummanifiestocarga>111</nummanifiestocarga>
    <fechaexpedicionmanifiesto>03/09/2014</fechaexpedicionmanifiesto>
    <numplaca>bod874</numplaca>
    <puntoscontrol>
      <puntocontrol>
        <codpuntocontrol>1</codpuntocontrol>
        <codmunicipio>11001000</codmunicipio>
        <direccion>calle 1 3-51 parque industrial xxx</direccion>
        <fechacita>2018/11/05</fechacita>
        <horacita>16:07</horacita>
        <latitud>5.417198</latitud>
        <longitud>-72.290611</longitud>
        <tiempopactado>65</tiempopactado>
      </puntocontrol>
      <puntocontrol>
        <codpuntocontrol>2</codpuntocontrol>
        <codmunicipio>5001000</codmunicipio>
        <direccion>calle 30 -40</direccion>
        <fechacita>2018/11/06</fechacita>
        <horacita>08:00</horacita>
        <latitud>4.417198</latitud>
        <longitud>-73.290611</longitud>
        <tiempopactado>125</tiempopactado>
      </puntocontrol>
    </puntoscontrol>
  </documento>
  <!-- Documentos adicionales omitidos por brevedad -->
  <documento>
    <ingresoidmanifiesto>123456789</ingresoidmanifiesto>
    <ajuste>1</ajuste>
    <numnitempresatransporte>9999999999</numnitempresatransporte>
    <nummanifiestocarga>111</nummanifiestocarga>
    <fechaexpedicionmanifiesto>03/09/2014</fechaexpedicionmanifiesto>
    <numplaca>bod874</numplaca>
    <puntoscontrol>
      <puntocontrol>
        <codpuntocontrol>2</codpuntocontrol>
        <ajuste>1</ajuste>
        <codmunicipio>11001000</codmunicipio>
        <direccion>calle 1 3-51 parque industrial xxx</direccion>
        <fechacita>2018/11/05</fechacita>
        <horacita>16:07</horacita>
        <latitud>5.417198</latitud>
        <longitud>-72.290611</longitud>
        <tiempopactado>65</tiempopactado>
      </puntocontrol>
    </puntoscontrol>
  </documento>
</root>
```

### Etiqueta `<ajuste>` en la respuesta

Cuando un punto de control presenta la etiqueta `<ajuste>`, indica que la ETC ha realizado modificaciones en los atributos previamente definidos. La información se envía nuevamente con las nuevas condiciones para actualizar el monitoreo. Los posibles tipos de ajuste son:

1. Cambio en la Fecha y hora del Punto de control
2. Cambio en la sede del Punto de control
3. Cambio en la sede y fecha y hora del Punto de control
4. Anulación de Manifiesto de carga (Suspensión de Monitoreo)
5. Transbordo NO planeado (evento en carretera que suspende el viaje con la misma placa)

### Código de error por consultas frecuentes

| Código | Observación |
|---|---|
| GPS200 | La empresa de monitoreo de flota debe esperar 15 minutos para volver a consultar manifiestos autorizados. |

> **Nota:** Si la EMF consulta con frecuencia inferior a 15 minutos, el RNDC responderá con el error GPS200.

---

## 10. Registro Monitoreo de Manifiesto (RMM)

*Proceso que realiza la Empresa de Monitoreo de Flota.*

El Registro Monitoreo de Manifiesto (RMM) es el reporte de los tiempos logísticos reales enviado por la EMF. Incluye:
- Fecha-hora de llegada y fecha-hora de salida
- Coordenadas georreferenciadas
- Placa del vehículo
- Radicado del manifiesto de carga

Se realiza **una transacción por cada punto de control**.

**Reglas de tiempo para el envío del RMM:**

- La EMF debe implementar una ventana de tolerancia desde el momento en que es informada hasta **24 horas después** con relación a la fecha y hora de la cita del punto de control.
- Los reportes de fecha-hora de llegada y salida deben ser los tiempos reales del monitoreo, aunque el vehículo haya llegado antes de la cita.
- La EMF debe enviar la información del RMM **máximo en las 72 horas siguientes** a partir de la fecha y hora de llegada en cada punto de control.
- En caso de que el vehículo permanezca más de 72 horas en el punto de control, la EMF debe realizar el RMM con los datos de llegada y la etiqueta `<sinsalida>S</sinsalida>`.
- Si se supera el tiempo estipulado y la EMF envía el RMM de todos modos, el RNDC no acepta el registro y devuelve error `"72 horas vencidas"`. En ese caso, la EMF debe emitir un RNMM.

**Reglas SICE-TAC para el cálculo de tiempos:**

- Si la fecha-hora de llegada al punto de control es **anterior** a la fecha-hora de cita pactada, el RNDC tomará como hora de llegada la fecha-hora de la cita para el cálculo del tiempo de espera.
- Si la fecha-hora de llegada es anterior a la cita y el vehículo es atendido antes de la cita, los tiempos de espera son 0 y el tiempo de atención inicia con la entrada al punto de control.

El RNDC devuelve un número de radicado a la EMF como señal de aceptación. Cada manifiesto tendrá dos o más números de radicado de RMM.

### Ejemplo XML: RMM — Punto de Control 1

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuariogps</username>
    <password>passwordgps</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>60</procesoid>
  </solicitud>
  <variables>
    <numidgps>9999999999</numidgps>
    <ingresoidmanifiesto>123456789</ingresoidmanifiesto>
    <numplaca>bod875</numplaca>
    <codpuntocontrol>1</codpuntocontrol>
    <latitud>123.456</latitud>
    <longitud>123.456</longitud>
    <fechallegada>01/01/2017</fechallegada>
    <horallegada>08:32</horallegada>
    <fechasalida>01/01/2017</fechasalida>
    <horasalida>10:32</horasalida>
  </variables>
</root>
```

### Ejemplo XML: RMM — Punto de Control 2

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuariogps</username>
    <password>passwordgps</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>60</procesoid>
  </solicitud>
  <variables>
    <numidgps>9999999999</numidgps>
    <ingresoidmanifiesto>123456789</ingresoidmanifiesto>
    <numplaca>bod875</numplaca>
    <codpuntocontrol>2</codpuntocontrol>
    <latitud>123.456</latitud>
    <longitud>123.456</longitud>
    <fechallegada>02/01/2017</fechallegada>
    <horallegada>08:32</horallegada>
    <fechasalida>02/01/2017</fechasalida>
    <horasalida>10:32</horasalida>
  </variables>
</root>
```

### Ejemplo XML: RMM — Punto de Control 3 (sin salida)

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuariogps</username>
    <password>passwordgps</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>60</procesoid>
  </solicitud>
  <variables>
    <numidgps>9999999999</numidgps>
    <ingresoidmanifiesto>123456789</ingresoidmanifiesto>
    <numplaca>bod875</numplaca>
    <codpuntocontrol>3</codpuntocontrol>
    <latitud>123.456</latitud>
    <longitud>123.456</longitud>
    <fechallegada>02/01/2017</fechallegada>
    <horallegada>08:32</horallegada>
    <sinsalida>S</sinsalida>
  </variables>
</root>
```

### Ejemplo XML: Respuesta de aceptación del RNDC

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <ingresoid>123456</ingresoid>
</root>
```

### Ejemplo XML: Respuesta de no aceptación del RNDC

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <errormsg>error rmm020: falta el nro. radicado de manifiesto. usuario:169</errormsg>
</root>
```

### Anulación de Registro de Monitoreo de Manifiesto

En caso de que la EMF detecte un error en el RMM, puede enviar un registro de anulación.

#### Ejemplo XML: Anulación de RMM

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuariogps</username>
    <password>passwordgps</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>68</procesoid>
  </solicitud>
  <variables>
    <numidgps>9999999999</numidgps>
    <ingresoidrmm>1234</ingresoidrmm>
    <ingresoidmanifiesto>123456789</ingresoidmanifiesto>
    <numplaca>bod875</numplaca>
    <codpuntocontrol>2</codpuntocontrol>
    <observaciones>haciendo pruebas</observaciones>
  </variables>
</root>
```

#### Ejemplo XML: Respuesta del RNDC a la anulación

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <ingresoid>123456</ingresoid>
</root>
```

---

### 10.1 Ajuste Registro de Monitoreo de Manifiesto

*Proceso que realiza la Empresa de Transporte.*

En caso de que la empresa de transporte identifique inconsistencias en los tiempos logísticos reales reportados por la EMF, se hayan presentado novedades en el monitoreo, o haya incumplimiento de la EMF, la empresa de transporte podrá modificar los datos de llegada y salida al punto de control.

**Acceso al módulo:** Portal RNDC2 → menú **Cumplir >> Monitoreo Manifiesto**.

**Requisito de usuario:** La empresa de transporte debe tener un **usuario tipo 2 (Usuario de monitoreo)**. De lo contrario, el sistema mostrará el error: `"El usuario: XXXXX@1111 no está autorizado para usar esta opción."`

Para crear este usuario: ingresar a https://rndc2.mintransporte.gov.co/ con el usuario maestro (Tipo 6) → **Herramientas >> Administrar Usuarios >> Nuevo usuario** → seleccionar tipo **"Usuario Monitoreo de Flota"**.

**Generación de puntos de control:** La asignación de códigos a los puntos de control se realiza mediante la consulta de la EMF a los manifiestos autorizados (ver sección 9). Si el manifiesto a ajustar no ha sido consultado por la EMF, la empresa de transporte debe primero generar la codificación de los puntos de control mediante el botón **"GENERAR PUNTOS DE CONTROL DEL MANIFIESTO"**, ubicado en la parte inferior izquierda del formulario.

**Proceso de ajuste:**

1. Digitar el Consecutivo de Manifiesto o Radicado de Manifiesto; el sistema muestra la información general del manifiesto.
2. En el campo **Punto de control**, seleccionar el punto a modificar. El sistema muestra una codificación numérica con sufijo: **C** (puntos de cargue) o **D** (puntos de descargue).
3. Una vez identificado el punto, el sistema muestra automáticamente la información de la sede.
4. En el campo **Motivo de ajuste**, seleccionar el motivo correspondiente.

#### Motivos de Modificación de Tiempos Logísticos

| Código | Motivo |
|---|---|
| 1 | Operaciones afectadas por casos fortuitos o fuerza mayor (evento externo, imprevisible e irresistible que imposibilita el cumplimiento de una obligación). |
| 2 | Vehículo no sale de la geocerca después de realizar el cargue y/o descargue. |
| 3 | Superposición de sedes en manifiestos distintos. |
| 4 | Incumplimiento empresa de monitoreo de flota. |
| 5 | Empresa de monitoreo de flota reportó un RNMM. |
| 6 | Otra razón por la cual no está de acuerdo. |

> *Esta codificación numérica aplica para identificar los motivos a través de WEBSERVICE como se muestra en el ejemplo XML.*

Adicional al motivo, se debe diligenciar el campo **Observaciones** con el detalle de la novedad. Finalmente, en la sección **Tiempos Logísticos** se deben diligenciar los tiempos logísticos reales producto de la modificación.

#### Ejemplo XML: Ajuste de RMM

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuarioempresatransporte(tipo2)</username>
    <password>passworetc</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>60</procesoid>
  </solicitud>
  <variables>
    <numnitempresatransporte>1111</numnitempresatransporte>
    <numidgps>111</numidgps>
    <ingresoidmanifiesto>123456789</ingresoidmanifiesto>
    <numplaca>BOD875</numplaca>
    <codpuntocontrol>1</codpuntocontrol>
    <latitud>123.456</latitud>       <!-- opcional -->
    <longitud>123.456</longitud>     <!-- opcional -->
    <codmotivoajuste>1</codmotivoajuste>
    <observaciones>cierre puerto por lluvias</observaciones>
    <fechallegada>01/01/2017</fechallegada>
    <horallegada>08:32</horallegada>
    <fechasalida>01/01/2017</fechasalida>
    <horasalida>10:32</horasalida>
  </variables>
</root>
```

> **⚠️ NOTA:** El procedimiento para la modificación de los tiempos logísticos estará sujeto a supervisión y seguimiento permanente por parte del Ministerio de Transporte y de la Superintendencia de Transporte, quienes en ejercicio de sus competencias podrán efectuar los ajustes o actualizaciones que resulten pertinentes, con fundamento en los análisis efectuados sobre la información reportada al RNDC.

---

## 11. Registro de Novedades Monitoreo de Manifiesto (RNMM)

*Proceso que realiza la Empresa de Monitoreo de Flota.*

La EMF puede registrar los eventos que se presenten antes y durante la operación de transporte y que afecten el seguimiento y el reporte del RMM. Estos eventos se reportan al RNDC mediante el RNMM.

> **Plazo máximo:** Solo se recibirán novedades hasta **36 horas después** de la fecha y hora de la cita del punto de control.

### Tipos de novedad que puede reportar la EMF

| Código | Novedad |
|---|---|
| 1 | El vehículo no apareció en la ventana de tolerancia de la cita comparado con la fecha-hora de cita de cargue o descargue. *(Debe reportarse pasadas 24 horas y máximo hasta 1 hora después de vencidas las 24 horas.)* |
| 2 | La placa del vehículo no está registrada en la EMF. |
| 3 | El vehículo se encuentra suspendido o desactivado en la EMF. |
| 4 | La unidad remota instalada en el vehículo se encuentra funcionando mal. |
| 5 | No hay relación con la empresa de transporte (NIT mal relacionado). |
| 6 | No hay vías de acceso para llegar al punto de control. |

> **Nota:** Para las novedades 2, 3, 4 y 5, no es necesario enviar la etiqueta `<codpuntocontrol>` porque aplica para todos los puntos de control del manifiesto. En caso de enviar un segundo RNMM con estas novedades para el mismo manifiesto, el sistema mostrará un mensaje de error.

### Ejemplo XML: RNMM — Novedad tipo 1 (con punto de control)

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuariogps</username>
    <password>passwordgps</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>46</procesoid>
  </solicitud>
  <variables>
    <numidgps>9999999999</numidgps>
    <ingresoidmanifiesto>123456789</ingresoidmanifiesto>
    <numplaca>bod875</numplaca>
    <codpuntocontrol>1</codpuntocontrol>
    <codnovedad>1</codnovedad>
  </variables>
</root>
```

### Ejemplo XML: RNMM — Novedad tipo 2 (aplica a todos los puntos)

```xml
<?xml version='1.0' encoding='iso-8859-1' ?>
<root>
  <acceso>
    <username>usuariogps</username>
    <password>passwordgps</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>46</procesoid>
  </solicitud>
  <variables>
    <numidgps>9999999999</numidgps>
    <ingresoidmanifiesto>123456789</ingresoidmanifiesto>
    <numplaca>bod875</numplaca>
    <codnovedad>2</codnovedad>
  </variables>
</root>
```

### Respuestas del RNDC

**Aceptación de la novedad:**
```xml
<?xml version="1.0" encoding="iso-8859-1" ?>
<root>
  <ingresoid>1</ingresoid>
</root>
```

**Registro de novedad duplicado:**
```xml
<?xml version="1.0" encoding="iso-8859-1" ?>
<root>
  <errormsg>duplicado:1</errormsg>
</root>
```

### Límites porcentuales de RNMM

La cantidad de registros de RNMM no podrá superar los siguientes porcentajes con respecto al número total de Manifiestos Electrónicos de Carga autorizados en los últimos 30 días calendario:

| Rango de manifiestos en el mes | Porcentaje máximo de RNMM |
|---|---|
| Más de 1.000 manifiestos | 10% |
| Entre 500 y 1.000 manifiestos | 15% |
| Entre 100 y 499 manifiestos | 20% |
| Entre 50 y 99 manifiestos | 40% |
| Menos de 50 manifiestos | 50% |

### Límites porcentuales de incumplimiento

En la situación en que la EMF no reporte RNMM en el tiempo estipulado y tampoco realice el RMM, se contempla un **incumplimiento** por parte de la EMF. El total de incumplimientos no podrá superar los siguientes porcentajes:

| Rango de manifiestos en el mes | Porcentaje máximo de incumplimiento |
|---|---|
| Más de 1.000 manifiestos | 10% |
| Entre 500 y 1.000 manifiestos | 15% |
| Entre 100 y 499 manifiestos | 20% |
| Entre 50 y 99 manifiestos | 40% |
| Menos de 50 manifiestos | 50% |

En caso de superar el porcentaje establecido, **la ETC no podrá relacionar el NIT de esa EMF para nuevos manifiestos**. La ETC debe registrar un plan de acción en el RNDC, el cual habilita por **24 horas** para subsanar el incumplimiento y volver a relacionar el NIT de esa EMF.

El Ministerio de Transporte realizará seguimiento y análisis de la información suministrada. En caso de identificar mala calidad de los datos, realizará reporte a la Superintendencia de Transporte para que ejerza sus competencias de vigilancia, inspección y control.

> **Regla de contingencia:** En caso de existir RNMM o incumplimiento por parte de la EMF, **la empresa de transporte debe registrar los tiempos logísticos en el cumplido de remesa terrestre de carga**.

---

## 12. Distribución de Tiempos Logísticos Reales en Remesas

*Proceso que realiza el sistema RNDC.*

Teniendo en cuenta que un manifiesto electrónico de carga puede contener una o varias remesas, el RNDC identifica el tiempo logístico por cada punto de control y lo relaciona con cada remesa en base a los puntos de control.

En los casos en que un punto de control hace parte de dos o más remesas, se aplica la siguiente regla:

> **Regla de distribución proporcional:** Los tiempos logísticos reales de cada remesa de un mismo manifiesto de carga serán distribuidos **proporcionalmente de acuerdo con el peso total de la mercancía** en el punto de control.

La hora de llegada y hora de salida es la misma para todas las remesas, pero el tiempo logístico de cada remesa será el resultado de la distribución proporcional.

---

## 13. Cumplido Inicial de Remesa

*Proceso que realiza el sistema RNDC.*

A partir del registro de monitoreo de manifiesto (RMM), el RNDC genera automáticamente el registro de **cumplido inicial de remesa** para cada una de las remesas que pertenecen al manifiesto de carga. El sistema asignará un número de radicado a cada cumplido inicial de remesa, consultable únicamente por la ETC.

---

## 14. Cumplido de Remesa

*Proceso que realiza la Empresa de Transporte.*

A partir del cumplido inicial de remesa, se deben incluir los tiempos de **entrada al cargue** y **entrada al descargue** con la cantidad de la mercancía entregada.

> **Nota sobre anulación:** En caso de realizar un segundo cumplido de remesa, el sistema seguirá teniendo en cuenta la información del cumplido inicial de remesa.

---

## 15. Diccionario de Errores

El diccionario de errores es un proceso dinámico en el RNDC, consultable a través del portal interactivo:

**Ruta:** Menú Principal → **Consultar >> Consultar Maestros >> Diccionario de Errores**

De acuerdo con el proceso (columna 2), el sistema muestra la relación de errores activos.

<!-- Imagen: Tabla del Diccionario de Errores con columnas: Fecha Ingreso, PROCESO ID, CODIGO ERR, MENSAJE ERROR, VARIABLE, TIPO ERRO, PROCESO, SOLUCIÓN. Errores mostrados incluyen: GPS042 (placa no corresponde al manifiesto), GPS041 (manifiesto no enviado para monitoreo), AMM020 (faltan observaciones para anular), AMM011 (registro no existe o no activo), AMM014 (NUMIDGPS no corresponde a la empresa), AMM013 (falta placa del manifiesto), AMM012 (falta ingreso ID del manifiesto), AMM010 (falta ingreso ID del registro a anular), AMM015 (falta punto de control), AMM005 (usuario no existe), AMM007 (usuario no existe en empresa GPS), AMM006 (usuario no pertenece a empresa de monitoreo). Proceso 46 corresponde a Novedades Empresas GPS; proceso 68 a Anular Monitoreo Manifiesto. -->

---

## 16. Plan de Contingencia RNDC

El Ministerio de Transporte monitoreará permanentemente el funcionamiento del sistema RNDC. En caso de ser necesario realizar tareas de mantenimiento, se informará oportunamente a los usuarios para que den inicio al plan de contingencia.

También aplica para eventos fortuitos que afectan la operatividad del RNDC para todos los usuarios.

> **Exclusión:** El plan de contingencia **no aplica** cuando los actores del RNDC no pueden acceder al sistema por fallas tecnológicas atribuibles a sus propios sistemas de información.

### Procedimiento durante contingencia

La ETC puede realizar el viaje generando el **documento en papel del manifiesto de carga**, sin número de radicado y sin código QR. Los formatos están disponibles en el Portal Interactivo.

Si durante la ejecución de una operación de transporte se activa el plan de contingencia y la EMF está realizando el seguimiento al vehículo, por la situación de contingencia del RNDC no es posible realizar el envío de información de tiempos logísticos. La EMF deberá realizar el envío **una vez sea restablecido el servicio del RNDC**.

Los registros deberán ser reportados al RNDC en un término **máximo de 24 horas** contados a partir de la hora en que se restableció el servicio.

Cuando por causa de la contingencia la EMF no pueda conocer las operaciones futuras para las que ha sido autorizada:
- Una vez restablecido el RNDC, **no se enviará información de los puntos de control con fecha y hora de cita pasada**.
- Para esos puntos de control, **la empresa de transporte relaciona los tiempos logísticos en el cumplido de remesa**.

---

## 17. Estadísticas de Información de la Empresa de Monitoreo de Flota

El sistema RNDC consolida la información de los registros realizados por la EMF y los valida con la ETC. En el Portal Interactivo del RNDC, la EMF tendrá acceso al módulo de consultas con la siguiente información:

1. Registros enviados del RNDC a la EMF para hacer seguimiento y reportar los tiempos logísticos reales.
2. Registros de RMM realizados por la EMF.
3. Registros con novedades enviados por la EMF.
4. Número de anulaciones de registros RMM de la EMF.
5. Cantidad de rechazos de la ETC a los registros RMM.

---

## 18. Consultas para la EMF

### 18.1 Consulta de ETC que han relacionado el NIT como estándar para el reporte de tiempos logísticos

**Ruta:** Portal interactivo RNDC2 → **Herramientas >> Información Empresa** → sección **Afiliados**

<!-- Imagen: Pantalla del portal RNDC con menú Herramientas. Sección de Afiliados con tabla de ETC que han relacionado el NIT estándar, mostrando columnas ID, Nombre y Tipo Empresa. Ejemplos de empresas listadas: ENVI&CIA S.A.S, COOPERATIVA MULTIACTIVA DE TRANSPORTADORES CIMPRA LTDA, INBERTRANS HB S.A.S, LOGÍSTICA DE COLOMBIA S.A.S., ULTRASERVICIOS DE TRANSPORTE S.A.S. -->

Desde esta sección se pueden visualizar las empresas de transporte que han relacionado el NIT como un NIT estándar para el monitoreo de manifiestos.

### 18.2 Consultas de Documentos

**Ruta:** Portal interactivo RNDC2 → menú **Consultas >> Consultas a Documentos**

<!-- Imagen: Pantalla del portal RNDC con menú Consultas desplegado, mostrando opciones: Consultas a Documentos, SiceTac Remesa, Consultar Documentos Pendientes de Cumplir, Consultar Maestros, Información de Control de RNDC, Consultar Cubos de Información, Registros de Otras Entidades. Formulario de consulta con campos: Consulta de Documentos del Proceso, Fecha Inicial Radicación, Fecha Final Radicación. Nota: "Use el % si desea una cadena iniciando en los caracteres digitados. Ej. Barranacabermeja, etc. Máximo 50.000 registros". -->
