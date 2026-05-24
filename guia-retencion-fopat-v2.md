---
title: "Guía de Retención FOPAT"
source: "Guia_de_Liquidacion_Retención_FOPAT_V2_compressed.pdf"
date_converted: "2026-05-24"
total_sections: 9
issuer: "Ministerio de Transporte - Colombia"
version: "02"
date_approved: "2026-04-20"
---

<!-- METADATOS DEL DOCUMENTO -->
<!-- Encabezado recurrente: Ministerio de Transporte / Guía Retención FOPAT -->
<!-- Pie de página recurrente: "Guía Retención FOPAT" con número de página -->

# Guía de Retención FOPAT

**Descripción:** Actividades para realizar el registro de la retención FOPAT en el Manifiesto Electrónico de Carga y el Cumplido del Manifiesto.

---

## Control de Cambios

| Campo | Detalle |
|---|---|
| Versión | 2 |
| Elaborado por | Edna Lorena Gutiérrez, Camilo Sarmiento |
| Revisado por | Jairo Vesga |
| Aprobado por | Juan Felipe Sanabria Saetta |

| Fecha | Modificación |
|---|---|
| 31/03/2026 | Versión Inicial |
| 20/04/2026 | Funcionalidad consulta retenciones FOPAT |

---

## Tabla de Contenido

