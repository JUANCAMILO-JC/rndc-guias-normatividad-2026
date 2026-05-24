---
title: "Guía de Manifiesto Electrónico de Carga - RNDC"
source: "Guia_de_Manifiesto_V3_compressed.pdf"
date_converted: "2026-05-24"
total_sections: 9
version: "03"
date_document: "12 de mayo de 2026"
issuer: "Ministerio de Transporte de Colombia"
---

# Guía de Manifiesto Electrónico de Carga (RNDC)

**Documento:** Guía de Manifiesto — Actividades a realizar para expedir el Manifiesto Electrónico de Carga
**Versión:** 03
**Fecha:** 12 de mayo de 2026
**Entidad:** Ministerio de Transporte de Colombia

---

## Control de Cambios

| Versión | Elaborado por | Revisado por | Aprobado por |
|---------|---------------|--------------|--------------|
| 3 | Edna Lorena Gutiérrez | Jairo Vesga | Juan Felipe Sanabria Saetta |

| Fecha | Descripción de la modificación |
|-------|-------------------------------|
| 09/04/2026 | Versión Inicial |
| 06/05/2026 | Tipo de Manifiesto: Viaje Urbano o Municipal / Viaje Vacío |
| 12/05/2026 | Modelo Manifiesto con municipio intermedio |

---

## Tabla de Contenido

