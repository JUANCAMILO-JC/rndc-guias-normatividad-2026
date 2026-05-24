---
title: "Guía Registro Remesa - Sistema RNDC"
source: "Guía_Registro_Remesa_Revisión_01_12_25_GAADS_V4_compressed.pdf"
date_converted: "2026-05-24"
version: "4"
total_sections: 7
elaborado_por: "Edna Lorena Gutiérrez"
revisado_por: "Jairo Vesga"
aprobado_por: "Juan Felipe Sanabria Saetta / Alexandra Hernández"
grupo: "Grupo de Logística"
---

## Control de Cambios

| Fecha | Modificación |
|---|---|
| 31/10/2024 | Borrador |
| 09/02/2025 | Revisión Final |
| 27/02/2025 | XML - web |
| 08/04/2025 | Codificación de Subpartida y Código Arancel |
| 12/06/2025 | XML de Residuos Peligrosos |
| 22/07/2025 | Nueva tipología de embalajes o envases |

---

## Tabla de Contenido

- [Introducción](#introducción)
- [1. Remesa](#1-remesa)
- [2. Ingreso al Sistema RNDC](#2-ingreso-al-sistema-rndc)
- [3. Módulo de Remesa](#3-módulo-de-remesa)
- [4. Expedir Remesa](#4-expedir-remesa)
  - [4.1 Contratante de la Remesa](#41-contratante-de-la-remesa)
  - [4.2 Datos Generales de la Remesa](#42-datos-generales-de-la-remesa)
  - [4.3 Punto de Cargue y Descargue](#43-punto-de-cargue-y-descargue)
  - [4.4 Producto – Mercancía](#44-producto--mercancía)
  - [4.5 Empaques y Cantidades del Producto](#45-empaques-y-cantidades-del-producto)
  - [4.6 Operaciones de Trasbordo](#46-operaciones-de-trasbordo)
  - [4.7 Observaciones](#47-observaciones)
  - [4.8 Guardar Remesa](#48-guardar-remesa)
- [5. Web Service](#5-web-service)
- [6. Residuos Peligrosos](#6-residuos-peligrosos)
- [7. Diccionario de Errores](#7-diccionario-de-errores)

---

## Introducción

Este documento permitirá conocer el proceso a seguir para el reporte o registro de la remesa en el sistema Registro Nacional de Despachos de Carga - RNDC.

---

## 1. Remesa

**Registro de Remesa:** Es el registro obligatorio de la información que permite a la empresa de transporte generar el documento remesa, y en donde se especifica quién es el contratante o generador de carga, lugar de cargue, lugar del descargue y todos los datos referentes a la mercancía a transportar, así como los pactos de los tiempos logísticos y las citas para el cargue y descargue.

Esos pactos sirven a la empresa de transporte y al transportador para hacer la planeación del viaje y contar con ellos en los valores pactados por el servicio en el manifiesto de carga o en el registro viaje municipal.

---

## 2. Ingreso al Sistema RNDC

Las empresas de transporte pueden enviar la información de la remesa usando el portal web interactivo del RNDC o usando el webservice del RNDC.

### Acceso por Portal Web

Si usa el portal web interactivo, la empresa de transporte puede hacer el registro de la remesa ingresando al portal del RNDC con el siguiente enlace:

```
https://rndc2.mintransporte.gov.co/Ingresar/Iniciar-Sesi%C3%B3n
```

Debe ingresar el usuario y la contraseña. Se puede utilizar el usuario Principal o los usuarios dependientes para el ingreso al sistema y dar clic en **INGRESAR**.

### Acceso por Web Service

Las empresas que usen el webservice deben accesar el archivo WSDL en:

```
rndcws.mintransporte.gov.co:8080/ws
```

o

```
rndcws2.mintransporte.gov.co:8080/ws
```

**Mesa de Ayuda:**
- Teléfono: 3240800
- Horario: Lunes a viernes 8 AM – 5 PM
- Correo: servicioalciudadano@mintransporte.gov.co
- Entidad: Ministerio de Transporte

---

## 3. Módulo de Remesa

En los módulos disponibles del sistema debe dar clic en el módulo de **EXPEDIR** y allí le despliega la opción de **Remesa** y **Manifiesto Electrónico de Carga**.

Debe dar clic en la opción **REMESA**.

---

## 4. Expedir Remesa

Al dar clic en la opción de remesa el sistema muestra la información que debe diligenciar en cada una de las casillas. De acuerdo con la tipología de las mercancías, le despliega más opciones según corresponda.

---

### 4.1 Contratante de la Remesa

En la parte superior se puede visualizar el nombre de la **Empresa de Transporte** con su respectivo NIT. El usuario debe revisar que los datos coincidan con los de la empresa.

En la segunda parte se debe digitar la información del **Contratante** o **Generador de Carga** o cliente de la empresa de transporte cuando expida la factura electrónica.

#### Tipo de Identificación del Contratante

El primer paso es escoger el **TIPO DE IDENTIFICACIÓN** del Propietario de la Carga / Generador de Carga / Contratante y seleccionar una de las opciones según esté creado en el sistema como tercero.

Opciones disponibles de Tipo de Identificación:

- Cédula Ciudadanía
- Carné Diplomático
- NIT
- Pasaporte
- Tarjeta Identidad
- Cédula Extranjería
- NUIP
- Identificación Extranjera

> La identificación extranjera permite que las empresas de transporte sean contratadas por Generador extranjero.

Al escoger la opción y digitar el número de la identificación, el sistema de manera automática muestra la información ya registrada. Lo primero que muestra es la lista de **sedes** creadas para el propietario de la carga. El usuario debe escoger una de ellas y así el sistema selecciona el nombre y el municipio.

Es la identificación del contratante a quien la empresa de transporte debe reportar como cliente en la factura electrónica que envía a la DIAN y luego al RNDC.

#### Orden de Servicio Expedida por el Generador

En esta casilla la Empresa de Transporte podrá escribir el número de la Orden de Servicio (Orden de Compra, Orden de Pedido), con el fin de poder integrar los sistemas del generador con los sistemas de información de la Empresa de Transporte.

En caso de que en la remesa se digite, en la factura también deberá colocarse el dato de la Orden de Servicio de acuerdo con lo definido por la DIAN.

---

### 4.2 Datos Generales de la Remesa

Una remesa de carga puede ser creada a partir del:

- **Registro de Información de Carga:** Si con anterioridad se ha registrado la información de carga por parte de empresas de transporte o por parte del Generador de Carga, se puede reportar este consecutivo y el sistema hará una ligación entre ese consecutivo de la información de carga y la nueva remesa. El sistema valida que ese consecutivo esté registrado por el respectivo Generador o por la misma Empresa de Transporte.

- **Registro de Remesa previamente creado (Consecutivo de Remesa a Copiar):** Si desea copiar la información de una remesa anterior puede hacerlo, llamando con el número consecutivo de la remesa de la cual va a tomar la información. El sistema muestra esta información para que la modifique según sea la necesidad.

La Empresa de transporte debe diligenciar el **Número del Consecutivo de remesa**, compuesto por números y letras, con hasta 15 caracteres. El sistema valida que no se repita ese consecutivo dentro de la Empresa de Transporte. Es llamado **consecutivo interno** de la empresa de transporte.

El usuario puede escribir el número de la **Orden de Servicio de Transporte** expedida por el Generador de Carga (también llamado Orden de Compra, Orden de Trabajo, etc.), cuya finalidad es formalizar un contrato entre el Generador y la Empresa de Transporte.

#### Tipo de Operación

El usuario debe escoger o seleccionar el tipo de Operación a ejecutar con la remesa de las siguientes opciones:

| Tipo de Operación | Descripción |
|---|---|
| **General** | Aplica a aquella remesa que no corresponda a contenedores ni mercancía consolidada. |
| **Mercancía Consolidada** | Consolidación en una sola remesa de varios paquetes pequeños de diferentes Generadores de carga o de un solo Generador, donde la operación corresponde a distribución en varias direcciones de un mismo municipio o recogida de paquetes en varias direcciones hacia una sola dirección de destino. |
| **Contenedor Cargado** | Remesas en las cuales el embalaje/envase externo es un contenedor de 20, 40 o 45 pies (o cualquier otro tamaño con tipología de Contenedor). |
| **Contenedor Vacío** | Remesas que transportan el embalaje/envase del tipo Contenedor, sin carga en su interior. |

> **Mercancía Consolidada – regla de contratante:** Si los paquetes son de varios generadores, el contratante o cliente debe ser la misma identificación de la Empresa de Transporte. Si los paquetes son del mismo generador, la identificación del contratante es la de ese Generador.

#### Tipo de Empaque

La lista de valores del **Tipo de Empaque** varía dependiendo del tipo de Operación seleccionado:

**Operación General:**

| Tipo de Empaque |
|---|
| General Fraccionada (Bulto, Caja, Saco, Paca, Pieza) |
| Granel Líquido |
| Granel Sólido |
| Unidad sin Empaque |

> Ejemplo de Unidad sin empaque: transporte de automóviles en un vehículo con remolque de cama baja o en una niñera.

**Operación Mercancía Consolidada:**

| Tipo de Empaque |
|---|
| Paquetes General Fraccionada en máximo 2 Kgs por unidad de empaque |
| Varios |

**Operación Contenedor Cargado o Contenedor Vacío:**

| Tipo de Empaque |
|---|
| Un contenedor de 20 pies |
| Dos contenedores de 20 pies |
| Un contenedor de 40 pies |
| Un contenedor de 45 pies |

---

### 4.3 Punto de Cargue y Descargue

En esta sección de la remesa, el usuario debe diligenciar la información de dos terceros:

- Uno para el **SITIO DE CARGUE**
- Otro para el **SITIO DE DESCARGUE**

Estos terceros deben estar creados previamente en el **maestro de terceros** en el sistema RNDC.

Para cada uno se debe digitar:

1. **Tipo de Identificación** (mismas opciones que el contratante)
2. **Número de Identificación**
3. **Sede** del tercero (seleccionable en lista desplegable)
4. **Código de Sede** (alternativa a la lista desplegable)

El sistema muestra automáticamente la información extraída del maestro de terceros: Nombre, dirección, municipio y coordenadas geo-referenciadas.

**Reglas de validación geográfica:**

- El municipio del SITIO DE CARGUE **puede ser igual** al municipio del SITIO DE DESCARGUE.
- La dirección del SITIO DE CARGUE **debe ser distinta** a la dirección del SITIO DE DESCARGUE.

#### Coordenadas Georeferenciadas

La codificación geográfica (geo-codificación) asigna coordenadas de Latitud-Longitud a las direcciones o puntos geográficos de interés.

- **Latitud:** número entre `-5.000000` y `14.000000`, con mínimo 6 decimales.
- **Longitud:** número entre `-79.000000` y `-66.000000`, con mínimo 6 decimales.
- Si alguno de los dos datos no está en ese rango, posiblemente es una ubicación por fuera de los límites de Colombia.

#### Fecha Cita Cargue

El Generador de carga debe entregar a la empresa de transporte la fecha y hora en que será atendido el vehículo en el punto de cargue. La empresa de transporte debe registrar esa fecha y hora de cita para que el conductor llegue puntual.

- **Fecha:** formato `dd/mm/aaaa`
- **Hora:** formato militar, desde `00:00` hasta `23:59`
- **Tiempo de Cargue:** horas y minutos (números enteros, sin decimales)

#### Fecha Cita Descargue

Para el sitio de Descargue se aplican los mismos datos que para el sitio de Cargue (fecha, hora y tiempo de descargue).

---

### 4.4 Producto – Mercancía

El usuario debe registrar la información de **PRODUCTO – MERCANCÍA**. Dependiendo de la opción que escoja en **NATURALEZA DE LA CARGA**, se activarán o desactivarán casillas. Se puede navegar entre casillas obligatorias con la tecla **TABULAR**.

#### Naturaleza de la Carga

Al escoger la Naturaleza de la Carga el sistema oculta los campos que no aplican para esa naturaleza. Las opciones disponibles son:

- Carga General (Carga Normal)
- Mercancía Peligrosa
- Carga Extradimensionada
- Carga Extrapesada
- Mercancía Peligrosa: Residuos Peligrosos
- Semovientes
- Refrigerada

#### Codificación Armonizada de Productos (Posiciones Arancelarias)

El **Código del Producto** es un dato obligatorio para todas las naturalezas. Se valida contra el **Maestro de la Codificación Armonizada de Productos** (también llamado Posiciones arancelarias).

En la codificación armonizada existen **4 conceptos** aplicables en el RNDC, cada uno representado por un código de **2 dígitos**:

| Nivel | Concepto | Dígitos acumulados |
|---|---|---|
| 1 | Capítulo | 2 |
| 2 | Partida | 4 (Capítulo + Partida) |
| 3 | Subpartida | 6 |
| 4 | Código Arancel | 8 |

**Reglas de obligatoriedad:**

- En el RNDC, el código del producto debe tener los primeros **4 dígitos** (Capítulo y Partida) de forma obligatoria.
- Los otros **4 dígitos** (Subpartida y Código Arancel) son obligatorios solo para ciertos casos de mercancías donde se necesite mayor precisión (ej. Mercancías Peligrosas).
- El dato de Código de Producto debe tener un `"00"` a la izquierda (el RNDC los incluye automáticamente si no se reportan).

**Maestros consultables en el RNDC:**

- Capítulos Codificación de Productos
- Codificación de Productos (Partidas)
- Subpartidas Productos
- Códigos de Arancel

**Ejemplos de codificación:**

- **Solo 4 dígitos** (Capítulo y Partida): `000201` → Carne de animales de la especie bovina; fresca o refrigerada.
- **6 dígitos** (Capítulo, Partida y Subpartida): `002710` + Subpartida `20`.
- **8 dígitos** (Capítulo, Partida, Subpartida y Código Arancel): `002710` + Subpartida `12` + Código Arancel `11`.

> Ejemplo práctico: Para transportar Gasolina para motores de aviación, se reporta: Código Producto `002710`, Subpartida `12`, Código Arancel `19`. El RNDC exige los tres datos.

#### Carga General (Carga Normal)

Es todo tipo de carga diferente a Mercancías Peligrosas / Residuos Peligrosos, Carga Extradimensionada / Extrapesada, Refrigerada y Semovientes.

**Campos obligatorios para Carga General:**

- Código del Producto (Capítulo y Partida mínimo)
- **Descripción del Producto** (también llamada Descripción Corta del Producto): máximo **60 caracteres**. Se solicita para precisar el producto más allá de la Partida.

> Si el código de la mercancía está clasificado como Mercancía Peligrosa, al seleccionar Carga General el sistema **no mostrará** el campo Código UN, lo cual obliga a seleccionar Mercancía Peligrosa como naturaleza.

#### Mercancía Peligrosa

Para clasificar la Naturaleza de Carga como Mercancía Peligrosa es obligatorio escribir:

1. **Código del Producto** (Codificación Armonizada)
2. **Código UN:** número de cuatro dígitos para identificar las mercancías peligrosas, establecido en las Recomendaciones Relativas al Transporte de Mercancías Peligrosas (Libro Naranja de las Naciones Unidas).

**Definición legal** (Decreto 1079 de 2015, Artículo 2.2.1.7.8.3):

> Materiales perjudiciales que durante la fabricación, manejo, transporte, almacenamiento o uso, pueden generar o desprender polvos, humos, gases, líquidos, vapores o fibras infecciosas, irritantes, inflamables, explosivos, corrosivos, asfixiantes, tóxicos o de otra naturaleza peligrosa, o radiaciones ionizantes en cantidades que puedan afectar la salud de las personas que entran en contacto con éstas, o que causen daño material.

> Hay ciertos productos de mercancías peligrosas prohibidas para el transporte, como el mercurio elemental (UN 2809); en esos casos no se permitirá generar la remesa.

**Grupos de embalaje/envase ONU:**

- **Grupo I:** Sustancias que presentan gran peligro
- **Grupo II:** Sustancias que presentan peligro intermedio
- **Grupo III:** Sustancias que presentan un peligro escaso

> Caso excepcional: Cuando una mercancía peligrosa aparezca en la lista con el número UN repetido (diferenciada por grupo de embalaje), el usuario debe seleccionar obligatoriamente el campo **Grupo Embalaje Envase** correcto (I, II o III).

**Códigos UN con sufijo de letra:** Cuando un producto de Mercancía Peligrosa tiene bajo el mismo código dos o más descripciones, se usa una letra como sufijo empezando en A, B, C…

Ejemplo: `UN 2031A`, `UN 2031B`, `UN 2031C` (Ácido Nítrico con diferentes concentraciones).

**Campo "Designación Mercancía Peligrosa":** Aparece automáticamente con la información de las columnas 1 a 5 de la Lista de Mercancías Peligrosas (Libro Naranja):

```
Formato: UN XXXX, NOMBRE Y DESCRIPCIÓN, Clase, (Peligro secundario), (Peligro terciario), GE [I|II|III]
```

Ejemplos de formato:

- `UN 0174, REMACHES EXPLOSIVOS, 1.4S` — Un solo peligro, no tiene GE.
- `UN 1072, OXÍGENO COMPRIMIDO, 2.2, (5.1)` — Dos peligros, sin Grupo de embalaje/envase.
- `UN 1154, DIETILAMINA, 3, (8), GE II` — Dos peligros, presenta GE.
- `UN 2965, DIMETILETERATO DE TRIFLUORUO DE BORO, 4.3, (3), (8), GE I` — Tres peligros, presenta GE.

**Estado del Producto:** El usuario debe seleccionar uno de los tres estados:

- Líquido
- Sólido o semisólido
- Gaseoso

#### Carga Extradimensionada

Aplica según la **Resolución No. 004959 de 2006** del Ministerio de Transporte.

**Definiciones clave:**

- **Carga Indivisible:** Carga que por sus características no puede ser fraccionada para su transporte.
- **Carga Extradimensionada:** Carga indivisible que excede las dimensiones de la carrocería de los vehículos convencionales homologados por el Ministerio de Transporte para la movilización de carga en tránsito normal por las vías públicas.

Se requiere permiso expedido por el Instituto Nacional de Vías (INVÍAS) para vías nacionales, o por las autoridades de los entes territoriales para vías departamentales, metropolitanas, municipales o distritales.

**Campos obligatorios:** Código del producto y descripción del producto (igual que Carga General).

#### Carga Extrapesada

Aplica según la **Resolución No. 004959 de 2006**.

**Definición:** Carga indivisible que, una vez montada en vehículos convencionales homologados por el Ministerio de Transporte, excede el peso bruto vehicular o los límites de peso por eje autorizados en las normas vigentes para el tránsito normal por las vías públicas.

**Campos obligatorios:** Código del producto y descripción del producto (igual que Carga General).

#### Mercancía Peligrosa – Residuos Peligrosos

Según el Decreto 1079 de 2015, Artículo 2.2.1.7.8.6.5:

> Los desechos que se generen por cualquier proceso productivo, incluyendo los envases y embalajes, adquieren las características de mercancía peligrosa. Por lo tanto, su manejo y transporte se debe realizar cumpliendo los mismos requisitos y obligaciones contemplados en esta Sección de acuerdo con la clasificación dada en el literal F, numeral 3 del artículo 2.2.1.7.8.1.1. del presente decreto.

Según el Decreto 1076 de 2015, Artículo 2.2.6.1.1.3:

> Residuo Peligroso: Es aquel residuo o desecho que por sus características corrosivas, reactivas, explosivas, tóxicas, inflamables, infecciosas o radiactivas, puede causar riesgos, daños o efectos no deseados, directos e indirectos, a la salud humana y el ambiente. Así mismo, se considerará residuo peligroso los empaques, envases y embalajes que estuvieron en contacto con ellos.

**Campos adicionales para Residuos Peligrosos:**

- **Código UN** (Naciones Unidas) — obligatorio
- **Designación Residuo Peligroso** — generada automáticamente por el sistema
- **Descripción detallada del Residuo Peligroso** — texto libre, describe el residuo específico
- **Característica Peligrosidad** — obligatorio; seleccionar una opción:

| Código | Peligrosidad |
|---|---|
| Corrosivo | Corrosivo |
| Reactivo | Reactivo |
| Explosivo | Explosivo |
| Toxico | Toxico |
| Inflamable | Inflamable |
| Infeccioso | Infeccioso |
| Radioactivo | Radioactivo |

- **Nombre Técnico o Grupo Químico del N.E.P.:** Se habilita cuando la designación del residuo peligroso contiene la sigla **N.E.P.** (No Especificado en otra Parte). Se describe el nombre o grupo químico de la sustancia que aporta el peligro.

- **Corrientes de Residuos Peligrosos (Y o A):** Códigos del Convenio de Basilea (Anexo I y Anexo VIII). Se consultan en el Maestro de Codificación de Productos filtrando por tipo **DP**.

  - Corriente **Y**: Anexo I del Convenio de Basilea (ej. Y1, Y2, … Y45)
  - Corriente **A**: Anexo VIII del Convenio de Basilea (ej. A1010, A1020, …)

- **Desagregación:** Subdivisión de la corriente de residuo peligroso (si aplica). Ejemplo: para Y1 las desagregaciones son Y1.1, Y1.2, Y1.3.

#### Semovientes

Las empresas de transporte que transporten semovientes deben cumplir con el **Decreto 1766 de 2016**, Artículo 2.13.5.2.1. Los requisitos para la movilización de ganado en el territorio nacional son:

1. Guía Sanitaria de Movilización Interna (GSMI), expedida por la autoridad competente.
2. Manifiesto de carga expedido por la empresa de transporte público terrestre automotor de carga, legalmente constituida y habilitada.

**Campos obligatorios:** Código del producto y descripción del producto (igual que Carga General).

#### Refrigerada

El transporte refrigerado se refiere al transporte de mercancías perecederas en vehículos equipados con sistemas de refrigeración para mantener una temperatura controlada durante el transporte.

**Campos obligatorios:** Código del producto y descripción del producto (igual que Carga General).

---

### 4.5 Empaques y Cantidades del Producto

**Conceptos clave:**

- **Empaque primario (interno):** Aquel donde el producto tiene contacto directo con el material del envase.
- **Empaque externo (secundario):** Contiene uno o varios envases primarios y proporciona protección adicional durante el transporte, distribución y comercialización.

#### Unidades de Medida

Hay **dos unidades de medida** que deben registrarse:

| Unidad | Descripción | Obligatoriedad |
|---|---|---|
| **Unidad Medida del Transporte** | Solo en Kilogramos. Controla el peso total del vehículo para vigilar carreteras, puentes y otros elementos. | Siempre obligatoria |
| **Unidad Medida del Producto** | Unidad en la cual el Generador define la cantidad real del producto (unidad de medida comercial). | Obligatoria cuando el tipo de empaque es **Granel Líquido**; opcional en otros casos |

Opciones de Unidad Medida del Producto:

- Kilogramo
- Galón
- MetroCubico
- Litro
- Barril
- Unidad

> Ejemplo: Si se transporta un derivado del petróleo en un carrotanque, la Unidad Medida del Transporte registra los kilos y la Unidad Medida del Producto se selecciona en Galón o Barril. Esta condición de las dos unidades de medida es obligatoria cuando el tipo de empaque es Granel Líquido.

#### Empaques Primario y Externo

Ambos son opcionales. Si el usuario conoce el **código** del empaque, no necesita seleccionar el nombre ni el material; el sistema lo muestra al digitar el código.

> Si se transporta granel líquido o granel sólido, **no se deben digitar** los códigos de empaque primario interno y externo.

Ejemplo: Si se transporta un producto líquido en tambores → Unidad de medida del producto en Litros, empaque interno: Tambor, empaque externo: Estiba.

#### Catálogo de Tipos de Embalaje/Envase

El RNDC maneja los siguientes tipos de embalaje/envase según el Libro Naranja de las Naciones Unidas:

---

**E/E Simple**

Los embalajes/envases simples se definen como uno o más recipientes y todos los demás elementos o materiales necesarios para que el o los recipientes puedan desempeñar su función de contención y demás funciones de seguridad.

| Nombre | Definición | Referencia Libro Naranja |
|---|---|---|
| **Bidón** | Embalaje/envase cilíndrico de fondo plano o convexo, hecho de metal, cartón, plástico, madera contrachapada u otro material apropiado. Incluye formas redondas de cuello cónico o en forma de cubo. Los toneles de madera y los jerricanes NO están incluidos. | Vol. 1, Cap. 1.2 Definiciones; Vol. 2, 6.1.2.5 Pág. 216 |
| **Jerricán** | Embalaje/envase de metal o de plástico de sección transversal rectangular o poligonal. | Vol. 1, Cap. 1.2 Definiciones; Vol. 2, 6.1.2.5 Pág. 216 |
| **Caja** | Embalaje/envase de caras compactas rectangulares o poligonales, hecho de metal, madera, madera contrachapada, aglomerado de madera, cartón, plástico u otro material apropiado. Se pueden realizar pequeños orificios para facilitar manipulación o apertura, siempre que no pongan en peligro la integridad durante el transporte. | Vol. 1, Cap. 1.2 Definiciones; Vol. 2, 6.1.2.5 Pág. 216 |
| **Saco** | Embalaje/envase flexible de papel, láminas de plástico, textil, material tejido u otro material apropiado. | Vol. 1, Cap. 1.2 Definiciones; Vol. 2, 6.1.2.5 Pág. 216 |

---

**E/E Compuestos (Interior y Exterior)**

| Tipo | Definición | Referencia Libro Naranja |
|---|---|---|
| **Embalaje/envase compuesto** | Constituido por un embalaje/envase exterior y un recipiente interior unidos de modo que formen un embalaje/envase integral. Una vez montado, se llena, se almacena, se transporta y se vacía como tal. | Vol. 1, Cap. 1.2 Definiciones |
| **Embalaje/envase interior** | Embalaje/envase que ha de estar provisto de un embalaje/envase exterior para el transporte. | Vol. 1, Cap. 1.2 Definiciones |
| **Embalaje/envase exterior** | La protección exterior de un embalaje/envase compuesto o combinado, junto con los materiales absorbentes, los materiales de relleno y cualquier otro elemento necesario para contener y proteger los recipientes interiores. | Vol. 1, Cap. 1.2 Definiciones |

---

**E/E Específicos para Gases**

| Nombre | Definición | Referencia Libro Naranja |
|---|---|---|
| **Botella de gas (Cilindro)** | Recipiente a presión con una capacidad (en agua) no superior a 150 litros. | Vol. 1, Cap. 1.2 Definiciones |
| **Tubo (Gases)** | Recipiente a presión sin soldadura o de construcción compuesta, con una capacidad (en agua) superior a 150 litros y no superior a 3000 litros. | Vol. 1, Cap. 1.2 Definiciones |
| **Bloque de botellas (Gases)** | Recipiente a presión compuesto por un conjunto de botellas o carcasas de botellas unidas e interconectadas por una tubería colectora y transportadas como un conjunto indisociable. Capacidad total no superior a 3000 litros (1000 litros para gases de la división 2.3). | Vol. 1, Cap. 1.2 Definiciones |
| **Contenedor de gas de elementos múltiples (CGEM)** | Montaje multimodal de botellas, tubos o bloques de botellas interconectadas por una tubería colectora y montados en un cuadro. Incluye equipo de servicio y elementos estructurales para el transporte de gases. | Vol. 1, Cap. 1.2 Definiciones |
| **Bidones a presión (Gases)** | Recipiente a presión transportable soldado con capacidad superior a 150 y menor de 1000 litros. Existen también recipientes criogénicos cerrados a presión, térmicamente aislados, de capacidad no superior a 1000 litros. | Vol. 1, Cap. 1.2 Definiciones |

---

**E/E Específicos para Materiales Radiactivos**

| Nombre | Definición | Referencia Libro Naranja |
|---|---|---|
| **Bulto para materiales radiactivos** | El producto final de la operación de embalaje/envasado, constituido por el embalaje/envase y su contenido preparados para el transporte. | Definición, Cap. 1.2 / 1.2.1 Pág. 28; 4.1.9 Pág. 129 |

---

**E/E Recipientes Intermedios para Graneles (RIG)**

| Nombre | Definición | Referencia Libro Naranja |
|---|---|---|
| **RIG (IBC, Big Bag)** | Embalaje/envase portátil, rígido o flexible, metálicos, de plástico rígido o compuestos. Incluye: RIG metálico, RIG flexible, RIG de plástico rígido, RIG compuesto, RIG de cartón y RIG de madera, según las especificaciones de construcción. | Vol. 2, Numeral 6.5.1.3 / Pág. 322 |

---

**E/E Grandes Embalajes y Envases**

| Nombre | Definición | Referencia Libro Naranja |
|---|---|---|
| **Grandes E/E** | Grandes E/E Rígidos: pueden ser en aluminio, acero, metálicos. Grandes E/E Flexibles: plástico, cartón, madera y papel. | Cap. 6.6 Prescripciones relativas a la construcción y el ensayo de grandes embalajes/envases, 6.6.1 Generalidades |

---

**E/E Cisternas Portátiles**

| Nombre | Definición | Referencia Libro Naranja |
|---|---|---|
| **Cisterna Portátil (Isotanque)** | Cisterna portátil multimodal con capacidad no inferior a 450 litros. Comprende un depósito con el equipo de servicio y elementos estructurales para el transporte de sustancias peligrosas (clases 1 y 3 a 9), gases licuados no refrigerados (clase 2) o gases licuados refrigerados. | Vol. 1, Cap. 1.2 Definiciones (Pág. 28) |

---

**E/E Contenedores para Graneles**

| Nombre | Definición | Referencia Libro Naranja |
|---|---|---|
| **Contenedor** | Elemento de transporte de carácter permanente, suficientemente resistente para uso reiterado, especialmente concebido para facilitar el transporte de mercancías sin operaciones intermedias de carga y descarga, aprobado conforme al Convenio Internacional sobre la Seguridad de los Contenedores (CSC) de 1972. No engloba vehículos ni embalajes. Capacidad: contenedor pequeño ≤ 3 m³; contenedor grande > 3 m³. Para graneles, capacidad no inferior a 1,0 m³. | Vol. 1, Cap. 1.2 Definiciones |

---

### 4.6 Operaciones de Trasbordo

En esta sección el usuario puede registrar hasta **dos municipios de trasbordo** cuando la operación de transporte requiera transbordos intermedios:

- Municipio Trasbordo 1
- Municipio Trasbordo 2

---

### 4.7 Observaciones

El usuario puede escribir información aclaratoria o según la necesidad a la remesa que está registrando, en el campo de **Observaciones**.

---

### 4.8 Guardar Remesa

El usuario debe dar clic en la opción de **GUARDAR REMESA** cuando haya terminado de digitar la información requerida en cada uno de los campos. Al dar clic, obtendrá el **número de radicado o autorización** asignada a la remesa registrada por el sistema RNDC.

> **Advertencia:** El presente Registro debe ser llenado sin excepción en su totalidad. La omisión de cualquier información dará lugar a las sanciones previstas en la normatividad correspondiente. La Empresa de Transporte debe detallar, con la precisión requerida, la mercancía que transporta.

---

## 5. Web Service

### Etiquetas XML Generales

La estructura del XML para enviar una remesa por Web Service sigue este esquema base:

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
  <acceso>
    <username>USUARIO1</username>
    <password>PASSWORD1</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>3</procesoid>
  </solicitud>
  <variables>
    <!-- campos de la remesa -->
  </variables>
</root>
```

### Ejemplo: Mercancía Peligrosa Sencilla

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
  <acceso>
    <username>USUARIO1</username>
    <password>PASSWORD1</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>3</procesoid>
  </solicitud>
  <variables>
    <NUMNITEMPRESATRANSPORTE>8999990554</NUMNITEMPRESATRANSPORTE>
    <CONSECUTIVOREMESA>REM54321</CONSECUTIVOREMESA>
    <CODOPERACIONTRANSPORTE>G</CODOPERACIONTRANSPORTE>
    <CODNATURALEZACARGA>2</CODNATURALEZACARGA>
    <MERCANCIAREMESA>002701</MERCANCIAREMESA>
    <!-- DESCRIPCIONCORTAPRODUCTO NO se debe enviar para mercancía peligrosa -->
    <CODIGOUN>0107</CODIGOUN>
    <GRUPOEMBALAJEENVASE>II</GRUPOEMBALAJEENVASE>
    <ESTADOMERCANCIA>L</ESTADOMERCANCIA>
    <UNIDADMEDIDACAPACIDAD>1</UNIDADMEDIDACAPACIDAD>
    <CANTIDADCARGADA>2500</CANTIDADCARGADA>
    <UNIDADMEDIDAPRODUCTO>GLL</UNIDADMEDIDAPRODUCTO>
    <CANTIDADPRODUCTO>800</CANTIDADPRODUCTO>
    <CODTIPOEMPAQUE>0</CODTIPOEMPAQUE>
    <EMPAQUEPRIMARIO>4G</EMPAQUEPRIMARIO>
    <CODTIPOIDREMITENTE>C</CODTIPOIDREMITENTE>
    <NUMIDREMITENTE>19258361</NUMIDREMITENTE>
    <CODSEDEREMITENTE>0</CODSEDEREMITENTE>
    <CODTIPOIDDESTINATARIO>C</CODTIPOIDDESTINATARIO>
    <NUMIDDESTINATARIO>19258361</NUMIDDESTINATARIO>
    <CODSEDEDESTINATARIO>4</CODSEDEDESTINATARIO>
    <HORASPACTOCARGA>4</HORASPACTOCARGA>
    <MINUTOSPACTOCARGA>0</MINUTOSPACTOCARGA>
    <HORASPACTODESCARGUE>4</HORASPACTODESCARGUE>
    <MINUTOSPACTODESCARGUE>0</MINUTOSPACTODESCARGUE>
    <CODTIPOIDPROPIETARIO>N</CODTIPOIDPROPIETARIO>
    <NUMIDPROPIETARIO>9003010078</NUMIDPROPIETARIO>
    <CODSEDEPROPIETARIO>0</CODSEDEPROPIETARIO>
    <ORDENSERVICIOGENERADOR>XXXXX</ORDENSERVICIOGENERADOR>
    <FECHACITAPACTADACARGUE>14/02/2025</FECHACITAPACTADACARGUE>
    <HORACITAPACTADACARGUE>08:00</HORACITAPACTADACARGUE>
    <FECHACITAPACTADADESCARGUE>15/02/2025</FECHACITAPACTADADESCARGUE>
    <HORACITAPACTADADESCARGUEREMESA>09:00</HORACITAPACTADADESCARGUEREMESA>
  </variables>
</root>
```

### Referencia de Valores por Etiqueta

**`<GRUPOEMBALAJEENVASE>`**

| Valor | Descripción |
|---|---|
| `I` | Grupo de embalaje I |
| `II` | Grupo de embalaje II |
| `III` | Grupo de embalaje III |

**`<ESTADOMERCANCIA>`**

| Valor | Descripción |
|---|---|
| `S` | Sólido |
| `L` | Líquido |
| `G` | Gaseoso |

**`<UNIDADMEDIDAPRODUCTO>`**

| Valor | Descripción |
|---|---|
| `KGM` | Kilogramo |
| `GLL` | Galón |
| `MTQ` | MetroCúbico |
| `CMQ` | CentímetroCúbico |
| `LTR` | Litro |
| `MLT` | MiliLitro |
| `BLL` | Barril |
| `UN` | Unidad |

**`<EMPAQUEPRIMARIO>`:** Permite los códigos del Maestro de Empaques publicado en el RNDC que estén permitidos para mercancías peligrosas (ver columna "Mercancía Peligrosa" en el maestro).

**`<ORDENSERVICIOGENERADOR>`:** Opcional. Obligatoria si el Generador la exige para la facturación electrónica. Máximo **20 caracteres**. Este dato se mostrará al generador cuando apruebe la factura.

**`<DESCRIPCIONCORTAPRODUCTO>`:** **NO se debe enviar** para mercancía peligrosa.

### Codificación de Subpartida y Código Arancel en Web Service

Cuando el Código de Capítulo y Partida de la mercancía está marcado como que necesita código de Subpartida, el usuario de webservice debe enviar:

```xml
<SUBPARTIDA_CODE>XX</SUBPARTIDA_CODE>
```

Donde `XX` es un código numérico de 2 dígitos (tercer nivel de la codificación armonizada).

Cuando el código de la Subpartida requiere el Código de Arancel, se debe enviar:

```xml
<CODIGOARANCEL_CODE>YY</CODIGOARANCEL_CODE>
```

Donde `YY` es un código numérico de 2 dígitos (cuarto nivel de la codificación armonizada).

> Si el usuario no envía el código de la subpartida o del Arancel cuando son requeridos, el RNDC enviará un mensaje de error.

### Ejemplo: XML para transporte de Gasolina para automóviles

```xml
<MERCANCIAREMESA>002710</MERCANCIAREMESA>
<CODIGOUN>1203</CODIGOUN>
<SUBPARTIDA_CODE>12</SUBPARTIDA_CODE>
<CODIGOARANCEL_CODE>13</CODIGOARANCEL_CODE>
```

---

## 6. Residuos Peligrosos

### Etiquetas XML Específicas para Residuos Peligrosos

**`<CODNATURALEZACARGA>`:** Para Residuos Peligrosos, el valor es `5`.

**`<PELIGROSIDAD>`:** Códigos de 3 letras permitidos:

| Código | Descripción |
|---|---|
| `COR` | Corrosivo |
| `REA` | Reactivo |
| `EXP` | Explosivo |
| `TOX` | Toxico |
| `IFM` | Inflamable |
| `IFC` | Infeccioso |
| `RAD` | Radiactivo |

**`<RESIDUO>`:** Código de la Corriente del Residuo Peligroso. Corresponde a la codificación de los Residuos Peligrosos del Convenio de Basilea, Anexo I (serie Y) y Anexo VIII (serie A).

**`<RESIDUODESAGREGACION>`:** Subdivisión de la corriente (si aplica). Ejemplo: `Y1.3`.

**`<NOMBRENEP>`:** Nombre técnico o grupo químico del N.E.P. Texto libre, máximo **80 caracteres**.

**`<DESCRIPCIONDETALLADARESIDUO>`:** Descripción detallada del residuo peligroso. Texto libre, máximo **80 caracteres**.

### Ejemplo: XML Residuo Peligroso – Desechos Clínicos

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
  <acceso>
    <username>USUARIO1</username>
    <password>PASSWORD1</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>3</procesoid>
  </solicitud>
  <variables>
    <NUMNITEMPRESATRANSPORTE>XXXXXX</NUMNITEMPRESATRANSPORTE>
    <CONSECUTIVOREMESA>XXXXXXX</CONSECUTIVOREMESA>
    <CODOPERACIONTRANSPORTE>G</CODOPERACIONTRANSPORTE>
    <CODNATURALEZACARGA>5</CODNATURALEZACARGA>
    <MERCANCIAREMESA>002701</MERCANCIAREMESA>
    <CODTIPOEMPAQUE>0</CODTIPOEMPAQUE>
    <UNIDADMEDIDACAPACIDAD>1</UNIDADMEDIDACAPACIDAD>
    <CANTIDADCARGADA>2500</CANTIDADCARGADA>
    <CODIGOUN>3895</CODIGOUN>
    <ESTADOMERCANCIA>S</ESTADOMERCANCIA>
    <NOMBRENEP>JERINGAS</NOMBRENEP>
    <DESCRIPCIONDETALLADARESIDUO>AGUJAS</DESCRIPCIONDETALLADARESIDUO>
    <RESIDUO>Y1</RESIDUO>
    <RESIDUODESAGREGACION>Y1.3</RESIDUODESAGREGACION>
    <PELIGROSIDAD>IFC</PELIGROSIDAD>
  </variables>
</root>
```

### Convenio de Basilea – Corrientes de Residuos Peligrosos

#### Anexo I: Corrientes de Desechos (Serie Y)

| Código | Descripción |
|---|---|
| Y1 | Desechos clínicos resultantes de la atención médica prestada en hospitales, centros médicos y clínicas. |
| Y2 | Desechos resultantes de la producción y preparación de productos farmacéuticos. |
| Y3 | Desechos de medicamentos y productos farmacéuticos. |
| Y4 | Desechos resultantes de la producción, la preparación y la utilización de biocidas y productos fitofarmacéuticos. |
| Y5 | Desechos resultantes de la fabricación, preparación y utilización de productos químicos para la preservación de la madera. |
| Y6 | Desechos resultantes de la producción, la preparación y la utilización de disolventes orgánicos. |
| Y7 | Desechos que contengan cianuros, resultantes del tratamiento térmico y las operaciones de temple. |
| Y8 | Desechos de aceites minerales no aptos para el uso al que estaban destinados. |
| Y9 | Mezclas y emulsiones de desecho de aceite y agua o de hidrocarburos y agua. |
| Y10 | Sustancias y artículos de desecho que contengan, o estén contaminados por, bifenilos policlorados (PCB), terfenilos policlorados (PCT) o bifenilos polibromados (PBB). |
| Y11 | Residuos alquitranados resultantes de la refinación, destilación o cualquier otro tratamiento pirológico. |
| Y12 | Desechos resultantes de la producción, preparación y utilización de tintas, colorantes, pigmentos, pinturas, lacas o barnices. |
| Y13 | Desechos resultantes de la producción, preparación y utilización de resinas, látex, plastificantes o adhesivos. |
| Y14 | Sustancias químicas de desecho, no identificadas o nuevas, resultantes de la investigación y el desarrollo o de las actividades de enseñanza y cuyos efectos en el ser humano o el medio ambiente no se conozcan. |
| Y15 | Desechos de carácter explosivo que no estén sometidos a una legislación diferente. |
| Y16 | Desechos resultantes de la producción, preparación y utilización de productos químicos y materiales para fines fotográficos. |
| Y17 | Residuos resultantes del tratamiento de superficie de metales y plásticos. |
| Y18 | Residuos resultantes de las operaciones de eliminación de desechos industriales. |

**Anexo I: Desechos que tengan como constituyentes**

| Código | Descripción |
|---|---|
| Y19 | Metales carbonilos |
| Y20 | Berilio, compuestos de berilio |
| Y21 | Compuestos de cromo hexavalente |
| Y22 | Compuestos de cobre |
| Y23 | Compuestos de zinc |
| Y24 | Arsénico, compuestos de arsénico |
| Y25 | Selenio, compuestos de selenio |
| Y26 | Cadmio, compuestos de cadmio |
| Y27 | Antimonio, compuestos de antimonio |
| Y28 | Telurio, compuestos de telurio |
| Y29 | Mercurio, compuestos de mercurio |
| Y30 | Talio, compuestos de talio |
| Y31 | Plomo, compuestos de plomo |
| Y32 | Compuestos inorgánicos de flúor, con exclusión del fluoruro cálcico |
| Y33 | Cianuros inorgánicos |
| Y34 | Soluciones ácidas o ácidos en forma sólida |
| Y35 | Soluciones básicas o bases en forma sólida |
| Y36 | Asbesto (polvo y fibras) |
| Y37 | Compuestos orgánicos de fósforo |
| Y38 | Cianuros orgánicos |
| Y39 | Fenoles, compuestos fenólicos, con inclusión de clorofenoles |
| Y40 | Éteres |
| Y41 | Solventes orgánicos halogenados |
| Y42 | Disolventes orgánicos, con exclusión de disolventes halogenados |
| Y43 | Cualquier sustancia del grupo de los dibenzofuranos policlorados |
| Y44 | Cualquier sustancia del grupo de las dibenzoparadioxinas policloradas |
| Y45 | Compuestos organohalogenados, que no sean las sustancias mencionadas en el presente anexo (por ejemplo, Y39, Y41, Y42, Y43, Y44) |

#### Anexo VIII Lista A (Extracto)

Los desechos enumerados en el Anexo VIII están caracterizados como peligrosos de conformidad con el apartado a) del párrafo 1 del Convenio de Basilea.

| Código | Descripción |
|---|---|
| A1010 | Desechos metálicos y desechos que contengan aleaciones de: Antimonio, Arsénico, Berilio, Cadmio, Plomo, Mercurio, Selenio, Telurio, Talio (excluidos los desechos que figuran específicamente en la lista B). |
| A1020 | Desechos que tengan como constituyentes o contaminantes (excluidos los desechos de metal en forma masiva): Antimonio/compuestos, Berilio/compuestos, Cadmio/compuestos, Plomo/compuestos, Selenio/compuestos, Telurio/compuestos. |
| A1030 | Desechos que tengan como constituyentes o contaminantes: Arsénico/compuestos, Mercurio/compuestos, Talio/compuestos. |
| A1040 | Desechos que tengan como constituyentes: Carbonilos de metal, Compuestos de cromo hexavalente. |
| A1050 | Lodos galvánicos. |
| A1060 | Líquidos de desecho del decapaje de metales. |
| A1070 | Residuos de lixiviación del tratamiento del zinc, polvos y lodos como jarosita, hematites, etc. |
| A1080 | Residuos de desechos de zinc no incluidos en la lista B, que contengan plomo y cadmio en concentraciones peligrosas. |
| A1090 | Cenizas de la incineración de cables de cobre recubiertos. |
| A1100 | Polvos y residuos de los sistemas de depuración de gases de las fundiciones de cobre. |
| A1110 | Soluciones electrolíticas usadas de las operaciones de refinación y extracción electrolítica del cobre. |
| A1120 | Lodos residuales (excluidos los fangos anódicos) de los sistemas de depuración electrolítica de las operaciones de refinación y extracción electrolítica del cobre. |
| A1130 | Soluciones de ácidos para grabar usadas que contengan cobre disuelto. |
| A1140 | Desechos de catalizadores de cloruro cúprico y cianuro de cobre. |
| A1150 | Cenizas de metales preciosos procedentes de la incineración de circuitos impresos no incluidos en la lista B2. |
| A1160 | Acumuladores de plomo de desecho, enteros o triturados. |
| A1170 | Acumuladores de desecho sin seleccionar, excluidas mezclas de acumuladores sólo de la lista B. |
| A1180 | Montajes eléctricos y electrónicos de desecho que contengan componentes como acumuladores y otras baterías incluidos en la lista A, interruptores de mercurio, vidrios de tubos de rayos catódicos y otros vidrios activados y capacitadores de PCB, o contaminados con constituyentes del Anexo I en tal grado que posean alguna de las características del Anexo III. |
| A2010 | Desechos de vidrio de tubos de rayos catódicos y otros vidrios activados. |
| A2020 | Desechos de compuestos inorgánicos de flúor en forma de líquidos o lodos (excluidos los desechos de ese tipo especificados en la lista B). |
| A2030 | Desechos de catalizadores (excluidos los desechos de este tipo especificados en la lista B). |
| A2040 | Yeso de desecho procedente de procesos de la industria química, si contiene constituyentes del Anexo I en tal grado que presenten una característica peligrosa del Anexo III. |
| A2050 | Desechos de amianto (polvo y fibras). |
| A2060 | Cenizas volantes de centrales eléctricas de carbón que contengan sustancias del Anexo I en concentraciones tales que presenten características del Anexo III. |
| A3010 | Desechos resultantes de la producción o el tratamiento de coque de petróleo y asfalto. |
| A3020 | Aceites minerales de desecho no aptos para el uso al que estaban destinados. |
| A3030 | Desechos que contengan, estén integrados o estén contaminados por lodos de compuestos antidetonantes con plomo. |
| A3040 | Desechos de líquidos térmicos (transferencia de calor). |

> **Nota:** La codificación del Anexo VIII continúa con más entradas. Se muestra aquí un extracto de las series A1, A2 y A3 más relevantes para referencia en el RNDC.

### Desagregaciones del Residuo Y1 (Ejemplo)

| Código | Descripción |
|---|---|
| Y1.1 | Desechos clínicos ANATOMOPATOLÓGICOS resultantes de la atención en salud en hospitales, consultorios, clínicas y otros. |
| Y1.2 | Desechos clínicos BIOSANITARIOS resultantes de la atención en salud en hospitales, consultorios, clínicas y otros. |
| Y1.3 | Desechos clínicos CORTOPUNZANTES resultantes de la atención en salud en hospitales, consultorios, clínicas y otros. |
| Y1.4 | Residuos de ANIMALES – residuos de decomisos NO aprovechables. |

> Algunos Residuos Peligrosos no tienen desagregación. Por ejemplo, el Y2 no tiene desagregación y por lo tanto el código de la Desagregación no se debe enviar.

---

## 7. Diccionario de Errores

El sistema RNDC tiene descrito en sus bases de datos, en **CONSULTAR → CONSULTAR MAESTROS**, el diccionario de errores. Puede visualizar el error con su código y la solución para subsanar el problema y que el sistema le permita radicar el registro.

Para consultar los mensajes de error de las remesas se digita el **Proceso ID 3**.

### Ejemplo de Errores Comunes en Remesas

<!-- Tabla compleja: convertida a lista -->

**Error REM099**
- **Proceso:** 3
- **Variable:** MERCANCIAREMESA
- **Tipo Error:** E
- **Mensaje:** El código de la mercancía para el transporte de un contenedor vacío es 9990.
- **Solución:** Revisar si efectivamente se transporta un contenedor vacío, porque el código es 9990.

**Error REM119**
- **Proceso:** 3
- **Variable:** CODIGOARANCEL_CODE
- **Tipo Error:** E
- **Mensaje:** No existe el Código del Arancel enviado para detallar el Capítulo - Partida - Subpartida de la codificación Armonizada.
- **Solución:** Consultar la codificación de Códigos Arancelarios para el Capítulo-Partida-Subpartida enviado en la codificación armonizada de la mercancía, y escoger el código de la mercancía más detallada.

**Error REM118**
- **Proceso:** 3
- **Variable:** CODIGOARANCEL_CODE
- **Tipo Error:** E
- **Mensaje:** Se necesita el Código del Arancel para la codificación armonizada registrada en el dato de Mercancía Remesa, el cual es a nivel de Capítulo y Partida más la Subpartida.
- **Solución:** Consultar la codificación de Códigos Arancelarios para el Capítulo-Partida-Subpartida enviado en la codificación armonizada de la mercancía, y escoger el código de la mercancía más detallada.

**Error REM112**
- **Proceso:** 3
- **Variable:** SUBPARTIDA_CODE
- **Tipo Error:** E
- **Mensaje:** No existe el Código de la Subpartida enviado para detallar el Capítulo y Partida de la codificación Armonizada.
- **Solución:** Consultar la codificación de Subpartidas para el capítulo-partida enviado en la codificación armonizada de la mercancía, y escoger el código de la mercancía más detallada.

---

*Fin del documento – Guía Registro Remesa Sistema RNDC – Versión 4*