- [Introducción](#introducción)
- [1. Retención 0.1% para el Fondo para la Promoción de Ascenso Tecnológico (FOPAT)](#1-retención-01-para-el-fondo-para-la-promoción-de-ascenso-tecnológico-fopat)
- [2. Ingreso al Sistema RNDC](#2-ingreso-al-sistema-rndc)
- [3. Módulo Manifiesto Electrónico de Carga](#3-módulo-manifiesto-electrónico-de-carga)
- [4. Expedir Manifiesto](#4-expedir-manifiesto)
- [5. Valor del Viaje](#5-valor-del-viaje)
- [6. Cumplido del Manifiesto](#6-cumplido-del-manifiesto)
  - [6.1 Valores Pactados del Viaje](#61-valores-pactados-del-viaje)
  - [6.2 Valores Finales del Viaje](#62-valores-finales-del-viaje)
- [7. Cálculo del Valor Total FOPAT Mensual](#7-cálculo-del-valor-total-fopat-mensual)
- [8. Consulta Retenciones FOPAT](#8-consulta-retenciones-fopat)
- [9. Modelo XML](#9-modelo-xml)

---

## Introducción

Este documento permitirá conocer el proceso para hacer el registro del valor de retención 0.1% FOPAT en el manifiesto electrónico de carga y en el cumplido del manifiesto en el sistema Registro Nacional de Despachos de Carga - RNDC.

---

## 1. Retención 0.1% para el Fondo para la Promoción de Ascenso Tecnológico (FOPAT)

La Resolución No. 0000008 del 25 de marzo de 2026, expedida por la DIAN, indica lo siguiente:

> *"Que el inciso primero del artículo 21 de la Ley 2251 de 2022 adicionó las fuentes de financiación del Fondo Nacional de Modernización del Parque Automotor de Carga y dispuso que dicho Fondo se financiará, entre otras fuentes, con un porcentaje del valor de las operaciones de transporte terrestre de carga prestadas como servicio público intermunicipal o nacional, realizadas en vehículos con un peso bruto vehicular superior a diez puntos cinco (10.5) toneladas.*
>
> *Que el inciso segundo del artículo 21 de la Ley 2251 de 2022 estableció que la tarifa aplicable a las operaciones de transporte terrestre de carga no podrá ser superior al cero punto uno por ciento (0.1%), calculada sobre el valor a pagar determinado en el respectivo manifiesto de carga.*
>
> *Que el inciso tercero del mismo artículo 21 de la Ley 2151 de 2022 señaló a las empresas transportadoras como agentes de retención de la tarifa del cero punto uno por ciento (0,1%) y desplegó el recaudo en la Unidad Administrativa Especial Dirección de Impuestos y Aduanas Nacionales — DIAN, así como la periodicidad de su traslado por parte de las empresas de transporte.*
>
> *Que el FOPAT es un patrimonio autónomo constituido mediante contrato de fiducia entre el Ministerio de Transporte y la fiduciaria que se seleccione; su contratación y administración se rigen por derecho privado o reglas de organismos multilaterales, con observancia de los principios de la función administrativa (D. 1266 de 2024, art. 2.2.9.2.1).*
>
> *Que el FOPAT opera a través de cuatro subcuentas: (i) movilidad de bajas o cero emisiones para STPP cofinanciados; (ii) modernización de carga liviana y volquetas; (iii) modernización de carga pesada; y (iv) modernización del taxi (arts. 2.2.8.2.3 y 2.2.9.3.1, D. 1266/2024). Los recursos del 0,1% previsto en el art. 21 de la Ley 2251 de 2022, recaudados por la DIAN, se destinan a la subcuenta de Carga Pesada.*
>
> *Que el artículo 24 del Decreto 1017 de 2025 adicionó el artículo 2.2.1.7.7.16 del Decreto 1079 de 2015 - Único Reglamentario del Sector Transporte, y asignó a la Unidad Administrativa Especial Dirección de Impuestos y Aduanas Nacionales – DIAN competencia para reglamentar el procedimiento para el recaudo y la transferencia de los recursos provenientes de la citada tarifa."*

**Enlace Resolución DIAN:** https://www.dian.gov.co/normatividad/Normatividad/Resolución%20000008%20de%2025-03-2026.pdf

### Obligaciones derivadas

De acuerdo con lo anterior, en el Registro Nacional de Despachos de Carga – RNDC, la empresa de transporte debe:

- Registrar en la expedición del manifiesto de carga el valor de retención 0.1% FOPAT.
- Registrar en el cumplido del manifiesto de carga el valor de retención 0.1% FOPAT.
- Realizar la retención y el pago de esta a la DIAN.

Lo anterior **aplica para las operaciones de transporte de carga intermunicipales realizadas con PBV > 10.5 toneladas.**

> **Aclaración:** Esta retención **no aplica** para vehículos con PBV <= 10.5 toneladas y volquetas, ya que hacen parte de la subcuenta (ii) modernización de carga liviana y volquetas.

---

## 2. Ingreso al Sistema RNDC

Las empresas de transporte pueden enviar la información del manifiesto usando:

- **Portal web interactivo del RNDC:** https://rndc2.mintransporte.gov.co/Ingresar/Iniciar-Sesión
- **Webservice del RNDC:** La empresa debe extraer la URL correcta del archivo WSDL disponible en `rndcws.mintransporte.gov.co:8080/ws`. El Ministerio de Transporte puede disponer de otro archivo WSDL para mejorar el tiempo de respuesta, por ejemplo: `rndcws2.mintransporte.gov.co:8080/ws`.

### Credenciales de acceso

- Ingresar el usuario y la contraseña.
- Se puede utilizar el usuario Principal (no recomendable).
- Se sugiere utilizar los usuarios **TIPO (1) - Dependientes** para el ingreso al sistema.
- Dar clic en **INGRESAR**.

<!-- Imagen: Figura No. 01 - Pantalla de login del portal RNDC con campos de usuario y contraseña, opciones de Mesa de Ayuda (tel. 3240800, lunes a viernes 8AM-5PM) y enlaces auxiliares (restaurar contraseña, solicitar usuario, actualizar eMail). -->

---

## 3. Módulo Manifiesto Electrónico de Carga

En los módulos disponibles del sistema, se debe dar clic en el menú **EXPEDIR** y allí se despliega la opción de **Manifiesto Electrónico de Carga**.

<!-- Imagen: Figura No. 02 - Menú desplegable bajo "EXPEDIR" con opciones: Remesa, Manifiesto, Reimprimir Manifiesto, Reimprimir Remesa, Corregir Remesa, No Expedición Manifiesto en el Mes. Panel lateral con gráfica acumulada anual de viajes 2021–2026. -->

Debe dar clic en la opción **Manifiesto**.

---

## 4. Expedir Manifiesto

Al dar clic en la opción de Manifiesto Electrónico de Carga, el sistema muestra la información que debe diligenciar en cada una de las casillas, de acuerdo con la tipología de las operaciones del transporte.

---

## 5. Valor del Viaje

<!-- Imagen: Figura No. 03 - Formulario "VALOR DEL VIAJE" con campos: Valor a pagar por el Viaje, Valor Trayecto Vacío 1, Valor Trayecto Vacío 2, Retención en la Fuente, Retención ICA (%*mil), Retención FOPAT (0.1%) con nota "Sin Centavos, Ajuste al Peso más cercano", Neto a Pagar, Responsable del Pago en (Cargue / Descargue), Valor Anticipo, Saldo x Pagar, Lugar del Pago, Fecha Pago, Recomendaciones. -->

### Definición de campos del Valor del Viaje

**Valor a pagar:**
Es el valor que se paga por el servicio de transporte de las mercancías al titular del manifiesto. Este valor debe ser mayor o igual al costo mínimo de referencia del SICETAC, excepto cuando la identificación del titular del manifiesto electrónico de carga y la identificación del tenedor del vehículo automotor es igual a la identificación de la empresa de transporte (Transporte en Flota Propia); en este caso el valor de flota propia debe ser 0.

El valor a pagar deberá cumplir lo establecido en la normatividad vigente o aquella que la adicione, modifique o sustituya expedida por el Ministerio de Transporte. Por ende, las Empresas de Transporte únicamente podrán expedir Manifiestos de Carga que registren un valor a pagar igual o superior a los costos eficientes de operación de SICE TAC.

**Retención en la fuente:**
Es el descuento autorizado del valor a pagar del manifiesto electrónico de carga. Es un pago anticipado del impuesto de renta del titular del manifiesto, excepto cuando el titular del manifiesto pertenezca al régimen simple de tributación (en ese caso, el valor sería igual a 0). El sistema tiene un parámetro correspondiente al porcentaje definido por el gobierno para la actividad del transporte de carga y se usa para calcular este valor. Por lo tanto, este dato no es un porcentaje. En caso de que el titular del manifiesto sea de régimen simple de tributación, el sistema asigna automáticamente el valor 0 en la casilla de retención en la fuente.

**Retención de ICA:**
Es el descuento autorizado del valor a pagar del manifiesto electrónico de carga, definido por el municipio del sitio de cargue de cada una de las remesas. Este dato es el factor con base en mil y no el valor resultado del cálculo, con base en el valor a pagar.

- El valor base para aplicar la retención de ICA es el resultado de la resta del valor a pagar menos el valor trayecto vacío 1 y el valor trayecto vacío 2.
- En caso de que el manifiesto tenga varias remesas (Multiparada) y sus municipios de cargue sean diferentes con factores distintos, la empresa de transporte debe realizar el cálculo de la suma en dinero de los valores de retención de ICA y luego compararlo con el valor a pagar para dar como resultado el factor de retención de ICA (Promedio ponderado).

**Neto a Pagar:**
Es el resultado de restar los descuentos autorizados (Retención en la fuente, ICA, FOPAT) al valor a pagar del manifiesto electrónico de carga.

**Valor Anticipo:**
Es el valor entregado por la empresa de transporte al titular del manifiesto o a quien este designe antes de iniciar el viaje. Este valor puede ser cero y máximo el valor neto a pagar.

**Saldo por Pagar:**
Es el resultado de restar el valor anticipo del neto a pagar.

### Retención FOPAT 0.1%

Es el descuento autorizado y obligatorio que debe la Empresa de Transporte calcular y reportar. El RNDC verifica que sea igual al 0.1% del Valor a Pagar del Manifiesto Electrónico de Carga. **El valor no debe tener decimales; por lo tanto, debe ser ajustado al peso más cercano.**

Este valor corresponde al aporte de los recursos para la financiación de la Subcuenta de Modernización de Transporte de Carga Pesada del Fondo para la Promoción de Ascenso Tecnológico – FOPAT, de conformidad con lo señalado en el artículo 2.2.1.7.7.16 del Decreto 1079 de 2015.

**Aplica únicamente para vehículos con peso bruto vehicular mayor a 10.5 toneladas**, según la Ley 2251 de 2022, Artículo 21.

#### Pasos para hacer la liquidación

1. **Identifica la base:** Tome el total del Valor a Pagar por el Viaje registrado en el Manifiesto.
2. **Cálculo:** Multiplique el valor a pagar por **0.001** (equivalente al 0.1%).
   - *Ejemplo:* Si el valor a pagar es de $1,000,000, el FOPAT será de **$1,000**.
3. **Registro en RNDC:** En la sección "Valor FOPAT (0.1%)" del sistema, ingrese el monto calculado. El valor no debe tener decimales; debe ser ajustado al peso más cercano.
4. Esto debe quedar reflejado en el documento físico (PDF) del manifiesto para que el conductor tenga claridad sobre el descuento.

### Obligatoriedad del campo FOPAT en el RNDC

De acuerdo con la Resolución 20223040045515 de 2022, numeral 5.2.4 (Registro obligatorio manifiesto electrónico de carga), el valor a pagar del Manifiesto debe ser mayor a 0, excepto cuando la identificación del titular del manifiesto electrónico de carga y la identificación del tenedor del vehículo automotor es igual a la identificación de la empresa de transporte (Transporte en Flota Propia).

- Cuando el valor a pagar es igual a 0: `Valor a pagar × retención FOPAT 0.1% = 0`

El RNDC solicitará de manera obligatoria el campo **"Valor FOPAT (0.1%)"** para las operaciones de transporte de carga intermunicipales realizadas con vehículos de clase:

- Tractocamión
- Camión (3 y 4 ejes)
- Camión de dos ejes con PBV > 10.5 toneladas

> **Aclaración:** Esta retención **no aplica** para Camionetas, Camiones de dos ejes con PBV <= 10.5 toneladas y volquetas, ya que hacen parte de la subcuenta (ii) modernización de carga liviana y volquetas.

---

## 6. Cumplido del Manifiesto

<!-- Imagen: Figura No. 04 - Menú desplegable bajo "CUMPLIR" con opciones: Monitoreo Manifiesto, Cumplir Remesa, Cumplir Manifiesto (resaltado), Reimprimir Cumplido Remesa, Reimprimir Cumplido Manifiesto, Facturación Electrónica, Cumplir Registro Municipal. -->

### 6.1 Valores Pactados del Viaje

<!-- Imagen: Figura No. 05 - Formulario "VALORES PACTADOS DEL VIAJE" con campos: Nro de Viajes del Día, Valor Manifiesto, Valor Adicional x Tiempos de Cargue, Valor Adicional x Tiempos Descargue, Otros Valores adicionales (con campo Motivo), Descuento por Tiempos Reales (con campo Motivo). Los campos con fondo naranja indican campos ajustables. -->

Si la Empresa de transporte, al momento de cumplir el manifiesto, realizó ajustes en el **VALOR A PAGAR** que inicialmente registró en el manifiesto electrónico de carga, y registró valores en las casillas de **Valores Adicionales** o **Descuentos por Tiempos Reales** y seleccionó el motivo, se debe recalcular el valor a pagar final y las retenciones también se modifican.

### 6.2 Valores Finales del Viaje

<!-- Imagen: Figura No. 06 - Formulario "VALORES FINALES DEL VIAJE" con campos: Valor a Pagar, Valor Retención en la Fuente, Valor Retención ICA, Valor Retención FOPAT (0.1%) con nota "Sin Centavos, Ajuste al Peso más cercano" (campo resaltado en naranja), Neto a Pagar, Valor Anticipo, Valor SobreAnticipos, Saldo a Pagar. -->

#### Procedimiento al realizar el Cumplido del Manifiesto

1. **Verificación:** Antes de cerrar el cumplido en la plataforma RNDC, se debe revisar que no existan variaciones en el valor final pagado (por ejemplo, por valores adicionales o descuentos).
2. **Ajuste (si aplica):** Si el valor final del viaje cambió, recalcule el 0.1% sobre el nuevo valor final del viaje.
3. **Cálculo:** Multiplique el valor a pagar final del viaje por **0.001** (equivalente al 0.1%).
   - *Ejemplo:* Si el valor a pagar final es de $1,500,000, el FOPAT será de **$1,500**.
4. **Cierre:** Asegúrese de que el valor descontado por FOPAT coincida con lo reportado en VALORES FINALES DE VIAJE para evitar inconsistencias en el reporte al Sistema Registro Nacional de Carga.

**Registro en RNDC:** En la sección de los valores finales del viaje **"Valor Final FOPAT (0.1%)"** del sistema, ingrese el monto recalculado FOPAT. El valor no debe tener decimales; por lo tanto, debe ser ajustado al peso más cercano.

- Esto debe quedar reflejado en el documento físico (PDF) del cumplido del manifiesto para que el titular del manifiesto tenga claridad sobre el descuento.

#### Obligatoriedad del campo FOPAT en el Cumplido

El RNDC solicitará de manera obligatoria el campo **"Valor FOPAT (0.1%)"** para las operaciones de transporte de carga intermunicipales realizadas con vehículos de clase:

- Tractocamión
- Camión (3 y 4 ejes)
- Camión de dos ejes con PBV > 10.5 toneladas

Cuando el valor a pagar es igual a 0: `Valor a pagar × retención FOPAT 0.1% = 0`

> **Aclaración:** Esta retención **no aplica** para Camionetas, Camiones de dos ejes con PBV <= 10.5 toneladas y volquetas, ya que hacen parte de la subcuenta (ii) modernización de carga liviana y volquetas.

---

## 7. Cálculo del Valor Total FOPAT Mensual

### Causación de la retención

De acuerdo con el Artículo 1.8.2.5.6 de la Resolución No. 008 de 2026 - DIAN:

> *"Causación. La retención se causará en la fecha en que se realice la aceptación del cumplido de manifiesto electrónico de carga en el sistema Registro Nacional de Despachos de Carga - RNDC, donde se confirma el Valor a Pagar de cada operación de transporte que hace parte del flete, de conformidad con lo establecido en la Ley 2251 de 2022, sin perjuicio del registro contable y electrónico desde la expedición del manifiesto electrónico de carga."*

El RNDC registrará el valor de la retención de cada operación en la fecha en que el titular del manifiesto acepte el cumplido del manifiesto o cuando se dé la aceptación automática del cumplido.

### Reglas por período

**Primer mes de aplicación (abril 2026) — recaudo en mayo 2026:**

- La retención del 0.1% se aplica a operaciones con **aceptación de cumplido de manifiesto con fecha en abril**.
- Se debe validar que la **fecha de expedición del manifiesto sea igual o posterior al 01 de abril de 2026**.
- No se tendrán en cuenta manifiestos expedidos en marzo que sean cumplidos y aceptados en abril, ya que en el manifiesto se pactan las condiciones de la operación y no se puede aplicar la retención a operaciones donde esta no fue pactada inicialmente. La norma no es retroactiva.

**Meses siguientes:**

- La retención se calculará sobre la aceptación de cumplido de manifiesto realizada dentro de cada mes.
- Se registrará como un **número positivo**.
- Cuando se den **anulaciones de cumplido de manifiesto**, el valor calculado de retención se registrará como un **número negativo** y se incluirá en el cálculo del mes correspondiente según la fecha de anulación.

### Ejemplo de liquidación mensual

La empresa de transporte registró 2 cumplidos de manifiestos en el mes de abril:

| Manifiesto | Valor a Pagar Final (Cumplido) | Retención FOPAT |
|---|---|---|
| 00001 | $3,000,000 | $3,000 |
| 00002 | $2,000,000 | $2,000 |

**Escenario A:** Si la empresa anula el manifiesto No. 0002 (retención FOPAT de $2,000) **en el mes de abril**:
- Pago de retenciones del mes de abril = **$3,000**

**Escenario B:** Si la empresa anula el manifiesto No. 0002 (retención FOPAT de $2,000) **en el mes de mayo**:
- Pago de retenciones del mes de abril = **$5,000**
- La retención de $2,000 se debe descontar en el cálculo de las retenciones causadas en el mes de mayo.

---

## 8. Consulta Retenciones FOPAT

El RNDC dispone para cada empresa de transporte una consulta que permite conocer el valor a consignar total, calculado a partir de:

- Las aceptaciones de cumplido de manifiesto del mes.
- Las anulaciones del cumplido de manifiesto del mes.

Este reporte se actualiza diariamente, permitiendo conocer el valor de la retención total a la fecha en que se realiza la consulta.

### Cómo acceder a la consulta

1. Ingresar al sistema RNDC 2: https://rndc2.mintransporte.gov.co/Ingresar/Iniciar-Sesión
2. Digitar usuario y contraseña.
3. Seleccionar la opción **CONSULTAS → INFORMACIÓN EMPRESA TRANSPORTADORA**.

<!-- Imagen: Figura - Menú desplegable "CONSULTAS" con opciones: Consultas a Documentos, SiceTac Remesa, Consultar Documentos Pendientes de Cumplir, Consultar Maestros, Información de Control de RNDC, Consultar Cubos de Información, Registros de Otras Entidades, Información Empresa Transportadora (resaltado). -->

Después de ingresar a la opción Información Empresa Transportadora, se puede visualizar el informe de las retenciones realizadas al manifiesto electrónico de carga en la última sección de la página.

> **IMPORTANCIA DE CONSULTAR:** Este botón recalcula las retenciones del mes en curso reportadas en los Cumplidos de Manifiesto y luego muestra los datos en la parte de abajo. Con lo anterior, cualquier empresa puede mantener esa información de FOPAT en línea.

### Interfaz de consulta

<!-- Imagen: Figura - Panel de consulta "CONSULTAR" con campos: Fecha Inicial Análisis (ej. 202601) y Fecha Final (ej. 202604), botón CONSULTAR. Panel inferior "FOPAT" con tabla de liquidación por mes (202601, 202602, 202603, 202604) mostrando: + Valor Retenciones, - Valor Retenciones Anuladas, Total Retenciones Causadas, + Saldo a Pagar Mes Anterior, - Consignaciones DIAN en el Mes, Total a pagar siguiente mes. Botón "CONSULTAR DETALLE RETENCIONES FOPAT". -->

### Descripción de los campos del panel FOPAT

| Campo | Descripción |
|---|---|
| **Valor Retenciones** | Valor de las retenciones realizadas en los cumplidos de manifiesto aceptados en el mes. |
| **Valor Retenciones Anuladas** | Valor de las retenciones de los cumplidos de manifiestos anulados en el mes. |
| **Total Retenciones Causadas** | Resultado de: Valor Retenciones − Valor Retenciones Anuladas. Muestra el total de retenciones causadas en el mes. |
| **Saldo al Mes Anterior** | Valor pendiente por pagar a la DIAN de la retención FOPAT en el mes anterior. |
| **Consignaciones DIAN en el Mes** | Valor consignado a la DIAN dentro de los primeros 10 días hábiles del mes. (Se actualiza una vez el RNDC reciba el reporte de la DIAN de los valores recaudados en el mes.) |
| **Total a Pagar Siguiente Mes** | Resultado de: Total Retenciones Causadas + Saldo Mes Anterior − Consignaciones DIAN en el Mes. |

### Ejemplo de liquidación FOPAT (tabla completa)

| Concepto | ABRIL | MAYO | JUNIO | JULIO | AGOSTO |
|---|---|---|---|---|---|
| + VALOR RETENCIONES | 1,000 | 800 | 700 | 1,000 | 0 |
| - VALOR RETENCIONES ANULADAS | 20 | 300 | 90 | 20 | 0 |
| **TOTAL RETENCIONES CAUSADAS** | **980** | **500** | **610** | **980** | **0** |
| + SALDO A PAGAR MES ANTERIOR | 0 | 980 | 500 | 610 | 1,040 |
| - CONSIGNACIONES DIAN EN EL MES | 0 | 980 | 500 | 550 | 1,040 |
| **TOTAL A PAGAR SIGUIENTE MES** | **980** | **500** | **610** | **1,040** | **0** |

### Detalle de retenciones FOPAT (archivo Excel)

Al dar clic en **CONSULTAR DETALLE RETENCIONES FOPAT**, el sistema permite descargar un archivo Excel con los siguientes campos:

- Fecha Ingreso
- Año y Mes
- Número de Radicado
- Estado
- Tipo (`CMA` - Cumplido Manifiesto / `ANC` - Anulación Cumplido Manifiesto)
- Valor a Pagar
- Valor Retención FOPAT
- Consecutivo Manifiesto
- Identificación del Titular
- Placa

<!-- Tabla compleja: convertida a lista -->
<!-- Imagen: Figura No. 13 - Captura del modelo de archivo Excel descargado del RNDC, con columnas: Fecha Ingreso Cumplido, AñoMes, Nro. Radicado, Estado, Tipo, Valor a Pagar Cumplido, Valor Retención FOPAT, Consecutivo Manifiesto, Núm. Id. Titular, Placa. Muestra filas de ejemplo con valores de cumplidos (CMA) y anulaciones (ANC). -->

### Regla de causación por fecha de aceptación

De acuerdo con el Artículo 1.8.2.5.6 de la Resolución No. 008 de 2026 - DIAN, las retenciones realizadas de los cumplidos de manifiesto son causadas en la **fecha de aceptación del cumplido por parte del titular del manifiesto**.

*Ejemplo:* Si un cumplido de manifiesto se registró por la empresa de transporte el día **30 de abril** y la aceptación por parte del titular del manifiesto se realizó el día **1 de mayo**, el valor de la retención es causado en el **mes de mayo** y será registrado por el RNDC en el mes de mayo.

---

## 9. Modelo XML

Las empresas de transporte que realicen el registro de las operaciones al RNDC a través de webservice deben incluir la etiqueta `<RETENCIONFOPAT>` en el XML del registro de:

- Expedición de manifiesto de carga.
- Cumplido de manifiesto de carga.

### Ejemplo de manifiesto con FOPAT en XML

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
