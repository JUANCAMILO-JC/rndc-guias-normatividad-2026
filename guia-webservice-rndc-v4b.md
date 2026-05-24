---
title: "Guía de Uso del Web Service en el RNDC"
source: "GUIA_Uso_del_Web_Service_en_el_RNDC_LC_V4_compressed.pdf"
date_converted: "2026-05-24"
version: "4"
approved_by: "Juan Felipe Sanabria Saetta"
approval_date: "2023-06-22"
issuer: "Ministerio de Transporte de Colombia – Grupo de Logística"
total_sections: 8
---

# Guía de Uso del Web Service en el RNDC

**Sistema de Información:** Registro Nacional de Despachos de Carga (RNDC)
**Versión:** 4
**Elaborado por:** Jairo Vesga
**Revisado por:** Edna Lorena Gutiérrez
**Aprobado por:** Juan Felipe Sanabria Saetta
**Fecha de aprobación:** 22/06/2023
**Descripción de modificaciones:** Se modifica versión de la guía de Uso del Web Service en el RNDC para incluir lo definido en la resolución 20233040045515 de 2022.

---

## Tabla de Contenido

- [Introducción](#introducción)
- [1. Arquitectura del Web Service del RNDC](#1-arquitectura-del-web-service-del-rndc)
- [2. Elementos de la arquitectura del XML del Web Service](#2-elementos-de-la-arquitectura-del-xml-del-web-service)
- [3. Ambiente de pruebas](#3-ambiente-de-pruebas)
- [4. Usando paso a paso el Web Service](#4-usando-paso-a-paso-el-web-service)
- [5. Consultas de información de los datos grabados previamente en el RNDC, usando Web Service](#5-consultas-de-información-de-los-datos-grabados-previamente-en-el-rndc-usando-web-service)
- [6. Herramienta wstest para aprendizaje del Web Service del RNDC](#6-herramienta-wstest-para-aprendizaje-del-web-service-del-rndc)
- [7. Diccionario de datos](#7-diccionario-de-datos)
- [8. Diccionario de Errores](#8-diccionario-de-errores)

---

## Introducción

Este documento tiene por objeto establecer los estándares y parámetros para guiar a los usuarios en la transmisión y recepción de los datos, en el marco de interacción con el **RNDC WEB-SERVICE**. Busca facilitar el uso adecuado de la aplicación y la ejecución del proceso de transporte que se está instrumentando a través del RNDC, de una manera fácil y rápida.

Un Web Service o servicio web es un fragmento de software que usa un conjunto de protocolos y estándares que sirven para intercambiar datos entre aplicaciones. En el caso del RNDC, el Web Service busca que las aplicaciones desarrolladas por y para las diferentes empresas de transporte puedan intercambiar datos con la aplicación del RNDC.

El **RNDC WEB-SERVICE** ofrece interoperabilidad entre aplicaciones de software creadas con propiedades diferentes e instaladas en plataformas diferentes. Además, al usar estándares y protocolos basados en texto (cadenas de caracteres) hace que sea más fácil acceder al contenido generado y entender claramente su funcionamiento. Por último, el **RNDC WEB-SERVICE** permite que las aplicaciones de todas las empresas de transporte puedan interactuar con la plataforma y combinar fácilmente la información para que ésta sea centralizada.

---

## 1. Arquitectura del Web Service del RNDC

El Web Service del RNDC atiende con protocolo **SOAP** (Simple Object Access Protocol) y formato de datos **XML**.

- **URL principal del Web Service:** `http://rndcws.mintransporte.gov.co:8080`
- **URL del archivo WSDL (principal):** `http://rndcws.mintransporte.gov.co:8080/ws`
- **URL de contingencia (WSDL):** `http://rndcws2.mintransporte.gov.co:8080/ws`

> **Nota:** Adicional a la URL que se encuentra en el WSDL, el RNDC posee otra URL de contingencia que puede ser usada en caso de que la original no funcione.

### WSDL del servicio (Web-Service Definition Language)

El servicio expone el PortType `IBPMServices` con dos operaciones:

- `AtenderMensajeRNDC` – Operación principal para el envío y actualización de información en el RNDC.
- `AtenderMensajeBPM` – Operación auxiliar de BPM.

```xml
<definitions
  xmlns="http://schemas.xmlsoap.org/wsdl/"
  xmlns:xs="http://www.w3.org/2001/XMLSchema"
  xmlns:tns="http://tempuri.org/"
  xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"
  xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/"
  xmlns:mime="http://schemas.xmlsoap.org/wsdl/mime/"
  name="IBPMServicesservice"
  targetNamespace="http://tempuri.org/">

  <message name="AtenderMensajeRNDC0Request">
    <part name="Request" type="xs:string"/>
  </message>
  <message name="AtenderMensajeRNDC0Response">
    <part name="return" type="xs:string"/>
  </message>
  <message name="AtenderMensajeBPM1Request">
    <part name="Request" type="xs:string"/>
  </message>
  <message name="AtenderMensajeBPM1Response">
    <part name="return" type="xs:string"/>
  </message>

  <portType name="IBPMServices">
    <operation name="AtenderMensajeRNDC">
      <input message="tns:AtenderMensajeRNDC0Request"/>
      <output message="tns:AtenderMensajeRNDC0Response"/>
    </operation>
    <operation name="AtenderMensajeBPM">
      <input message="tns:AtenderMensajeBPM1Request"/>
      <output message="tns:AtenderMensajeBPM1Response"/>
    </operation>
  </portType>

  <binding name="IBPMServicesbinding" type="tns:IBPMServices">
    <binding xmlns="http://schemas.xmlsoap.org/wsdl/soap/"
             style="rpc"
             transport="http://schemas.xmlsoap.org/soap/http"/>
    <operation name="AtenderMensajeRNDC">
      <operation xmlns="http://schemas.xmlsoap.org/wsdl/soap/"
                 soapAction="urn:BPMServicesIntfIBPMServices#AtenderMensajeRNDC"
                 style="rpc"/>
      <input>
        <body xmlns="http://schemas.xmlsoap.org/wsdl/soap/"
              use="encoded"
              encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"
              namespace="urn:BPMServicesIntf-IBPMServices"/>
      </input>
      <output>
        <body xmlns="http://schemas.xmlsoap.org/wsdl/soap/"
              use="encoded"
              encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"
              namespace="urn:BPMServicesIntf-IBPMServices"/>
      </output>
    </operation>
    <operation name="AtenderMensajeBPM">
      <operation xmlns="http://schemas.xmlsoap.org/wsdl/soap/"
                 soapAction="urn:BPMServicesIntfIBPMServices#AtenderMensajeBPM"
                 style="rpc"/>
      <input>
        <body xmlns="http://schemas.xmlsoap.org/wsdl/soap/"
              use="encoded"
              encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"
              namespace="urn:BPMServicesIntf-IBPMServices"/>
      </input>
      <output>
        <body xmlns="http://schemas.xmlsoap.org/wsdl/soap/"
              use="encoded"
              encodingStyle="http://schemas.xmlsoap.org/soap/encoding/"
              namespace="urn:BPMServicesIntf-IBPMServices"/>
      </output>
    </operation>
  </binding>

  <service name="IBPMServicesservice">
    <port name="IBPMServicesPort" binding="tns:IBPMServicesbinding">
      <address xmlns="http://schemas.xmlsoap.org/wsdl/soap/"
               location="http://rndcws.mintransporte.gov.co:8080/soap/IBPMServices"/>
    </port>
  </service>

</definitions>
```

### Método principal: AtenderMensajeRNDC

Con un solo Web Service se pueden realizar todas las operaciones necesarias para enviar o actualizar la información, tanto en el registro de Terceros y Vehículos como en cada uno de los pasos del proceso.

- **Método:** `AtenderMensajeRNDC`
- **Parámetro de entrada:** `Request` (cadena en formato XML)
- **Respuesta:** cadena en formato XML con el número de radicación o con el texto del error (o errores)

### Estructura general del XML de Request

El `Request` debe tener la siguiente estructura, con un elemento principal `<root>` y cuatro elementos secundarios:

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
  <acceso>
    <!-- Seguridad del acceso -->
  </acceso>
  <solicitud>
    <!-- Qué se desea hacer y en cuál proceso -->
  </solicitud>
  <variables>
    <!-- Detalle de la información que se envía -->
  </variables>
  <documento>
    <!-- Datos para filtrar el documento del proceso a consultar -->
  </documento>
</root>
```

### Estructura de la respuesta exitosa

Cuando los registros se han realizado satisfactoriamente, la respuesta lleva siempre el siguiente formato:

```xml
<?xml version="1.0" encoding="ISO-8859-1" ?>
<root>
  <ingresoid>12</ingresoid>
</root>
```

El número `12` es el consecutivo de radicado. El consecutivo cambia cada vez que se acepta un registro nuevo sin errores.

---

## 2. Elementos de la arquitectura del XML del Web Service

### Elemento `<acceso>`

Contempla dos subelementos:

- `<username>uuuuuu</username>` — código del usuario de la empresa de transporte, generador de carga, empresa de GPS u otro actor de la cadena de transporte.
- `<password>pppppp</password>` — palabra clave del usuario.

### Elemento `<solicitud>`

Contempla dos subelementos:

#### `<tipo>` — Tipo de operación

| Valor | Descripción |
|-------|-------------|
| 1 | Registrar información en procesos y maestros |
| 2 | Consultar registros de maestros |
| 3 | Consultar documentos o registros de cualquier proceso |
| 4 | Consulta para la Policía |
| 5 | Consulta para generadores de carga |
| 6 | Consulta de maestros especiales |
| 7 | Crear un usuario desde la app RNDC transportador |
| 8 | Consulta de un conductor |
| 9 | Consultas de remesas autorizadas para empresas de GPS |

#### `<procesoid>` — Número del proceso

| ID | Proceso |
|----|---------|
| 1 | Registrar información de carga |
| 2 | Registrar información de viaje |
| 3 | Expedir remesa terrestre de carga |
| 4 | Expedir manifiesto de carga |
| 5 | Cumplir remesa terrestre de carga |
| 6 | Cumplir manifiesto de carga |
| 7 | Anular información de carga |
| 8 | Anular información del viaje |
| 9 | Anular remesa terrestre de carga |
| 11 | Crear o actualizar datos de tercero (Maestro) |
| 12 | Crear o actualizar datos de vehículo (Maestro) |
| 17 | Diccionario de datos (Maestro) |
| 26 | SiceTac |
| 27 | Diccionario de errores (Maestro) |
| 28 | Anular cumplido de remesa |
| 29 | Anular cumplido de manifiesto |
| 32 | Anular manifiesto de carga |
| 34 | Tarifas o fletes de generador de carga |
| 38 | Corregir remesa |
| 39 | Control en carretera |
| 40 | Puesto de control en carretera (Maestro) |
| 41 | Anular flete de generador / Anular flete del generador de carga |
| 45 | Registrar un cumplido inicial de remesa (empresa de GPS o empresa de transporte) |
| 46 | Registrar novedades de empresa de GPS |
| 48 | Registro Nacional Automotor (Maestro) |
| 54 | Anular cumplido inicial de remesa |
| 73 | Aceptación electrónica del manifiesto por parte del titular del manifiesto o del conductor |
| 75 | Delegar aceptación electrónica del titular del manifiesto al conductor |
| 79 | Cumplido de viaje municipal |
| 81 | Registro de viaje municipal |
| 83 | Remesa municipal |
| 86 | Factura electrónica de transporte |
| 91 | Anular registros de viaje municipal |
| 92 | Anular remesa municipal |
| 93 | Anular cumplido de viaje municipal |

### Elemento `<variables>`

El elemento `<variables>` tiene `n` subelementos y depende del proceso al cual se desea enviar información. Cada elemento tiene como etiqueta el nombre de la variable del Diccionario de Datos, al cual se puede acceder en el portal `rndc.mintransporte.gov.co` en la consulta de maestros.

### Elemento `<documento>`

El elemento `<documento>` solo se necesita cuando se quiere **consultar** información. Si se desea radicar o enviar información hacia los procesos del RNDC, ese elemento no se usa.

### Ejemplo completo de estructura XML

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
  <acceso>
    <username>uuuuuu</username>
    <password>pppppp</password>
  </acceso>
  <solicitud>
    <tipo>x</tipo>
    <procesoid>xx</procesoid>
  </solicitud>
  <variables>
    <numnitempresatransporte>xxxxxx</numnitempresatransporte>
  </variables>
</root>
```

---

## 3. Ambiente de pruebas

Las empresas de transporte pueden realizar sus pruebas del Web Service en un servidor de pruebas independiente.

- **URL WSDL ambiente de pruebas:** `http://plc.mintransporte.gov.co:8080/ws`
- **URL herramienta wstest (ambiente de pruebas):** `rndc.mintransporte.gov.co/wstest/defaultp.aspx`

Los usuarios del ambiente de producción pueden usar las mismas credenciales en el ambiente de pruebas. En el ambiente de pruebas, el sistema RNDC puede responder con números de radicados diferentes al orden de los consecutivos del ambiente de producción normal. La base de datos de pruebas del RNDC cambia cada año por una nueva foto del ambiente de producción.

---

## 4. Usando paso a paso el Web Service

Para realizar un proceso rápido y sin interrupciones, se recomienda primero realizar el ingreso de la información de conductores, propietarios o tenedores de vehículos, empresas, personas naturales y vehículos, antes de realizar el proceso de registro de la información en el RNDC.

Solo se debe efectuar una vez el registro en el sistema. Luego de que éste se guarde en la base de datos, solo se necesita enviar el tipo de documento y el número de documento (terceros) o placa (vehículos), para que la información restante sea heredada automáticamente por el proceso que se está realizando.

Los terceros y vehículos se deben registrar únicamente cuando hay cambios en alguna información. El RNDC envía un mensaje de error cuando recibe un XML de creación de tercero o vehículo y la información coincide con la que ya está guardada en la base de datos.

### Ejemplo: Crear un tercero sin licencia de conducción (proceso 11)

**Caso:** Linda Barreto Arévalo, cédula de ciudadanía No. 51.760.125 de Bogotá, reside en la Calle 156 # 9-50, teléfono 6753733. Puede asumir el rol de Titular de Manifiesto, Propietario de Vehículo, Tenedor de Vehículo y Generador de Carga.

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
  <acceso>
    <username>USUARIO1</username>
    <password>CLAVE</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>11</procesoid>
  </solicitud>
  <variables>
    <NUMNITEMPRESATRANSPORTE>900301001</NUMNITEMPRESATRANSPORTE>
    <CODTIPOIDTERCERO>C</CODTIPOIDTERCERO>
    <NUMIDTERCERO>51760125</NUMIDTERCERO>
    <NOMIDTERCERO>LINDA</NOMIDTERCERO>
    <PRIMERAPELLIDOIDTERCERO>BARRETO</PRIMERAPELLIDOIDTERCERO>
    <SEGUNDOAPELLIDOIDTERCERO>AREVALO</SEGUNDOAPELLIDOIDTERCERO>
    <NUMTELEFONOCONTACTO>6753733</NUMTELEFONOCONTACTO>
    <NOMENCLATURADIRECCION>CALLE 156 # 9-50</NOMENCLATURADIRECCION>
    <CODMUNICIPIORNDC>11001000</CODMUNICIPIORNDC>
  </variables>
</root>
```

### Ejemplo: Crear un vehículo (proceso 12)

**Caso:** Tractocamión de 3 ejes, marca Chevrolet, línea código 373, placa WZH111, modelo 2010. Propietaria y tenedora: Linda Barreto Arévalo. Combustible: ACPM, peso vacío: 8000 kg, carrocería: S.R.S. Aseguradora: MAPFRE CREDISEGURO S.A. (NIT 8110191907), póliza AT131811151729, vence 14/10/2011.

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
  <acceso>
    <username>USUARIO1</username>
    <password>CLAVE</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>12</procesoid>
  </solicitud>
  <variables>
    <NUMNITEMPRESATRANSPORTE>900301001</NUMNITEMPRESATRANSPORTE>
    <NUMPLACA>WZH111</NUMPLACA>
    <CODCONFIGURACIONUNIDADCARGA>55</CODCONFIGURACIONUNIDADCARGA>
    <CODMARCAVEHICULOCARGA>1</CODMARCAVEHICULOCARGA>
    <CODLINEAVEHICULOCARGA>373</CODLINEAVEHICULOCARGA>
    <ANOFABRICACIONVEHICULOCARGA>2010</ANOFABRICACIONVEHICULOCARGA>
    <CODTIPOCOMBUSTIBLE>1</CODTIPOCOMBUSTIBLE>
    <PESOVEHICULOVACIO>8000</PESOVEHICULOVACIO>
    <CODTIPOCARROCERIA>0</CODTIPOCARROCERIA>
    <CODTIPOIDPROPIETARIO>C</CODTIPOIDPROPIETARIO>
    <NUMIDPROPIETARIO>51760125</NUMIDPROPIETARIO>
    <CODTIPOIDTENEDOR>C</CODTIPOIDTENEDOR>
    <NUMIDTENEDOR>51760125</NUMIDTENEDOR>
    <NUMSEGUROSOAT>AT131811151729</NUMSEGUROSOAT>
    <FECHAVENCIMIENTOSOAT>14/10/2011</FECHAVENCIMIENTOSOAT>
    <NUMNITASEGURADORASOAT>8110191907</NUMNITASEGURADORASOAT>
  </variables>
</root>
```

### Ejemplo: Crear una Remesa Terrestre de Carga (proceso 3, consecutivo 0001)

**Caso:** Carga de 22.000 kg. Tomador de póliza: empresa de transporte, póliza No. 15987462357, vence 08/08/2012. Aseguradora: Royal y Sun Alliance Seguros (Colombia) S.A. (NIT 8600025057). Fecha de cargue: 10/08/2011.

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
  <acceso>
    <username>USUARIO1</username>
    <password>CLAVE</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>3</procesoid>
  </solicitud>
  <variables>
    <NUMNITEMPRESATRANSPORTE>900301001</NUMNITEMPRESATRANSPORTE>
    <CONSECUTIVOREMESA>0001</CONSECUTIVOREMESA>
    <CODOPERACIONTRANSPORTE>1</CODOPERACIONTRANSPORTE>
    <CODNATURALEZACARGA>G</CODNATURALEZACARGA>
    <CANTIDADCARGADA>22000</CANTIDADCARGADA>
    <UNIDADMEDIDACAPACIDAD>1</UNIDADMEDIDACAPACIDAD>
    <CODTIPOEMPAQUE>10</CODTIPOEMPAQUE>
    <PESOCONTENEDORVACIO>2800</PESOCONTENEDORVACIO>
    <MERCANCIAREMESA>000201</MERCANCIAREMESA>
    <DESCRIPCIONCORTAPRODUCTO>TRIGO BLANCO</DESCRIPCIONCORTAPRODUCTO>
    <CODTIPOIDREMITENTE>C</CODTIPOIDREMITENTE>
    <NUMIDREMITENTE>4676747</NUMIDREMITENTE>
    <CODSEDEREMITENTE>1</CODSEDEREMITENTE>
    <CODTIPOIDDESTINATARIO>C</CODTIPOIDDESTINATARIO>
    <NUMIDDESTINATARIO>46456</NUMIDDESTINATARIO>
    <CODSEDEDESTINATARIO>2</CODSEDEDESTINATARIO>
    <DUENOPOLIZA>E</DUENOPOLIZA>
    <NUMPOLIZATRANSPORTE>15987462357</NUMPOLIZATRANSPORTE>
    <FECHAVENCIMIENTOPOLIZACARGA>08/08/2012</FECHAVENCIMIENTOPOLIZACARGA>
    <COMPANIASEGURO>8600025057</COMPANIASEGURO>
    <HORASPACTOCARGA>4</HORASPACTOCARGA>
    <MINUTOSPACTOCARGA>10</MINUTOSPACTOCARGA>
    <HORASPACTODESCARGUE>3</HORASPACTODESCARGUE>
    <MINUTOSPACTODESCARGUE>00</MINUTOSPACTODESCARGUE>
    <CODTIPOIDPROPIETARIO>N</CODTIPOIDPROPIETARIO>
    <NUMIDPROPIETARIO>5765765</NUMIDPROPIETARIO>
    <CODSEDEPROPIETARIO>3</CODSEDEPROPIETARIO>
    <PERMISOCARGAEXTRA>566</PERMISOCARGAEXTRA>
    <NUMIDGPS>5675756</NUMIDGPS>
  </variables>
</root>
```

### Ejemplo: Crear un Manifiesto de Carga (proceso 4, consecutivo 0001)

**Caso:** Manifiesto tipo general, expedición 29/07/2011, origen Cali (código 76001000), destino Bogotá (código 11001000). Titular: Edgar Moreno Silva, CC 79.616.565. Descuento ICA: 3 por mil. Anticipo: $1.000.000. Saldo en Bogotá el 29/07/2011. Remesas asociadas: 0001 y 0020.

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
  <acceso>
    <username>USUARIO1</username>
    <password>USUARIO1</password>
  </acceso>
  <solicitud>
    <tipo>1</tipo>
    <procesoid>4</procesoid>
  </solicitud>
  <variables>
    <NUMNITEMPRESATRANSPORTE>900301001</NUMNITEMPRESATRANSPORTE>
    <NUMMANIFIESTOCARGA>0001</NUMMANIFIESTOCARGA>
    <CODOPERACIONTRANSPORTE>G</CODOPERACIONTRANSPORTE>
    <FECHAEXPEDICIONMANIFIESTO>29/07/2011</FECHAEXPEDICIONMANIFIESTO>
    <CODMUNICIPIOORIGENMANIFIESTO>76001000</CODMUNICIPIOORIGENMANIFIESTO>
    <CODMUNICIPIODESTINOMANIFIESTO>11001000</CODMUNICIPIODESTINOMANIFIESTO>
    <CODIDTITULARMANIFIESTO>C</CODIDTITULARMANIFIESTO>
    <NUMIDTITULARMANIFIESTO>79616565</NUMIDTITULARMANIFIESTO>
    <NUMPLACA>XXXXXX</NUMPLACA>
    <NUMPLACAREMOLQUE>YYYYYY</NUMPLACAREMOLQUE>
    <CODIDCONDUCTOR>C</CODIDCONDUCTOR>
    <NUMIDCONDUCTOR>4675675</NUMIDCONDUCTOR>
    <CODIDCONDUCTOR2>C</CODIDCONDUCTOR2>
    <NUMIDCONDUCTOR2>96896</NUMIDCONDUCTOR2>
    <VALORFLETEPACTADOVIAJE>3250000</VALORFLETEPACTADOVIAJE>
    <RETENCIONICAMANIFIESTOCARGA>3</RETENCIONICAMANIFIESTOCARGA>
    <VALORANTICIPOMANIFIESTO>1000000</VALORANTICIPOMANIFIESTO>
    <CODMUNICIPIOPAGOSALDO>11001000</CODMUNICIPIOPAGOSALDO>
    <FECHAPAGOSALDOMANIFIESTO>29/07/2011</FECHAPAGOSALDOMANIFIESTO>
    <CODRESPONSABLEPAGOCARGUE>E</CODRESPONSABLEPAGOCARGUE>
    <CODRESPONSABLEPAGODESCARGUE>E</CODRESPONSABLEPAGODESCARGUE>
    <ACEPTACIONELECTRONICA>SI</ACEPTACIONELECTRONICA>
    <OBSERVACIONES>Se recomienda que en caso de accidente el conductor debe comunicarse al número celular 3102569871</OBSERVACIONES>
    <REMESASMAN procesoid="43">
      <REMESA>
        <CONSECUTIVOREMESA>0001</CONSECUTIVOREMESA>
      </REMESA>
      <REMESA>
        <CONSECUTIVOREMESA>0020</CONSECUTIVOREMESA>
      </REMESA>
    </REMESASMAN>
  </variables>
</root>
```

---

## 5. Consultas de información de los datos grabados previamente en el RNDC, usando Web Service

Las empresas de transporte pueden realizar consultas de cada uno de los procesos o registros de información enviada previamente. Para ello se usa el **tipo de solicitud 3** (Consulta) en vez del 1 (Envío de información).

### Ejemplo: Consultar si un manifiesto ya fue firmado (proceso 73)

Se utiliza tipo `3` y `procesoid` `73` (Aceptación Electrónica del Manifiesto).

**XML de consulta:**

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
  <acceso>
    <username>XXXXXX</username>
    <password>XXXXXX</password>
  </acceso>
  <solicitud>
    <tipo>3</tipo>
    <procesoid>73</procesoid>
  </solicitud>
  <variables>
    INGRESOID, FECHAING, TIPO, CODIDCONDUCTOR, NUMIDCONDUCTOR,
    CODIDTITULARMANIFIESTO, NUMIDTITULARMANIFIESTO, OBSERVACION
  </variables>
  <documento>
    <NUMNITEMPRESATRANSPORTE>8999990554</NUMNITEMPRESATRANSPORTE>
    <INGRESOIDMANIFIESTO>'46532952'</INGRESOIDMANIFIESTO>
  </documento>
</root>
```

**XML de respuesta:**

```xml
<?xml version="1.0" encoding="ISO-8859-1" ?>
<root>
  <documento>
    <ingresoid>4</ingresoid>
    <fechaing>20/03/2020 5:24:23 p. m.</fechaing>
    <tipo>C</tipo>
    <codidconductor>C</codidconductor>
    <numidconductor>19258361</numidconductor>
    <codidtitularmanifiesto></codidtitularmanifiesto>
    <numidtitularmanifiesto></numidtitularmanifiesto>
    <observacion>Aceptado el viaje</observacion>
  </documento>
</root>
```

> **Nota:** La fecha y hora entregada en el tag `<fechaing>` puede ser almacenada en la base de datos del sistema de información de la empresa de transporte, para que cuando realicen la generación del PDF del manifiesto aparezca en la ubicación de la firma electrónica.

### Ejemplo: Consulta de varias aprobaciones electrónicas en un rango de tiempo

**XML de consulta:**

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
  <acceso>
    <username>xxxxxxx@xxx</username>
    <password>xxxxxxxxxx</password>
  </acceso>
  <solicitud>
    <tipo>3</tipo>
    <procesoid>73</procesoid>
  </solicitud>
  <variables>
    INGRESOID, FECHAING, INGRESOIDMANIFIESTO, TIPO,
    CODIDCONDUCTOR, NUMIDCONDUCTOR, OBSERVACION
  </variables>
  <documento>
    <NUMNITEMPRESATRANSPORTE>8999990554</NUMNITEMPRESATRANSPORTE>
  </documento>
  <documentorango>
    <iniFECHAING>'2020/01/01'</iniFECHAING>
    <finFECHAING>'2020/03/31'</finFECHAING>
  </documentorango>
</root>
```

**XML de respuesta (múltiples documentos):**

```xml
<?xml version="1.0" encoding="ISO-8859-1" ?>
<root>
  <documento>
    <ingresoid>15</ingresoid>
    <fechaing>28/03/2020 9:44:52 a. m.</fechaing>
    <ingresoidmanifiesto>48043700</ingresoidmanifiesto>
    <tipo>C</tipo>
    <codidconductor>C</codidconductor>
    <numidconductor>80387330</numidconductor>
    <observacion>Celular 3103040052</observacion>
  </documento>
  <documento>
    <ingresoid>8</ingresoid>
    <fechaing>22/03/2020 10:26:49 p. m.</fechaing>
    <ingresoidmanifiesto>47492363</ingresoidmanifiesto>
    <tipo>T</tipo>
    <codidconductor></codidconductor>
    <numidconductor></numidconductor>
    <observacion>okk</observacion>
  </documento>
  <documento>
    <ingresoid>18</ingresoid>
    <fechaing>30/03/2020 8:37:08 a. m.</fechaing>
    <ingresoidmanifiesto>48088076</ingresoidmanifiesto>
    <tipo>C</tipo>
    <codidconductor>C</codidconductor>
    <numidconductor>79171592</numidconductor>
    <observacion>Celular 3134850261</observacion>
  </documento>
  <documento>
    <ingresoid>12</ingresoid>
    <fechaing>27/03/2020 12:31:07 p. m.</fechaing>
    <ingresoidmanifiesto>48045984</ingresoidmanifiesto>
    <tipo>C</tipo>
    <codidconductor>C</codidconductor>
    <numidconductor>79170327</numidconductor>
    <observacion>Celular 3112119340</observacion>
  </documento>
</root>
```

### Ejemplo: Consultar manifiestos pendientes de Aceptación Electrónica (proceso 4)

**XML de consulta:**

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
  <acceso>
    <username>xxxxxx@xxxx</username>
    <password>xxxxxxxxxxx</password>
  </acceso>
  <solicitud>
    <tipo>3</tipo>
    <procesoid>4</procesoid>
  </solicitud>
  <variables>
    INGRESOID, FECHAING, NUMMANIFIESTOCARGA, NUMIDTITULARMANIFIESTO,
    NUMPLACA, NUMIDCONDUCTOR
  </variables>
  <documento>
    <NUMNITEMPRESATRANSPORTE>8999990554</NUMNITEMPRESATRANSPORTE>
    <ACEPTACIONELECTRONICA>NULL</ACEPTACIONELECTRONICA>
  </documento>
  <documentorango>
    <iniFECHAING>'2020/04/01'</iniFECHAING>
    <finFECHAING>'2020/05/01'</finFECHAING>
  </documentorango>
</root>
```

**XML de respuesta:**

```xml
<?xml version="1.0" encoding="ISO-8859-1" ?>
<root>
  <documento>
    <ingresoid>48017065</ingresoid>
    <fechaing>05/04/2020 10:09:58 a. m.</fechaing>
    <nummanifiestocarga>M321</nummanifiestocarga>
    <numidtitularmanifiesto>19258361</numidtitularmanifiesto>
    <numplaca>BOD874</numplaca>
    <numidconductor>19258361</numidconductor>
  </documento>
</root>
```

---

## 6. Herramienta wstest para aprendizaje del Web Service del RNDC

El RNDC posee una herramienta web que permite comprender la forma en que se debe escribir el XML, realizar pruebas de cada operación y verificar respuestas del servidor.

### URLs disponibles

| URL | Servidor destino |
|-----|-----------------|
| `https://rndc.mintransporte.gov.co/wstest/default.aspx` | Servidor principal: `rndcws.mintransporte.gov.co:8080` |
| `https://rndc.mintransporte.gov.co/wstest/default2.aspx` | Servidor secundario: `rndcws2.mintransporte.gov.co:8080` |
| `https://rndc.mintransporte.gov.co/wstest/defaultp.aspx` | Servidor de pruebas: `plc.mintransporte.gov.co:8080` |

### Partes de la interfaz wstest

La herramienta muestra una pantalla compuesta por 4 partes:

1. **Lista de procesos del RNDC** — número y nombre de cada proceso disponible.
2. **Diccionario de datos del proceso seleccionado** — campos y validaciones.
3. **XML generado automáticamente** — se genera a partir del diccionario de datos y es editable.
4. **XML de respuesta del RNDC** — respuesta recibida al consumir el servicio.

### Flujo de uso de wstest

1. Ingresar usuario y clave.
2. Digitar el número del proceso en el campo **Proceso ID**.
3. Hacer clic en **Validar** para cargar el diccionario de datos del proceso.
4. Diligenciar los datos en los campos de cada variable. Los campos en blanco no se incluirán en el XML generado.
5. Hacer clic en **Generar XML para grabar** — el sistema muestra el XML resultante a la derecha.
6. Hacer clic en **Consumir Servicio** — el sistema envía el Web Service al servidor del RNDC y muestra la respuesta (número de radicado o mensajes de error).

### Botones adicionales disponibles en wstest

- **Generar XML para Consultar** — genera XML de tipo consulta (tipo 3).
- **Generar XML para Consultar Maestros Especial** — para maestros especiales.
- Campos de rango de fechas: `Fec.Inicio(yyyy/mm/dd)` y `Fec.Final(yyyy/mm/dd)`.

---

## 7. Diccionario de datos

Los usuarios pueden consultar el diccionario de datos para cada uno de los procesos a través del portal web del RNDC.

### Ruta de acceso en el portal

1. Ingresar a `rndc.mintransporte.gov.co`
2. Seleccionar el menú **Consultar**
3. Hacer clic en **Consultar Maestros**
4. Seleccionar **Diccionario de Datos** en la lista desplegable de maestros
5. Ingresar el **Proceso ID** deseado y hacer clic en **Consultar Registros**

### Estructura del Diccionario de Datos

El diccionario presenta las siguientes columnas por cada variable de proceso:

| Columna | Descripción |
|---------|-------------|
| Fecha Ingreso | Fecha en que se incorporó la variable |
| Proceso ID | Identificador numérico del proceso |
| Proceso | Nombre del proceso |
| Variable | Nombre de la variable (etiqueta XML) |
| Tamaño | Longitud máxima del campo |
| Tipo Dato | Tipo de dato (Varchar, Numérico, etc.) |
| Requerido | S = requerido, N = opcional |
| Descripción Variable | Explicación del campo |
| Validación | Reglas de validación aplicadas |
| Etiqueta | Nombre visible en la interfaz web |
| Consecutivo | Orden del campo |
| Web Service | Si aplica al Web Service (S/N) |
| Web Interactivo | Si aplica a la interfaz web interactiva (S/N) |

El usuario puede filtrar los registros escribiendo valores en la línea en blanco al inicio de cada columna. También puede hacer clic en **Transmitir Archivo Plano** para descargar la información en formato Excel.

---

## 8. Diccionario de Errores

Los usuarios pueden consultar el diccionario de errores para cada uno de los procesos a través del portal web del RNDC.

### Ruta de acceso en el portal

1. Ingresar a `rndc.mintransporte.gov.co`
2. Seleccionar el menú **Consultar**
3. Hacer clic en **Consultar Maestros**
4. Seleccionar **Diccionario de Errores** en la lista desplegable de maestros
5. Ingresar el **Proceso ID** y/o **Código Error** y hacer clic en **Consultar Registros**

### Estructura del Diccionario de Errores

El diccionario presenta las siguientes columnas:

| Columna | Descripción |
|---------|-------------|
| Fecha Ingreso | Fecha en que se incorporó el error |
| Proceso ID | Identificador numérico del proceso |
| Código Error | Código único del error |
| Mensaje Error | Texto descriptivo del error |
| Variable | Variable del XML a la que aplica el error |
| Tipo Error | Tipo de error (E = Error, I = Informativo, etc.) |
| Proceso | Nombre del proceso asociado |
| Solución | Acción recomendada para resolver el error |

### Ejemplos de errores del Diccionario

<!-- Tabla compleja: convertida a lista -->

- **FAC006** (Proceso 86 – Factura Electrónica): El `NUMNITEMPRESATRANSPORTE` debe coincidir con el NIT del Proveedor en el XML de la DIAN. Variable: `NUMNITEMPRESATRANSPORTE`. Solución: Verificar el dato `NUMNITEMPRESATRANSPORTE` o `NITFACTURADOR`.
- **FAC005** (Proceso 86 – Factura Electrónica): Falta el `NUMNITEMPRESATRANSPORTE`. Solución: Verificar el dato `NUMNITEMPRESATRANSPORTE` o `NITFACTURADOR`.
- **INFOR016** (Proceso 39 – Control en Carretera): `ESTADO_MATRICULA` inválido. Variable: `NUMPLACA`. Solución: Verificar el estado de la matrícula.
- **CRE101** (Proceso 5 – Cumplir Remesa): El manifiesto asociado a la remesa tiene una cita pendiente de cerrar en una terminal portuaria. Variable: `CONSECUTIVOREMESA`. Solución: Verificar con la terminal portuaria la causa del no cierre de la cita del manifiesto.
- **CRE322** (Proceso 5 – Cumplir Remesa): La fecha y hora de salida del descargue no puede ser futura. Variable: `FECHASALIDADESCARGUE`.
- **RTU370** (Proceso 81 – Viaje Urbano): El factor de retención de ICA no puede ser mayor al 20 por mil. Variable: `FACTORICA`.
- **ACU070** (Proceso 93 – Anular Cumplido Viaje Urbano): El consecutivo de viaje urbano no existe o no está cumplido. Variable: `CONSECUTIVOURBANO`.
- **ACU030** (Proceso 93 – Anular Cumplido Viaje Urbano): Falta el consecutivo de viaje urbano. Variable: `CONSECUTIVOURBANO`.
- **ACU040** (Proceso 93 – Anular Cumplido Viaje Urbano): El motivo de anulación no es correcto, debe ser D, O o Otro. Variable: `MOTIVOANULACION`.

El usuario puede filtrar los mensajes escribiendo el dato en la línea en blanco al inicio de cada columna. También puede hacer clic en **Transmitir Archivo Plano** para descargar la información en formato Excel.