- [Introducción](#introducción)
- [1. Manifiesto Electrónico de Carga](#1-manifiesto-electrónico-de-carga)
- [2. Ingreso al Sistema RNDC](#2-ingreso-al-sistema-rndc)
- [3. Módulo Manifiesto Electrónico de Carga](#3-módulo-manifiesto-electrónico-de-carga)
- [4. Expedir Manifiesto](#4-expedir-manifiesto)
  - [4.1 Datos Generales del Manifiesto](#41-datos-generales-del-manifiesto)
  - [4.2 Información Preliminar](#42-información-preliminar)
  - [4.3 Características del Manifiesto](#43-características-del-manifiesto)
  - [4.4 Titular del Manifiesto](#44-titular-del-manifiesto)
  - [4.5 Vehículo](#45-vehículo)
  - [4.6 Conductor 1](#46-conductor-1)
  - [4.7 Conductor 2 (opcional)](#47-conductor-2-opcional)
  - [4.8 Valor de Viaje](#48-valor-de-viaje)
  - [4.9 Datos de Control](#49-datos-de-control)
  - [4.10 Remesas](#410-remesas)
- [5. Mensajes de Error](#5-mensajes-de-error)
- [6. Diccionario de Datos](#6-diccionario-de-datos)
- [7. Formato de Manifiesto V3](#7-formato-de-manifiesto-v3)
- [8. Ejemplo XML Manifiesto](#8-ejemplo-xml-manifiesto)

---

## Introducción

Este documento permitirá conocer el proceso a seguir para el reporte o registro de manifiesto electrónico de carga en el sistema Registro Nacional de Despachos de Carga (RNDC).

---

## 1. Manifiesto Electrónico de Carga

**Manifiesto de carga o manifiesto electrónico de carga:** Es el documento expedido a través del Sistema del Registro Nacional de Despachos de Carga (RNDC), de manera gratuita por la empresa de transporte, que ampara el transporte de mercancías ante las distintas autoridades.

Características y funciones clave:

- Debe ser portado por el conductor del vehículo durante todo el recorrido.
- El manifiesto de carga cumplido se utilizará para llevar las estadísticas del transporte público de carga por carretera dentro del territorio nacional.
- Una vez sea ejecutado el contrato de transporte, el manifiesto de carga prestará mérito ejecutivo con el cumplimiento de las condiciones de claridad, carácter expreso de la obligación y exigibilidad actual, establecidas en el artículo 422 del Código General del Proceso.

---

## 2. Ingreso al Sistema RNDC

Las empresas de transporte pueden enviar la información del manifiesto usando dos mecanismos:

- **Portal web interactivo:** Acceso en [https://rndc2.mintransporte.gov.co/Ingresar/Iniciar-Sesión](https://rndc2.mintransporte.gov.co/Ingresar/Iniciar-Sesi%C3%B3n)
- **Webservice del RNDC:** Las empresas que usen el webservice deben extraer la URL correcta del archivo WSDL.

### Acceso por portal web

Ingresar usuario y contraseña. Se recomienda utilizar los **usuarios TIPO (1) - Dependientes** para el ingreso al sistema (no el usuario Principal).

### Acceso por webservice

- URL principal: `rndcws.mintransporte.gov.co:8080/ws`
- URL alternativa (mejora tiempo de respuesta): `rndcws2.mintransporte.gov.co:8080/ws`

El Ministerio de Transporte puede disponer de otro archivo WSDL con el fin de mejorar el servicio del tiempo de respuesta del RNDC.

---

## 3. Módulo Manifiesto Electrónico de Carga

En los módulos disponibles del sistema, hacer clic en el menú **EXPEDIR**. Se despliega la opción **Manifiesto Electrónico de Carga**.

Opciones disponibles en el menú EXPEDIR:

- Remesa
- Manifiesto
- Reimprimir Manifiesto
- Reimprimir Remesa
- Corregir Remesa
- No Expedición Manifiesto en el Mes

---

## 4. Expedir Manifiesto

Al hacer clic en la opción de Manifiesto Electrónico de Carga, el sistema muestra la información que debe diligenciarse en cada casilla, de acuerdo con la tipología de las operaciones del transporte.

> **Requisito previo:** La empresa de transporte debe tener la habilitación activa.

---

### 4.1 Datos Generales del Manifiesto

En la parte superior se visualiza el nombre de la Empresa de Transporte con su respectivo NIT. El usuario debe verificar que los datos coincidan con los de la empresa.

**Control de manifiestos pendientes:**

Cada vez que una empresa de transporte desee expedir un nuevo manifiesto, el sistema verificará que la cantidad de registros de Cumplido de Manifiestos pendientes por registrar no supere el **20%** del número total de Manifiestos Electrónicos de Carga expedidos en los últimos 30 días calendario.

Condición de bloqueo:
- Se cuentan los manifiestos con más de **5 días hábiles** de retraso, contados desde la fecha de entrega de la mercancía registrada en el Cumplido de Remesa (fecha y hora de salida del descargue), o desde la cita pactada para el descargue si no se ha reportado el Cumplido de Remesa.
- De superarse el 20%, el sistema no permitirá la generación de nuevos Manifiestos Electrónicos de Carga.
- El sistema provee a la empresa de transporte una funcionalidad para consultar la lista de los manifiestos pendientes de cumplir cuya fecha ya expiró.

---

### 4.2 Información Preliminar

**Consecutivo del Manifiesto:**

- Debe estar compuesto por números y letras.
- Puede tener hasta **15 caracteres**.
- El sistema valida que no se repita el consecutivo dentro de la misma empresa de transporte (es el consecutivo interno de la empresa).
- El consecutivo debe estar en el rango autorizado por la empresa de transporte para el usuario que intenta expedir el manifiesto. Esto se configura con el usuario principal Tipo 6 para cada uno de los usuarios dependientes tipo 1 en el programa de administrar usuarios.

> No se permiten manifiestos duplicados. El RNDC vigila que el consecutivo del manifiesto no se repita.

**Opciones para crear un Manifiesto Electrónico de Carga:**

- **Información de Viaje:** Si se registró previamente la información de viaje, se puede reportar ese consecutivo y el sistema creará una ligación entre dicho consecutivo y el nuevo manifiesto. El sistema valida que ese consecutivo esté registrado por la misma empresa de transporte. *Nota: Se mantiene por compatibilidad con versiones anteriores; se sugiere a las empresas de transporte no utilizarlo.*

- **Radicado de Viaje Consolidado:** Este dato está pendiente de viabilidad normativa.

- **Manifiesto anterior para Transbordo o Reemplazo:** Para realizar el trasbordo de remesas a un nuevo manifiesto, se digita el número consecutivo del manifiesto anterior. Para reemplazar un manifiesto por errores de digitación, se utiliza este campo.

  Reglas de trasbordo:
  - La empresa de transporte debe digitar el consecutivo interno asignado al manifiesto que transporta la mercancía desde el punto de cargue hasta el punto de transbordo.
  - El RNDC valida que el manifiesto anterior esté pendiente de iniciar el viaje (trasbordo planeado) o cumplido con tipología de suspensión del viaje (trasbordo no planeado).
  - Para estos casos, la remesa terrestre de carga es la misma para los dos manifiestos (no se debe generar una nueva remesa).

---

### 4.3 Características del Manifiesto

El usuario debe escoger el **Tipo de Manifiesto** de las siguientes opciones:

#### a) General

Manifiesto que ampara o sustenta la operación de transporte en un viaje diferente a las operaciones: varios viajes en el día, en vacío, Multiparada, ida y regreso y Viaje Municipal o Urbano.
**Código XML (webservice):** `G`

#### b) Viaje Vacío

Manifiesto de un viaje en vacío: trayecto que realiza un vehículo de transporte sin llevar ninguna mercancía. Este tipo de manifiesto no lleva remesa.
**Código XML (webservice):** `W`

#### c) Ida y Regreso

Manifiesto que ampara la operación de transporte correspondiente a un viaje de ida y regreso (Round Trip) donde el origen y destino es un mismo municipio. La empresa de transporte debe definir el municipio intermedio o de retorno. Es ejecutado por un mismo vehículo de servicio público de transporte de carga. Transporta mínimo dos remesas, las cuales pueden ser de generadores de carga distintos.
**Código XML (webservice):** `I`

#### d) Multiparada

Manifiesto que ampara la operación de transporte en un viaje que incluye paradas en municipios intermedios de la ruta origen-destino del manifiesto, para hacer operaciones de cargue o descargue. Se debe asociar más de una remesa, las cuales pueden ser de generadores de carga distintos.
**Código XML (webservice):** `M`

#### e) Viaje Municipal o Urbano

Manifiesto que ampara las operaciones de transporte de carga en el radio de acción municipal, sus áreas urbanas (viaje urbano) y sus áreas rurales (viaje rural) pertenecientes a la misma cabecera municipal.
**Código XML (webservice):** `U`
> Remesa por proceso No. 3 y Manifiesto Proceso No. 04

#### f) Varios Viajes en el Día

Manifiesto que ampara la operación de transporte que se desarrolla en un mismo día y en un único vehículo, para trasladar una cantidad de carga que requiera varios viajes en una misma ruta origen-destino. Solo se podrá asociar una sola remesa.
**Código XML (webservice):** `D`

#### g) Varios Viajes Municipales en el Día

Variante de varios viajes en el día para el ámbito municipal.

---

#### Campos de Características del Manifiesto

**Fecha de Expedición del Manifiesto:**

- Es la fecha en que se planea la realización del proceso de cargue de la primera remesa. No necesariamente coincide con la fecha de radicación en el sistema RNDC, pero puede hacerlo.
- No puede ser una fecha futura mayor a **30 días**.

**Manifiesto Tardío:**

- Aquel en el cual la fecha de expedición es menor a la fecha del sistema RNDC (fecha de radicación).
- La fecha de expedición no puede ser menor a la fecha del sistema RNDC menos **30 días**.
- Los manifiestos tardíos no pueden sobrepasar el **10%** de la cantidad de manifiestos expedidos en los últimos 30 días. De sobrepasarse, se debe solicitar autorización en el programa **AUTORIZAR ALERTA** y seleccionar el permiso para expedir manifiestos tardíos.
- Para manifiestos con fecha de expedición anterior a los 30 días, solicitar autorización para **manifiestos super tardíos** en el mismo programa.

**Límite por placa:**

No se permite la expedición de más de **10 manifiestos** para la misma fecha de expedición de una placa de automotor, excepto para manifiestos de tipo municipal. De requerirse más, la empresa de transporte deberá registrar previamente la excepción en el RNDC.

**Viajes en el día:**

Solo se digita cuando se selecciona el tipo de manifiesto *Varios Viajes en el Día*. Se planea la cantidad de viajes que puede realizar el vehículo en el mismo día. La validez de esta operación va hasta las **23:59** del día definido como fecha de expedición.

**Municipio Origen:**

- Municipio donde se origina el contrato de transporte. Se puede escribir el nombre de una vereda o centro poblado perteneciente a la cabecera municipal.
- El sistema muestra una lista desplegable con coincidencias y el código DIVIPOLA.
- Cuando el contrato incluya trayecto en vacío antes de recoger la primera mercancía, el municipio origen debe ser aquel donde se inicia el trayecto en vacío (no donde se recoge la mercancía).
- El municipio Origen debe coincidir con mínimo un sitio de cargue de alguna de las remesas a transportar.

**Municipio Intermedio:**

- Obligatorio cuando el tipo de manifiesto es **Ida y Regreso**.
- Es el municipio donde el vehículo se devuelve hacia el municipio origen.

**Municipio Destino:**

- Municipio donde se entregarán las mercancías.
- Para el tipo **Ida y Regreso**, debe ser igual al municipio origen.
- Para manifiesto **municipal**, el municipio destino puede ser igual al municipio origen (o diferente si incluye veredas), pero los primeros 5 dígitos del código DIVIPOLA deben ser iguales entre municipio origen y destino.
- Cuando el contrato incluya trayecto en vacío después de entregar la última mercancía, el municipio destino debe ser aquel donde se termina ese trayecto en vacío.

**Vía a Utilizar:**

- La empresa puede seleccionar la vía por la cual el vehículo realiza el tránsito.
- Al seleccionar la vía, el sistema consulta el SICETAC para conocer el valor de referencia mínimo a pagar.
- Si el usuario no selecciona la vía, el sistema asigna la vía estándar del SICETAC para la ruta origen-destino.

**Municipio Origen Vacío 1:**

Si la empresa acordó con el transportador un valor a pagar para un trayecto en vacío antes del cargue de la primera remesa, se reporta el municipio desde donde se inicia ese trayecto (igual al municipio origen del manifiesto).

**Municipio Destino Vacío 1:**

Si se reportó el municipio origen vacío 1, se reporta el municipio destino vacío 1, que debe coincidir con el municipio de cargue de la primera remesa.

**Municipio Origen Vacío 2:**

Si la empresa acordó un valor a pagar para un trayecto en vacío después del descargue de la última remesa, se reporta el municipio desde donde inicia ese trayecto (igual al municipio del descargue de la última remesa del manifiesto).

**Municipio Destino Vacío 2:**

Si se reportó el municipio origen vacío 2, se reporta el municipio destino vacío 2, que debe coincidir con el municipio destino del manifiesto.

---

### 4.4 Titular del Manifiesto

El **Titular del Manifiesto** es el propietario, poseedor o tenedor de un vehículo de servicio público de carga. Es a quien se le cancela el Valor a Pagar.

Campos requeridos:

- **Tipo de Identificación:** Seleccionar de la lista desplegable.
- **Número de Identificación:** Escribir el número de identificación del titular del manifiesto.
- **Sede:** Seleccionar el nombre o número de la sede del titular del manifiesto.

Al escribir correctamente el número de identificación, el sistema muestra automáticamente los datos de nombre, dirección, municipio y teléfono, registrados previamente en la funcionalidad **Herramientas > Terceros**.

Restricciones:

- Si el tipo de identificación del titular es NIT, debe especificarse el dígito de chequeo según normatividad colombiana.
- No se puede reportar como titular el NIT del banco o de la entidad financiera que administra el leasing o renting del vehículo. En ese caso, el titular debe ser el tenedor o locatario del vehículo según el RUNT.

---

### 4.5 Vehículo

**Placa Vehículo:**

- La empresa de transporte digita la placa del vehículo automotor que transportará las mercancías.
- El vehículo debe estar previamente vinculado al parque automotor de la empresa mediante la funcionalidad **Herramientas > Vehículos Remolques**.
- El sistema muestra información del RUNT: configuración, peso vacío, tenedor del vehículo, póliza SOAT, vencimiento, aseguradora.

Requisitos de la placa del automotor (registro RNA del RUNT):

- Matrícula Activa
- Servicio Público
- Modalidad de Carga

Validaciones automáticas:

- La fecha de vencimiento del **SOAT** debe ser mayor a la fecha más alta de las citas de descargue de las remesas cargadas en el manifiesto.
- La fecha de vencimiento del **RTM** debe ser mayor a la fecha más alta de las citas de descargue (excepto para vehículo nuevo con menos de 2 años desde la matrícula, según disposición vigente).
- La placa no puede tener anotación de "automotor con omisiones en el registro inicial" en el RUNT ni en el RNDC.

**Placa Remolque:**

Si el vehículo automotor arrastra un remolque o semirremolque, se digita la placa de esa unidad (debe estar en el registro RNR del RUNT). El sistema muestra: configuración, peso vacío, vencimiento RTM.

**Configuración Resultante:**

Campo automático (no digitar). El sistema muestra la combinación de cabezote y remolque/semirremolque, que debe estar dentro de la lista de configuraciones permitidas (consultable en el RNDC).

**Permiso INVIAS Carga Extra:**

Campo automático (no digitar). El sistema verifica que la placa del cabezote y del remolque estén especificadas en el permiso de carga extra-pesada o extra-dimensionada expedida por INVIAS, cuando la naturaleza de la carga de alguna remesa sea extra-pesada o extra-dimensionada.

---

### 4.6 Conductor 1

**Tipo Identificación:** La empresa de transporte selecciona el tipo de identificación del conductor.

**Número Identificación:** Escribir el número de identificación del conductor del vehículo sin puntos, comas o caracteres especiales. Al oprimir la tecla tabular, el sistema consulta y muestra: nombre, teléfono, municipio, categoría de licencia, vencimiento y número de la licencia.

**Vencimiento Curso Mercancía Peligrosa:**

Campo automático (no digitar). El sistema verifica en línea con el sistema SISCOMMP si existe el curso para el respectivo conductor. El curso debe tener fecha de vencimiento posterior a la fecha de la cita de descargue de las remesas de naturaleza Mercancías Peligrosas.

**Vigencia de la licencia de conducción:**

Debe ser mayor a la máxima fecha de cita de descargue de las remesas cargadas en el manifiesto.

---

### 4.7 Conductor 2 (opcional)

El sistema RNDC permite adicionar un segundo conductor desde el inicio de la operación del transporte.

Campos: idénticos al Conductor 1 (Tipo Identificación, Número Identificación, datos automáticos del sistema).

El segundo conductor debe cumplir los mismos requisitos del primer conductor.

**Vencimiento Curso Mercancía Peligrosa:** Campo automático verificado en línea con SISCOMMP. El curso debe tener fecha de vencimiento posterior a la fecha de la cita de descargue de las remesas de naturaleza Mercancías Peligrosas.

---

### 4.8 Valor de Viaje

Campos del bloque Valor del Viaje:

**Valor a Pagar por el Viaje:**

- Es el valor que se paga por el servicio de transporte de las mercancías al titular del manifiesto.
- Debe ser **mayor o igual** al costo mínimo de referencia del SICETAC.
- Excepción: cuando la identificación del titular del manifiesto y la identificación del tenedor del vehículo automotor es igual a la identificación de la empresa de transporte (**Transporte en Flota Propia**), el valor debe ser **0**.
- Las empresas de transporte únicamente podrán expedir manifiestos que registren un valor a pagar igual o superior a los costos eficientes de operación de SICETAC.

**Valor Trayecto Vacío 1:**

Valor a pagar del trayecto recorrido por el vehículo desde el municipio origen del manifiesto hasta el lugar del cargue de la primera mercancía.

**Valor Trayecto Vacío 2:**

Valor a pagar del trayecto recorrido por el vehículo desde el lugar de descargue de la última mercancía hasta el municipio destino del manifiesto.

**Retención en la Fuente:**

- Descuento autorizado del valor a pagar del manifiesto electrónico de carga.
- Es un pago anticipado del impuesto de renta del titular del manifiesto.
- Si el titular pertenece al **régimen simple de tributación**, este valor es **0** (el sistema lo asigna automáticamente).
- El sistema calcula este valor con base en el porcentaje definido por el gobierno para la actividad del transporte de carga (no es un porcentaje, es el valor calculado).

**Retención de ICA:**

- Descuento autorizado del valor a pagar, definido por el municipio del sitio de cargue de cada remesa.
- Este dato es el factor con base en mil (no el valor resultado del cálculo).
- El valor base para aplicar la retención de ICA es: **Valor a Pagar − Valor Trayecto Vacío 1 − Valor Trayecto Vacío 2**.
- Para manifiestos con varias remesas (Multiparada) con municipios de cargue diferentes y factores distintos, se debe calcular la suma en dinero de los valores de retención de ICA y comparar con el valor a pagar para obtener el factor de retención de ICA (promedio ponderado).

**Retención FOPAT (0.1%):**

- Descuento autorizado y **obligatorio**.
- El RNDC verifica que sea igual al **0.1%** del Valor a Pagar del Manifiesto Electrónico de Carga.
- El valor no debe tener decimales (ajustar al peso más cercano).
- Corresponde al aporte para la financiación de la Subcuenta de Modernización de Transporte de Carga Pesada del Fondo para la Promoción de Ascenso Tecnológico (FOPAT), conforme al artículo 2.2.1.7.7.16 del Decreto 1079 de 2015.
- Aplica únicamente para vehículos con peso bruto vehicular **mayor a 10.5 toneladas**, según la Ley 2251 de 2022, Artículo 21.

**Neto a Pagar:**

Resultado de restar los descuentos autorizados al valor a pagar del manifiesto electrónico de carga.

**Responsable de Pago en Cargue:**

Seleccionar quién es el responsable del pago del servicio de cargue: Destinatario o Remitente.

**Responsable de Pago en Descargue:**

Seleccionar quién es el responsable del pago del servicio de descargue: Destinatario o Remitente.

**Valor Anticipo:**

Valor entregado por la empresa de transporte al titular del manifiesto (o a quien este designe) antes de iniciar el viaje. Puede ser cero y máximo el valor neto a pagar.

**Saldo por Pagar:**

Resultado de restar el valor anticipo del neto a pagar.

**Lugar de Pago:**

Municipio donde se realizará el pago del saldo a pagar del manifiesto electrónico de carga.

**Fecha de Pago:**

La fecha pactada para el pago del saldo no puede ser mayor a la fecha máxima de pago definida en el artículo 2.2.1.7.6.6 del Decreto 1079 de 2015: **5 días hábiles** después de la fecha de entrega de la mercancía (fecha pactada de la cita de descargue).

**Recomendaciones:**

Campo de texto libre para registrar observaciones o recomendaciones para el transporte de las mercancías. Máximo **500 caracteres**.

---

### 4.9 Datos de Control

**Firma de Aceptación Electrónica:**

Indica si la firma de aceptación por parte del titular del manifiesto electrónico de carga se realizará por medios electrónicos, a través de la aplicación para dispositivos móviles del RNDC transportador.

**Empresa de Monitoreo de Flota:**

Seleccionar de la lista desplegable la empresa de monitoreo de flota (EMF) que registrará en el RNDC los tiempos logísticos al manifiesto.

---

### 4.10 Remesas

La empresa de transporte debe seleccionar o escribir el consecutivo interno de las remesas a adjuntar al manifiesto electrónico de carga.

Reglas:

- Las remesas cargadas en un manifiesto **no deben haber sido cargadas en otro manifiesto**, excepto cuando hay trasbordo de remesas.
- La sumatoria de los pesos de la mercancía de todas las remesas, peso vacío del cabezote, peso vacío de los remolques y peso vacío de los contenedores, **no puede ser mayor** al tope máximo de la configuración combinada.
  - El RNDC valida el peso vacío del remolque/semirremolque con la información de la ficha técnica de homologación suministrada en el RUNT.
  - Para vehículos motorizados, el peso vacío es suministrado por las empresas de transporte.
  - Para vehículos automotores rígidos, el tope máximo se valida con el peso bruto vehicular suministrado por el RUNT.
- La sumatoria de los pesos de las remesas cargadas debe ser **mayor al peso mínimo de referencia**, determinado como control de calidad según la configuración combinada, publicado en el portal del RNDC.
  - Si la empresa requiere registrar un peso inferior al mínimo de referencia, deberá registrar la excepción en el RNDC asumiendo la responsabilidad sobre este dato.
- La remesa debe estar en estado **ACTIVO (AC)**: no puede estar cumplida (CE) ni anulada (AN).

---

## 5. Mensajes de Error

Los mensajes de error del sistema RNDC están disponibles en: **Consultar > Consultar Maestros > Diccionarios de Errores**.

Estructura de los códigos de error de manifiestos:

- Todos los errores al expedir un manifiesto tienen la estructura: **`MAN` + tres dígitos**
- Ejemplo: `MAN006`, `MAN007`, `MAN051`, `MAN067`, `MAN055`

Ejemplos de errores comunes:

| Código | Mensaje de Error |
|--------|-----------------|
| MAN006 | El valor a pagar del manifiesto no puede ser mayor a 0 cuando el titular del manifiesto es la misma empresa de transporte que expide el manifiesto. |
| MAN007 | La empresa de transporte no registró NIT de la empresa de monitoreo para el reporte de tiempos logísticos. |
| MAN051 | No existe el registro de topes en el valor a pagar del manifiesto. |
| MAN067 | Falta el NIT de la empresa de Monitoreo de Flota. |
| MAN055 | El transporte de Mercurio solo se puede hacer con la Naturaleza = Residuo Peligroso. |

---

## 6. Diccionario de Datos

El diccionario de datos del **Proceso 4 – Expedición de Manifiestos** está disponible en el sistema RNDC: **Consultar > Consultar Maestros > Diccionario de Datos**.

Ejemplos de variables del diccionario:

| Variable | Proceso | Tipo Dato | Req. | Descripción |
|----------|---------|-----------|------|-------------|
| NITMONITOREOFLOTA | 4 - Manifiesto de Carga | Varchar (15) | N | Nit de la flota. Monitoreo de flota debe ser parte de la lista de empresas. Monitoreo de flota de flota registrados en el sistema. |
| TIPOVALORPACTADO | 4 - Manifiesto de Carga | — | N | Tipo de valor pactado no se digita el RNDC asume Valor por Viaje. |
| VIAJESDIA | 4 - Manifiesto de Carga | Numérico | N | Cantidad de viajes no puede ser mayor a la cantidad de viajes de manifiestos de tipo Varios Viajes en el Día, dividido por la duración de el Día. |
| CODMUNICIPIOINTER MEDIO | 4 - Manifiesto de Carga | Numérico (8) | N | Código del municipio intermedio de los viajes de Ida y Regreso y Varios Viajes Municipales en el Día, es una representación digital (para efectos de autenticidad). Archivo Anexo a los Manuales RNDC tabla División Política Administrativa. |

---

## 7. Formato de Manifiesto V3

<!-- Imagen: Formato oficial del Manifiesto Electrónico de Carga V3 con campo de Municipio Intermedio -->

El formato físico/impreso del Manifiesto Electrónico de Carga versión 3 incluye los siguientes bloques de información:

**Encabezado:**

- Nombre de la empresa de transporte, NIT, dirección, teléfono, ciudad
- Número de manifiesto (ej. `Manifiesto: A12345C`)
- Autorización (ej. `Autorización: 70653092`)
- Fecha y hora de radicación

**Información del Viaje:**

| Campo | Ejemplo |
|-------|---------|
| Fecha Expedición | 2022/08/15 |
| Tipo de Manifiesto | Viaje Ida y Regreso |
| Origen del Viaje | BOGOTA BOGOTÁ D.C. |
| Municipio Intermedio | FUSAGASUGA CUNDINAMARCA |
| Destino del Viaje | BOGOTA BOGOTÁ D.C. |

**Información del Vehículo y Conductores:**

- Titular del manifiesto: nombre, documento de identificación, dirección, teléfonos, ciudad
- Placa, marca, placa semirremolque, configuración, peso vacío
- Póliza SOAT, vencimiento, aseguradora, VenceRTM
- Conductor(es): nombre, documento, dirección, teléfonos, categoría licencia, número de licencia, ciudad conductor

**Información de la Mercancía Transportada:**

| Columna | Descripción |
|---------|-------------|
| No. Remesa | Consecutivo de la remesa |
| Unidad Medida | Kilogramos |
| Cantidad | Cantidad de mercancía |
| Naturaleza | Ej. Carga Normal |
| Embalaje | Ej. Paquetes |
| Información Remitente / Lugar Cargue | Nombre, dirección, ciudad del remitente |
| Información Destinatario / Lugar Descargue | Nombre, dirección, ciudad del destinatario |
| Dueño Predio | Indicación si existe o no póliza |

**Valores:**

| Campo | Valor ejemplo |
|-------|--------------|
| Valor Total del Viaje | 1.300.000,00 |
| Retención en la Fuente | 13.000,00 |
| Retención ICA | 1.900,00 |
| Retención FOPAT | 0,00 |
| Valor Neto a Pagar | 1.285.200,00 |
| Valor Anticipo | 100.000,00 |
| Saldo a Pagar | 1.185.700,00 |
| Valor Total del Viaje en Letras | UN MILLÓN TRESCIENTOS MIL PESOS |

**Lugar de Pago:** BOGOTÁ BOGOTÁ D.C.
**Fecha de Pago:** 2022/09/16

**Responsable del Pago en Cargue:** (según configuración)
**Responsable del Pago en Descargue:** DESTINATARIO

**Observaciones:** NINGUNA

**Leyenda de autenticidad:** La impresión en soporte celular (papel) de este acto administrativo, producido por medios electrónicos da cumplimiento a la Ley 962 de 2005 (Artículo 6), es una representación digital (para efectos de autenticidad), el original electrónico se encuentro en la Base de Datos del RNDC en el Ministerio de Transporte; cuya representación digital (para efectos de autenticidad), integridad y no repudio.

**Espacios de firma:** Firma y Huella TITULAR MANIFIESTO o ACEPTACIÓN DIGITAL | Firma y Huella del CONDUCTOR o ACEPTACIÓN DIGITAL

---

## 8. Ejemplo XML Manifiesto

Ejemplo de un manifiesto con FOPAT enviado por webservice:

```xml
<root>
  <acceso>
    <username>xxxx</username>
    <password>xxxx</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>4</procesoid>
  </solicitud>
  <variables>
    <NUMNITEMPRESATRANSPORTE>xxxx</NUMNITEMPRESATRANSPORTE>
    <NUMMANIFIESTOCARGA>xxxx</NUMMANIFIESTOCARGA>
    <CODOPERACIONTRANSPORTE>G</CODOPERACIONTRANSPORTE>
    <FECHAEXPEDICIONMANIFIESTO>31/03/2026</FECHAEXPEDICIONMANIFIESTO>
    <CODMUNICIPIOORIGENMANIFIESTO>13001000</CODMUNICIPIOORIGENMANIFIESTO>
    <CODMUNICIPIODESTINOMANIFIESTO>68307000</CODMUNICIPIODESTINOMANIFIESTO>
    <CODIDTITULARMANIFIESTO>C</CODIDTITULARMANIFIESTO>
    <NUMIDTITULARMANIFIESTO>xxxxxx</NUMIDTITULARMANIFIESTO>
    <NUMPLACA>xxxx</NUMPLACA>
    <NUMPLACAREMOLQUE>xxxxx</NUMPLACAREMOLQUE>
    <CODIDCONDUCTOR>C</CODIDCONDUCTOR>
    <NUMIDCONDUCTOR>xxxxx</NUMIDCONDUCTOR>
    <VALORFLETEPACTADOVIAJE>999999</VALORFLETEPACTADOVIAJE>
    <CODMUNICIPIOPAGOSALDO>68001000</CODMUNICIPIOPAGOSALDO>
    <CODRESPONSABLEPAGOCARGUE>R</CODRESPONSABLEPAGOCARGUE>
    <CODRESPONSABLEPAGODESCARGUE>D</CODRESPONSABLEPAGODESCARGUE>
    <FECHAPAGOSALDOMANIFIESTO>30/04/2026</FECHAPAGOSALDOMANIFIESTO>
    <OBSERVACIONES>xxxx xxxxx xxxx</OBSERVACIONES>
    <ACEPTACIONELECTRONICA>NO</ACEPTACIONELECTRONICA>
    <RETENCIONFUENTEMANIFIESTO>1</RETENCIONFUENTEMANIFIESTO>
    <RETENCIONICAMANIFIESTOCARGA>9</RETENCIONICAMANIFIESTOCARGA>
    <VALORANTICIPOMANIFIESTO>9999999</VALORANTICIPOMANIFIESTO>
    <RETENCIONFOPAT>5417</RETENCIONFOPAT>
    <REMESASMAN procesoid="43">
      <REMESA>
        <CONSECUTIVOREMESA>xxxxxxx</CONSECUTIVOREMESA>
      </REMESA>
    </REMESASMAN>
  </variables>
</root>
```

### Descripción de variables XML principales

| Variable XML | Descripción |
|-------------|-------------|
| `NUMNITEMPRESATRANSPORTE` | NIT de la empresa de transporte |
| `NUMMANIFIESTOCARGA` | Consecutivo interno del manifiesto (hasta 15 caracteres alfanuméricos) |
| `CODOPERACIONTRANSPORTE` | Tipo de manifiesto: G=General, W=Viaje Vacío, I=Ida y Regreso, M=Multiparada, U=Urbano, D=Varios Viajes en el Día |
| `FECHAEXPEDICIONMANIFIESTO` | Fecha de expedición en formato DD/MM/AAAA |
| `CODMUNICIPIOORIGENMANIFIESTO` | Código DIVIPOLA del municipio origen (8 dígitos) |
| `CODMUNICIPIODESTINOMANIFIESTO` | Código DIVIPOLA del municipio destino (8 dígitos) |
| `CODIDTITULARMANIFIESTO` | Tipo de identificación del titular (ej. C=Cédula) |
| `NUMIDTITULARMANIFIESTO` | Número de identificación del titular |
| `NUMPLACA` | Placa del vehículo automotor |
| `NUMPLACAREMOLQUE` | Placa del remolque o semirremolque (si aplica) |
| `CODIDCONDUCTOR` | Tipo de identificación del conductor (ej. C=Cédula) |
| `NUMIDCONDUCTOR` | Número de identificación del conductor |
| `VALORFLETEPACTADOVIAJE` | Valor a pagar por el viaje (en pesos colombianos) |
| `CODMUNICIPIOPAGOSALDO` | Código DIVIPOLA del municipio de pago del saldo |
| `CODRESPONSABLEPAGOCARGUE` | Responsable del pago en cargue: R=Remitente, D=Destinatario |
| `CODRESPONSABLEPAGODESCARGUE` | Responsable del pago en descargue: R=Remitente, D=Destinatario |
| `FECHAPAGOSALDOMANIFIESTO` | Fecha pactada de pago del saldo en formato DD/MM/AAAA |
| `OBSERVACIONES` | Texto libre de observaciones (máx. 500 caracteres) |
| `ACEPTACIONELECTRONICA` | SI / NO — indica si la firma de aceptación es electrónica |
| `RETENCIONFUENTEMANIFIESTO` | Valor de retención en la fuente (en pesos) |
| `RETENCIONICAMANIFIESTOCARGA` | Factor de retención de ICA (base por mil) |
| `VALORANTICIPOMANIFIESTO` | Valor del anticipo entregado antes del viaje (en pesos) |
| `RETENCIONFOPAT` | Valor de retención FOPAT = 0.1% del valor a pagar (en pesos, sin decimales) |
| `CONSECUTIVOREMESA` | Consecutivo interno de la remesa a adjuntar al manifiesto |
