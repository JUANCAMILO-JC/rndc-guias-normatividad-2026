# GUÍA

# USO DE WEB SERVICE

# EN EL RNDC

# CONTROL DE CAMBIOS

Versión:4

# Elaborado por:

Jairo Vesga

# Revisado por:

Edna Lorena Gutiérrez

# Aprobado por:

Juan Felipe Sanabria Saetta

# Fecha de aprobación

22/06/2023

# Descripción de las modificaciones

22/06/2023: Se modifica versión de la guía de Uso del Web Service en el RNDC para incluir lo definido en la resolución 20233040045515 de 2022.

# TABLA DE CONTENIDO

# Introducción 4

1. Arquitectura del Web Service del RNDC .... 5   
2. Elementos de la arquitectura del XML del Web Service....10   
3. Ambiente de pruebas....14   
4. Usando paso a paso el Web Service ....14   
5. Consultas de información de los datos grabados previamente en el RNDC, usando Web Service ....21   
6. Herramienta wstest para aprendizaje del Web Service del RNDC .....25   
7. Diccionario de datos .....29   
8. Diccionario de Errores....32

# GUÍA USO DE WEB SERVICE EN EL RNDC

SISTEMA DE INFORMACIÓN REGISTRO NACIONAL DE DESPACHOS DE CARGA- RNDC

# Introducción

Este documento tiene por objeto establecer los estándares y parámetros para guiar a los usuarios en la transmisión y recepción de los datos, en el marco de interacción con el RNDC WEB-SERVICE. Busca facilitar el uso adecuado de la aplicación y la ejecución del proceso de transporte que se está instrumentando a través del RNDC, de una manera fácil y rápida.

Es importante resaltar que un Web Service o servicio web es un fragmento de software que usa un conjunto de protocolos y estándares que sirven para intercambiar datos entre aplicaciones. En el caso del RNDC, el Web Service busca que las aplicaciones desarrolladas por y para las diferentes empresas de transporte puedan intercambiar datos con la aplicación del RNDC.

El RNDC WEB-SERVICE ofrece interoperabilidad entre aplicaciones de software creadas con propiedades diferentes e instaladas en plataformas diferentes. Además, al usar estándares y protocolos basados en texto (cadenas de caracteres) hace que sea más fácil acceder al contenido generado y entender claramente su funcionamiento. Por último, el RNDC WEB-SERVICE permite que las aplicaciones de todas las empresas de transporte puedan interactuar con la plataforma y combinar fácilmente la información para que ésta sea centralizada.

# 1. Arquitectura del Web Service del RNDC

El Web Service del RNDC atiende con protocolo SOAP (Simple Object Access Protocol) y formato de datos XML. La url que atiende el Web Service del RNDC es: http://rndcws.mintransporte.gov.co:8080

Allí se puede consultar el archivo WSDL (WebService Definition Language)
http://rndcws.mintransporte.gov.co:8080/ws

← → C No es seguro | rndcws.mintransporte.gov.co:8080/ws

# wsSvr008svr - Service Info Page

wsSvr008svr - PortTypes:

IBPMServices [WSDL]

○ AtenderMensajeRNDC   
○ AtenderMensajeBPM

\- IWSDLPublish [WSDL]

Lists all the PortTypes published by this Service

GetPortTypeList   
GetWSDLForPortType   
○ GetTypeSystemsList   
GetXSDForTypeSystem

WSIL: Link to WS-Inspection document of Services here

# WSDL (Web-Service Definition Language)

<definitions xmlns="http://schemas.xmlsoap.org/wsdl/" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:tns="http://tempuri.org/" xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/" xmlns:mime="http://schemas.xmlsoap.org/wsdl/mime/" name="IBPMServiceservice" targetNamespace="http://tempuri.org/">

<message name="AtenderMensajeeRNDC0Request">

```xml
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
```

<binding xmlns="http://schemas.xmlsoap.org/wsdl/soap/" style="rpc" transport="http://schemas.xmlsoap.org/soap/http"/>

<operation name="AtenderMensajeeRNDC">

<operation xmlns="http://schemas.xmlsoap.org/wSDL/soap/" soapAction="urn:BPMServicesIntf-

IBPMServices#AtenderMensajeRNDC" style="rpc"/>

<input>

<body xmlns="http://schemas.xmlsoap.org/wsdl/soap/" use="encoded" encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:BPMServicesIntf-IBPMServices"/>

</input>

<output>

<body xmlns="http://schemas.xmlsoap.org/wsdl/soap/" use="encoded" encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:BPMServicesIntf-IBPMServices"/>

</output>

</operation>

<operation name="AtenderMensajeBPM">

<operation xmlns="http://schemas.xmlsoap.org/wSDL/soap/" soapAction="urn:BPMServicesIntf-

IBPMServices#AtenderMensajeBPM" style="rpc"/>
<input>

<body xmlns="http://schemas.xmlsoap.org/wsdl/soap/" use="encoded" encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:BPMServicesIntf-IBPMServices"/>

</input>

<output>

```xml
<body xmlns="http://schemas.xmlsoap.org/wsdl/soap/" use="encoded" encodingStyle="http://schemas.xmlsoap.org/soap/encoding/" namespace="urn:BPMServicesIntf-IBPMServices"/> 
```

```xml
</output>
</operation>
</binding>
<service name="IBPMServiceservice">
<port name="IBPMServicesPort" binding="tns:IBPMServicesbinding">
<address xmlns="http://schemas.xmlsoap.org/wsdl/soap/" location="http://rndcws.mintransporte.gov.co:8080/soap/IBPMServices"/>
</port>
</service>
</definitions> 
```

Adicional a la url que se encuentra en el WSDL, el RNDC posee otra url (contingencia) que puede ser usada en caso de que la original no funcione y el WSDL puede consultarse en:

http://rndcws2.mintransporte.gov.co:8080/ws

En el XML con un solo Web Service se pueden realizar todas las operaciones necesarias para enviar o actualizar la información, tanto en el registro de Terceros y Vehículos como en cada uno de los pasos del proceso.

Es fundamental entender la arquitectura del RNDC WEB-SERVICE ya que de esta forma para un desarrollador es posible comprender la estructura, el funcionamiento y la interacción entre las distintas partes de la aplicación.

Para el envío de información al RNDC se usa el método "AtenderMensajeRNDC". Asimismo, el único parámetro que se debe enviar en este método es "Request", el cual es una cadena en formato XML. El método envía una respuesta también en formato XML con el número de radicación o con el texto del error (o errores).

El "Request" del método "AtenderMensajeeRNDC" del Web Service del RNDC debe tener la siguiente estructura en XML:

```txt
Elemento principal <root> con cuatro elementos secundarios: <acceso>, <solicitud>, <variables> y <documento>. 
```

# A continuación, un ejemplo ilustrativo:

```txt
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
    <acceso>
    Seguridad del acceso.
    </acceso>
    <solicitud>
    Qué se desea hacer y en cual proceso.
    </solicitud>
    <variables>
    Detalle de la información que se envía.
    </variables>
    <documento>
    Datos para filtrar el documento del proceso a consultar. 
```

```txt
</documento>
</root> 
```

La respuesta que genera el Web-Service cuando los registros se han realizado satisfactoriamente lleva siempre el siguiente formato:

```xml
<?xml version="1.0" encoding="ISO-8859-1" ?>
<root>
<ingresoid>12</ingresoid>
</root> 
```

Aquí el número 12 es el consecutivo de radicado. El consecutivo cambia cada vez que se acepta un registro nuevo sin errores.

# 2. Elementos de la arquitectura del XML del Web Service

Los siguientes son los elementos de esta arquitectura, los cuales se revisarán uno.

# Elemento <acceso>

El elemento <acceso> contempla dos elementos: <username> y <password>.

<username>uuuuuu</username>, donde uuuuuu es el código del usuario de la empresa de transporte, generador de carga o empresa de GPS, entre otros actores de la cadena de transporte.

En el caso de <password>pppppp</password>, pppppp es la palabra clave del usuario.

# Elemento <solicitud>

El elemento <solicitud> contempla dos elementos:

En <tipo>x</tipo>, x es el tipo de operación:

1. Registrar Información en procesos y maestros.   
2. Consultar Registros de Maestros.   
3. Consultar Documentos o registros de cualquier proceso.   
4. Consulta para la Policía   
5. Consulta para Generadores de Carga   
6. Consulta de Maestros especiales   
7. Crear un usuario desde la app RNDC transportador   
8. Consulta de un conductor   
9. Consultas de remesas autorizadas para empresas de GPS

En <procesoid>xx</procesoid>, xx = Número del proceso, éste puede ser:

1: Registrar Información de Carga   
2: Registrar Información de Viaje   
3: Expedir Remesa Terrestre de Carga   
4: Expedir Manifiesto de Carga   
5: Cumplir Remesa Terrestre de Carga   
6: Cumplir Manifiesto de Carga   
7: Anular Información de Carga   
8: Anular Información del Viaje   
9: Anular Remesa Terrestre de Carga   
11: Crear o Actualizar datos de Tercero (Maestro)   
12: Crear o Actualizar datos de Vehículo (Maestro)

17: Diccionario de datos (Maestro)   
26: SiceTac   
27: Diccionario de errores (Maestro)   
28: Anular Cumplido de Remesa   
29: Anular Cumplido de Manifiesto   
32: Anular Manifiesto de Carga   
34: Tarifas o Fletes de Generador de carga   
38: Corregir Remesa   
39: Control en Carretera   
40: Puesto de control en carretera (Maestro)   
41: Anular flete de Generador   
45: Registrar un Cumplido Inicial de Remesa, puede ser empresa de GPS, o empresa de transporte.   
46: Registrar Novedades de Empresa de GPS   
48: Registro Nacional Automotor (Maestro)   
54: Anular Cumplido Inicial de Remesa   
41: Anular Flete del Generador de Carga   
73: Aceptación Electrónica del Manifiesto por parte del Titular del Manifiesto o del Conductor.   
75: Delegar Aceptación Electrónica del titular del manifiesto al Conductor.   
79: Cumplido de Viaje Municipal   
81: Registro de Viaje Municipal   
83: Remesa Municipal   
86: Factura Electrónica de transporte   
91: Anular Registros de Viaje Municipal   
92: Anular Remesa Municipal   
93: Anular Cumplido de Viaje Municipal

# Elemento <variables>

El elemento <variables> tiene n subelementos y depende del proceso al cual se desea enviar información. Cada elemento tiene como etiqueta el nombre de la variable del Diccionario de Datos, al cual se puede acceder en el portal del rndc.mintransporte.gov.co en la consulta de maestros.

# Elemento <documento>

El elemento <documento> solo se necesita cuando se quiere consultar información. Si se desea radicar o enviar información hacia los procesos del RNDC ese elemento no se usa.

Un ejemplo más detallado:   
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

# 3. Ambiente de pruebas

Las Empresas de Transporte pueden realizar sus pruebas del Web Service en otra IP. El WSDL lo pueden accesar en: http://plc.mintransporte.gov.co:8080/ws

Allí podrán accesar a una base de datos copia del ambiente de producción de alguna fecha. Los usuarios que la pueden usar son los mismos que tienen en el ambiente de producción, con sus respectivos password o claves.

Y si desean, pueden también accesar esa misma base de datos con el ayudante wstest: rndc.mintransporte.gov.co/wstest/defaultp.aspx

En el ambiente de pruebas, el sistema RNDC puede responder con números de radicados diferentes al orden de los consecutivos del ambiente de producción normal.

La base de datos de pruebas del RNDC cambia cada año por una nueva foto del ambiente de producción.

# 4. Usando paso a paso el Web Service

A continuación, se presentan algunos ejemplos comunes dentro del proceso del Web Service y las consideraciones generales para el registro de los Archivos Maestros (Terceros y Vehículos) y de cada uno de los pasos del proceso. Esto con el fin de ofrecer una mayor claridad acerca de los procesos, las herramientas y el lenguaje utilizado.

Para realizar un proceso rápido y sin interrupciones, se recomienda primero realizar el ingreso de la información de conductores, propietarios o tenedores de vehículos, empresas, personas naturales y vehículos, antes de realizar el proceso de registro de la información en el RNDC.

Solo se debe efectuar una vez el registro en el sistema. Luego de que éste se guarde en la base de datos, solo se necesita enviar el tipo de documento y el número de documento (terceros) o placa (vehículos), para que la información restante sea heredada automáticamente por el proceso que se está realizando.

Los Terceros y Vehículos se deben registrar únicamente cuando hay cambios en alguna información, de lo contrario se estaría almacenando una historia de cambios que no se necesita y ocupa mucho recurso de computación. El RNDC envía un mensaje de error cuando recibe un xml de creación de tercero o vehículo y la información coincide con la que ya está guardada en la base de datos.

# Ejemplo para crear un tercero sin licencia de conducción

En este caso, puede asumir el rol de Titular de Manifiesto, Propietario de Vehículo, Tenedor de Vehículo y Generador de Carga. Para el caso, se llamará a este tercero Linda Barreto Arévalo, identificada con cédula de ciudadanía No. 51.760.125 de Bogotá, quién reside en la Calle 156 # 9 - 50 en Bogotá, con número de teléfono 6753733.

# XML para el proceso solicitado:

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
<acceso>
<username>USUARIO1</username>
<password>CLAVE</password>
</acceso>
<solicitud> 
```

```xml
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

# Ejemplo para crear un vehículo

en este caso se trata de un Tractocamión de 3 ejes, marca Chevrolet, línea código 373, con placa WZH111, modelo 2010, que pertenece a Linda Barreto Arévalo, quien actúa como propietaria y tenedor; el vehículo funciona con ACPM, pesa 8000 kilogramos, el tipo de carrocería es S.R.S, la aseguradora es MAPFRE CREDISEGURO S.A. con NIT 8110191907, el número de póliza es AT131811151729 y vence el 14 de octubre del 2011.

# XML para el proceso solicitado:

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
<acceso>
<username>USUARIO1</username>
<password>CLAVE</password>
</acceso>
<solicitud> 
```

```xml
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

# Ejemplo para crear una Remesa Terrestre de Carga, con consecutivo 0001

La cantidad cargada es de 22,000 kilogramos. El tomador de la póliza de la carga número 15987462357 es la empresa de transporte. La póliza vence el 8 de Agosto del 2012. La Empresa Aseguradora es Royal y Sun Alliance Seguros (Colombia) S.A. La fecha del cargue es el 10 de agosto de 2011, con hora de llegada al cargue 8:00 a.m. Hora de inicio del cargue 8:15 a.m. y hora de salida del cargue 10:00am. Este formulario no tendrá recomendaciones.

XML para el proceso solicitado:   
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
<DESCRIPCIONCORTAPRODUCTO>TRIGO
BLANCO</DESCRIPCIONCORTAPRODUCTO>
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
<FECHAVENCIMIENTOPOLIZACARGA>01/01/2020</FECHAVENCIMIENTOPOLIZACARGA>
<HORASPACTOCARGA>4</HORASPACTOCARGA>
<MINUTOSPACTOCARGA>10</MINUTOSPACTOCARGA>
<HORASPACTODESCARGUE>3</HORASPACTODESCARGUE>
<MINUTOSPACTODESCARGUE>00</MINUTOSPACTODESCARGUE>
<CODTIPOIDPROPIETARIO>N</CODTIPOIDPROPIETARIO> 
```

```txt
<NUMIDPROPIETARIO>5765765</NUMIDPROPIETARIO>
<CODSEDEPROPIETARIO>3</CODSEDEPROPIETARIO>
<PERMISOCARGAEXTRA>566</PERMISOCARGAEXTRA>
<NUMIDGPS>5675756</NUMIDGPS>
</variables>
</root> 
```

# Ejemplo para crear un Manifiesto de Carga, con consecutivo 0001

El tipo de manifiesto es general, la fecha de expedición es 29 de julio de 2011, se transportará con origen Cali y destino Bogotá, el titular del Manifiesto de Carga es a nombre de Edgar Moreno Silva, identificado con cédula de ciudadanía No 79.616.565 de Bogotá. El descuento de ley es del 3 por mil, el valor del anticipo es de \$1.000.000, el saldo se pagará en la ciudad de Bogotá, el 29 de Julio del 2011. El encargado del pago del cargue y del descargue es la empresa de transporte. Se recomienda que en caso de accidente el conductor se comunique al número celular 3102569874. A este manifiesto están asociadas dos remesas con los consecutivos: 0001 y 0020.

# XML para el proceso solicitado:

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
<acceso>
<username>USUARIO1</username>
<password> USUARIO1</password>
</acceso>
<solicitud>
<tipo>1</tipo>
<procesoid>4</procesoid>
</solicitud>
<variables>
<NUMNITEMPRESATRANSPORTE>900301001</NUMNITEMPRESATRANSPORTE> 
```

```xml
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
<OBSERVACIONES>Se recomienda que en caso de accidente el conductor debe comunicarse al número celular
3102569871</OBSERVACIONES>
<REMESASMAN procesoid="43">
<REMESA>
<CONSECUTIVOREMESA>0001</ CONSECUTIVOREMESA >
</REMESA>
<REMESA>
< CONSECUTIVOREMESA >0020</ CONSECUTIVOREMESA >
</REMESA>
</REMESASMAN>
</variables>
</root> 
```

# 5. Consultas de información de los datos grabados previamente en el RNDC, usando Web Service

Las empresas de transporte pueden realizar consultas de cada uno de los procesos o registros de información enviada previamente. Para ello se usa el tipo de solicitud 3 en vez del 1, que es para enviar información.

A continuación, un ejemplo de la consulta de si un manifiesto ya fue firmado. Se usará el Web Service con el tipo: 3 "Consulta" del proceso 73, el cual corresponde a la firma o aceptación de manifiestos.

Ejemplo en Wstest del XML, con su respectiva respuesta:   
XML para el proceso solicitado   
```xml
<?xml version='1.0' encoding='ISO-8859-1' >>
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
INGRESOID,FECHAING,TIPO, CODIDCONDUCTOR, NUMIDCONDUCTOR,
CODIDTITULARMANIFIESTO, NUMIDTITULARMANIFIESTO, OBSERVACION
</variables>
<documento>
<NUMNITEMPRESATRANSPORTE>8999990554</NUMNITEMPRESATRANSPORTE>
<INGRESOIDMANIFIESTO>'46532952'<INGRESOIDMANIFIESTO>
</documento>
</root> 
```

# Consumir Servicio

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

La fecha y hora entregada en el tag: <fechaing> puede ser almacenada en la base de datos del sistema de información de la empresa de transporte, para que cuando realicen la generación del pdf del manifiesto aparezca en la ubicación de la firma electrónica.

Consulta de varias aprobaciones electrónicas en un rango de tiempo:   
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
INGRESOID,FECHAING, INGRESOIDMANIFIESTO,TIPO,
CODIDCONDUCTOR, NUMIDCONDUCTOR, OBSERVACION
</variables>
<documento>
<NUMNITEMPRESATRANSPORTE>8999990554</NUMNITEMPRESATRAN
SPORTE>
</documento>
<documentorango>
<iniFECHAING>'2020/01/01'<iniFECHAING>
<finFECHAING>'2020/03/31'<finFECHAING>
</documentorango>
</root> 
```  
Nos entrega la respuesta:

```xml
<?xml version="1.0" encoding="ISO-8859-1" ?>
<root>
<documento>
<ingresoid>15</ingresoid>
<fechaing>28/03/2020 9:44:52 a. m.</fechaing>
<ingresoidmanifiesto>48043700</ingresoidmanifiesto> 
```

```xml
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

# Si se desean consultar los manifiestos pendientes de Aceptación Electrónica, el XML sería:

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
<acceso> 
```

```xml
<username>xxxxxx@xxxx</username>
<password>xxxxxxxxxx</password>
</acceso>
<solicitud>
    <tipo>3</tipo>
    <procesoid>4</procesoid>
</solicitud>
<variables>
INGRESOID,FECHAING,NUMMANIFIESTOCARGA,NUMIDTITULARMANIFIE STO,NUMPLACA,NUMIDCONDUCTOR
</variables>
<documento>
<NUMNITEMPRESATRANSPORTE>8999990554</NUMNITEMPRESATRAN SPORTE>
<ACEPTACIONELECTRONICA>NULL</ACEPTACIONELECTRONICA>
</documento>
<documentorango>
    <iniFECHAING>'2020/04/01'<iniFECHAING>
    <finFECHAING>'2020/05/01'<finFECHAING>
</documentorango>
</root> 
```

# La respuesta de los manifiestos pendientes de aceptación electrónica sería:

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

# 6. Herramienta wstest para aprendizaje del Web Service del RNDC

El RNDC posee un programa que permite comprender bien la forma en que se debe escribir el XML.

Si el usuario empieza con el aprendizaje de la elaboración de los xml con esta herramienta, podrá realizar las pruebas de cada una de las operaciones a los procesos y comprender bien la forma en que se debe escribir el XML.

URL: https://rndc.mintransporte.gov.co/wstest/default.aspx
0

URL: https://rndc.mintransporte.gov.co/wstest/default2.aspx

La diferencia de las dos URL está en que la primera envía el Web Service al servidor: rndcws.mintransporte.gov.co:8080/....

Mientras la segunda envía el Web Service al servidor secundario: rndcws2.mintransporte.gov.co:8080/....

Existe una tercera URL

https://rndc.mintransporte.gov.co/wstest/default2.aspx la cual envía el

Web Service al servidor del ambiente de pruebas:

plc.mintransporte.gov.co:8080/....

La herramienta podrá buscarse desde distintos navegadores y al ingresar a la misma, se muestra una pantalla compuesta por 4 partes:

1. Lista de procesos del RNDC.   
2. Diccionario de datos del proceso seleccionado

3. XML que se genera automáticamente a partir del diccionario de datos y además es editable   
4. XML de respuesta del RNDC cuando recibe el Web Service

← → C rndc.mintransporte.gov.co/wstest/default.aspx

![](images/e07073baf1d2fca6dde7c5c42a3c07304c3327d6058854036e912c6e6b210c86.jpg)

Test Web Services RNDC: Procesos: 1-Información de Carga, 2-Información del Viaje, 3-Remesa, 4-Manifiesto, 5-CumplirRemesa, 6-Cumplir Manifiesto, 7-Anular Información de Carga, 8-Anular Viaje, 9-Anular Remesa, 11-Tercero, 12-Vehículo, 17-Diccionario de Datos, 26-SiceTAC, 27-Diccionario de Errores, 28-Anular Cumplido Remesa, 29-Anular Cumplido Manifiesto, 32-Anular Manifiesto, 38-Corregir Remesa, 34-Tarifas Generador, 39-Control en Carretera, 40-Puesto de Control en Carretera, 41-Anular Flete Generador, 45-Cumplido Inicial Remesa, 46-Novedades GPS, 48-RNA, 54-Anular Cumplido Inicial Remesa, 73-Aceptación Electrónica, 79-Cumplir Registro Urbano, 81-Viaje Urbano, 83-Remesa Urbana, 86-Factura Electronica, 91-Anular Viaje Urbano, 92-Anular Remesa Urbana, 93-Anular Cumplido Viaje Urbano

![](images/9d5804a20805223781122dfa3f4be7ff2536a404597130563836f3a64cbfbbf9.jpg)

<details>
<summary>text_image</summary>

Usuario: USUARIO1
Password: •••••••••
Proceso Id: □      Validar

□
?
□
?
□
?
□
?
□
?
□
?
□
?
□
?
□
?
□
?
</details>

![](images/e9ee22285eedda51fd4783a389ee99ee677fa37ea7bbb5c88cceced71e5ca17d.jpg)

<details>
<summary>text_image</summary>

XML para el proceso solicitado
Consumir Servicio
</details>

Como se observa en la figura, lo primero que se debe digitar es el usuario y la clave.

En la parte superior está la lista de los procesos que reciben Web Service en el RNDC: Número y nombre.

El número del proceso se debe digitar al lado izquierdo, en donde dice: Proceso ID.

Después de digitar el número del proceso, se hace clic en el botón "Validar" e inmediatamente se visualizará el diccionario de datos de ese proceso.

Por ejemplo, si se selecciona el 3-Remesa, se visualizará lo siguiente:

![](images/1f27a572a585df219fb780bf321236a74752644f5c39d327d6cc24d73b0afc6a.jpg)

<details>
<summary>text_image</summary>

Test Web Services RNDC: Procesos: 1-Información de Carga, 2-Información del Viaje, 3-Remesa, 4-Manifiesto, 5-CumplirRemesa, 6-Cumplir Manifiesto, 7-Anular Información de Carga, 8-Anular Viaje, 9-Anular Remesa, 11-Tercero, 12-Vehículo, 17-Diccionario de Datos, 26-SiceTAC, 27-Diccionario de Errores, 28-Anular Cumplido Remesa, 29-Anular Cumplido Manifiesto, 32-Anular Manifiesto, 38-Corregir Remesa, 34-Tarifas Generador, 39-Control en Carretera, 40-Puesto de Control en Carretera, 41-Anular Flete Generador, 45-Cumplido Inicial Remesa, 46-Novedades GPS, 48-RNA, 54-Anular Cumplido Inicial Remesa, 73-Aceptación Electrónica, 79-Cumplir Registro Urbano, 81-Viaje Urbano, 83-Remesa Urbana, 86-Factura Electronica, 91-Anular Viaje Urbano, 92-Anular Remesa Urbana, 93-Anular Cumplido Viaje Urbano
Username: USUARIO1
Password: ********
Proceso Id: 3 Validar REMESA
NUMNITEMPRESATRANSPORTE ?
CONSECUTIVOREMESA ?
CONSECUTIVOINFORMACIONCARGA ?
CONSECUTIVOCARGADIVIDIDA ?
CODOPERACIONTRANSPORTE ?
CODNATURALEZACARGA ?
CANTIDADCARGADA ?
UNIDADMEDIDACAPACIDAD ?
CODTIPOEMPAQUE ?
PESOCONTENEDORVACIO ?
MERCANCIAREMESA ?
XML para el proceso solicitado
Consumir Servicio
DESCRIPCIONCORTAPRODUCTO ?
CODTIPOIDREMITENTE ?
NUMIDREMITENTE ?
CODSEDEREMITENTE ?
CODTIPOIDDESTINATARIO ?
NUMIDDESTINATARIO ?
CODSEDEDESTINATARIO ?
DUENOPOLIZA ?
NUMPOLIZATRANSPORTE ?
COMPANIASEGURO ?
FECHAVENCIMIENTOPOLIZACARGA ?
HORASPACTOCARGA ?
MINUTOSPACTOCARGA ?
HORASPACTODESCARGUE ?
MINUTOSPACTODESCARGUE ?
FECHALLEGADACARGUE ?
HORALLEGADACARGUEREMESA ?
</details>

![](images/51bf6a13b87cb42b24711797613aad9e910552f4b7fcfac75f10ba751256a22e.jpg)

<details>
<summary>text_image</summary>

FECHAENTRADACARGUE
HORAENTRADACARGUEREMESA
FECHASALIDACARGUE
HORASALIDACARGUEREMESA
CODTIPOIDPROPIETARIO
NUMIDPROPIETARIO
CODSEDEPROPIETARIO
FECHACITAPACTADACARGUE
HORACITAPACTADACARGUE
FECHACITAPACTADADESCARGUE
HORACITAPACTADADESCARGUEREN
PERMISOCARGAEXTRA
NUMIDGPS
Generar XML para Grabar
Generar XML para Consultar
Fec.Inicio(yyyy/mm/dd):
Fec.Final(yyyy/mm/dd):
Para grabar valores alfanuméricos
NO deben llevar comillas sencillas
? check si desea consultar la variable. Entre
comillas sencillas los valores alfanuméricos
del filtro de la consulta, excepto el Nit de la
Empresa.
</details>

El usuario debe escribir los datos de cada variable del diccionario en los cajones de la derecha de cada uno.

Al terminar de diligenciar los datos, se debe hacer clic en el botón: Generar XML para grabar y el sistema mostrará a la derecha el XML que se debe enviar por el Web Service.

Se pueden dejar campos en blanco y el sistema no los incluirá en el XML.

![](images/59797ba79fc358a67303c98725131aa516b6394741fb74e84305b93c7ea51723.jpg)

<details>
<summary>text_image</summary>

Username: USUARIO1
Password: ••••••••
Proceso Id: 3     Validar         REMESA
NUMNITEMPRESATRANSPORTE    ? 8999990554
CONSECUTIVOREMESA    ? REM123
CONSECUTIVOINFORMACIONCARGI    ?
CONSECUTIVOCARGADIVIDIDA    ?
CODOPERACIONTRANSPORTE    ? G
CODNATURALEZACARGA    ? 1
CANTIDADCARGADA    ? 13500
UNIDADMEDIDACAPACIDAD    ? 1
CODTIPOEMPAQUE    ?
PESOCONTENEDORVACIO    ?
MERCANCIAREMESA    ? 000101
DESCRIPCIONCORTAPRODUCTO    ? VACAS
CODTIPOIDREMITENTE    ?
NUMIDREMITENTE    ?
CODSEDEREMITENTE    ?
XML para el proceso solicitado
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
<accesso>
<username>USUARIO1</username>
<password>PASSWORD1</password>
</accesso>
<solicitud>
<tipo>1</tipo>
<procesoid>3</procesoid>
</solicitud>
<variables>
<NUMNITEMPRESATRANSPORTE>8999990554</NUMNITEMPRESATRANSPORTE>
<CONSECUTIVOREMESA>REM123</CONSECUTIVOREMESA>
<CODOPERACIONTRANSPORTE>G</CODOPERACIONTRANSPORTE>
<CODNATURALEZACARGA>1</CODNATURALEZACARGA>
<CANTIDADCARGADA>13500</CANTIDADCARGADA>
<UNIDADMEDIDACAPACIDAD>1</UNIDADMEDIDACAPACIDAD>
<MERCANCIAREMESA>000101</MERCANCIAREMESA>
<DESCRIPCIONCORTAPRODUCTO>VACAS</DESCRIPCIONCORTAPRODUCTO>
</variables>
</root>
Consumir Servicio
</details>

Luego se debe hacer clic en el botón: Consumir Servicio.

El programa enviará el Web Service al servidor del RNDC y se visualizará la respuesta en un cuadro inferior, así como mensajes de error o el radicado de aceptación del registro.

![](images/3e86476dd978f450de690a9bda51852f787f1d1e133083c0285738c7a95ebc8f.jpg)

<details>
<summary>text_image</summary>

Username: USUARIO1
Password: ••••••••
Proceso Id: 3      Validar      REMESA
NUMNITEMPRESATRANSPORTE    ? 8999990554
CONSECUTIVOREMESA    ? REM123
CONSECUTIVOINFORMACIONCARG/    ?
CONSECUTIVOCARGADIVIDIDA    ?
CODOPERACIONTRANSPORTE    ? G
CODNATURALEZACARGA    ? 1
CANTIDADCARGADA    ? 13500
UNIDADMEDIDACAPACIDAD    ? 1
CODTIPOEMPAQUE    ?
PESOCONTENEDORVACIO    ?
MERCANCIAREMESA    ? 000101
DESCRIPCIONCORTAPRODUCTO    ? VACAS
CODTIPOIDREMITENTE    ?
NUMIDREMITENTE    ?
CODSEDEREMITENTE    ?
XML para el proceso solicitado
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
<acceso>
<username>JAIROVESGA@xxxx</username>
<password>xxxxxxxxx</password>
</acceso>
<solicitud>
<tipo>1</tipo>
<procesoid>3</procesoid>
</solicitud>
<variables>
<NUMNITEMPRESATRANSPORTE>8999990554</NUMNITEMPRESATRANSPORTE>
<CONSECUTIVOREMESA>REM123</CONSECUTIVOREMESA>
<CODOPERACIONTRANSPORTE>G</CODOPERACIONTRANSPORTE>
<CODNATURALEZACARGA>1</CODNATURALEZACARGA>
<CANTIDADCARGADA>13500</CANTIDADCARGADA>
<UNIDADMEDIDACAPACIDAD>1</UNIDADMEDIDACAPACIDAD>
<MERCANCIAREMESA>000101</MERCANCIAREMESA>
<DESCRIPCIONCORTAPRODUCTO>VACAS</DESCRIPCIONCORTAPRODUCTO>
</variables>
</root>
Consumir Servicio
<?xml version="1.0" encoding="ISO-8859-1" ?>
<root>
<ErrorMSG>Error REM019: La direccion del punto de cargue y la direccion del punto de descargue no pueden ser iguales
Error REM100: El código del tipo de empaque del producto no corresponde a los códigos establecidos.
Error REM132: El tipo de identificación del Propietario de la Carga no corresponde a los códigos establecidos. No se acepta campo en blanco.
Error REM135: El tipo y/o identificación del Propietario de la Carga no coinciden con los reportados en la tabla de Terceros. Está enviando una identificación del Propietario de la Carga de la Remesa Terrestre de Carga no válida o que no existe como Tercero en la base de datos.
Error REM140: El tipo de identificación del remitente no corresponde a los códigos establecidos. No se acepta campo en blanco.
Error REM150: El tipo y/o identificación del Remitente no coinciden con los
</details>

# 7. Diccionario de datos

Los usuarios pueden consultar el diccionario de datos para cada uno de los procesos. La consulta se debe hacer con la funcionalidad de CONSULTAR que se encuentra en el menú del portal rndc.mintransporte.gov.co

# Allí se debe seleccionar: Consultar Maestros

![](images/aec1ea7fb3559c1c11b012fd58d747457fd5ac2c3bb550555177a9e3c5d92a30.jpg)

<details>
<summary>text_image</summary>

mdc.mintransporte.gov.co/es-mx/menuprincipal.aspx
COLOMBIA
POTENCIA DE LA
VIDA
Transporte
RNDC
Registro Nacional
Despacho de Carga
Registrar
CONTROLADOR
Expedir
Cumplir
Reversar
Terceros Privados
Generador de Carga
Herramientas
Consultar Documentos
Consultar Documentos Pendientes de Cumplir
domingo, 25 de junio de 2023
Consultas Públicas
Antes de consultar cualquier Información, favor responder cuánto es 22 + 45
Empresas de Transporte Habilitadas por el Ministerio de Transporte
Consultar Empresas de Transp. Activas
Consultar Empresas de GPS
Consultas de Estadísticas RNDC desde Enero 2015.
Año Mes: 201501
Generar Archivo de estadísticas de las rutas y mercancías transportadas:
del Mes
del Año
Generar Archivo con los Tiempos Logísticos de cada viaje:
del Mes
Generar Archivo por Antigüedad de Vehículos y Combustible:
del Mes
del Año
soló Años 2020 y 2021
Consulta de Manifiestos de una Placa o Conductor
Placa Vehículo
Identificación
Conductor
Radicado
Manifiesto o
Viaje Urbano
Fecha Inicial
2023/06/10
Fecha Final
2023/06/25
Estado Matrícula/Licencia
SOAT/Licencia
RTM
Consultar Manifiestos
Generar PDF Consulta
Consultar Estado Place/Licencia
186.29.180.135
Consultar Manifiestos de una Placa o Conductor
Consultar Manifiestos de una Placa o Conductor
Consultar Manifiestos de una Placa o Conductor
Consultar Manifiestos de una Placa o Conductor
Consultar Manifiestos de una Placa o Conductor
Consultar Manifiestos de una Placa o Conductor
Consultar Manifiestos de una Placa o Conductor
Consultar Manifiestos de una Placa o Conductor
Consular Servicios - PQSD - Agendamiento videoLamada. Se podrá asignar una cita de acuerdo con la disponibilidad de la agenda, el horario de atención as de lunes a viernes de 07:00 a.m. a 05:00 p.m.
Consultar Registro Gestión del Riesgo
Consultar Manifiestos de una Placa/Cédula (VIGIA)
Información de Control del RNDC
Información Empresa
Control Solicitudes
Consultar Manifiestos SuperTransporte SiceTac
Consultar Cubos de Información
Registros de otras Entidades
Consultar Registro Gestión del Riesgo
yuda RNDC
SUBARIO
de 06:00 a.m. a 10:00 p.m.
00 a.m. a 12:00 m.
ectiórico
porta.gov.co
ano@mintransporte.gov.co
Canal Telefónico
Lihra (=601)240800 opción 2
Nivel nacional 018000 112042
Canal virtual
Rágina Web: www.mintransporta.gov.co opción servicio al ciudadano
radicar PQRS
Canal Presencial
Presia solicitud de cita a través de la página web del Ministerio de
Transporte. El horario de atención presencial será el de la sede
central.
Canal Video Llamada
Por medio de la página web www.mintransporta.gov.co a través de la
opción Servicios - PQSD - Agendamiento videoLamada. Se podrá
signar una cita de acuerdo con la disponibilidad de la agenda, el
horario de atención as de lunes a viernes de 07:00 a.m. a 05:00 p.m.
NOTICIAS
AGOSTO 12/2022
Desde las 11:00 a.m. y hasta las 18:30 p.m. del día de hoy no hubo servicio del RNDC, debido una falta
</details>

# Luego se debe seleccionar de la lista desplegable de los maestros el Diccionario de Datos

![](images/ec99ca2515c6daa9ea55a27f406bf74e7608f1c5d3060d2d41d598463b1c5d61.jpg)

<details>
<summary>text_image</summary>

mdc.mintransporte.gov.co/tabid/69/ctl/Maestros/mid/396//Default.aspx
COLOMBIA POTENCIA DE LA VIDA Transporte RNDC
Registro Nacional Despacho de Carga
Registrar CONTROLADOR Expedir Cumplir Reversar Terceros Privados Generador de Carga Horramientas Consultar Estadísticas Normatividad Documento
domingo, 25 de junio de 2023
Maestros
Máximo 50.000 registras
Maestro :
CAUSALES CANCELACION CITAS-TURNOS PUERTOS
Capítulos Codificación Productos
Codificación de Productos
Combinación de Configuraciones
Configuración Vehículos
Diccionario de Datos
Diccionario de Errores
División Política Administrativa
Empaques
Empresa Transportadora
Empresa Aseguradoras
Empresas Autorizados por Generadores
Generador
Lineas de Vehículos
Marcas Semiremolques
</details>

Se visualizará la pantalla que permite hacer la consulta de un solo mensaje de error. Asimismo, al dejar la casilla en blanco se visualizará una mayor información sobre distintos errores.

![](images/c7025b22bdfb917a4579e12b9a9e2904b899fee6d920f2f30d9c7ac079971e07.jpg)

COLOMBIA

POTENCIA DE LA

VIDA

![](images/86b00e50ad0e62698bc7e3bb97e963545d6adec1195f86bfeed214fe8046cbce.jpg)

Transporte

RNDC

Registro Nacional

Despacho de Carga

![](images/fea3c2cc0e10ea2145ca256c4212adc57e1aa2af4780a2e1be1290b270ea8bad.jpg)

Registrar

CONTROLADOR

Expedir

Cumplir

Reversar

Terceros Privados

Generador de Carga

Herramientas

Consultar

Estadisticas

Normativida

domingo, 25 de junio de 2023

# Maestros

Diccionario de Datos

Maestro : Diccionario de Datos

![](images/17f281ac0aefa8f85012bb1eab0be421b34d5c224cbeac424b685372ea600892.jpg)

Proceso ID

Consultar Registros

Máximo 50,000 registros

Registrar CONTROLADOR Expedir Cumplir Reversar Terceros Privados Generador de Carga Herramientas Consultar Estadísticas Normatividad Documentación Estado de las Vías

domingo, 25 de junio de 2023

jairo vesga

Salida Segura

# Maestro

Consultar otro Maestro   
Maestro: Diccionario de Datos 

<table><tr><td>Fecha Ingreso</td><td>Proceso ID</td><td>PROCESO</td><td>VARIABLE</td><td>TAMAÑO</td><td>TIPO DATO</td><td>Requerido</td><td>Descripción Variable</td><td>Validación</td><td>Etiqueta</td><td>Consecutivo</td><td>Web Service</td><td>Web Interactivo</td></tr><tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>2022/11/21 06:15:52</td><td>83</td><td>Remesa Municipal</td><td>CONSECUTIVOREMESA</td><td>15</td><td>Varchar</td><td>S</td><td>Consecutivo de la Remesa Municipal asignado por la empresa de transporte</td><td>El consecutivo de la Remesa Municipal debe ser único por Empresa de Transporte. No puede existir otra Remesa Municipal registrada con ese consecutivo.</td><td>Consecutivo</td><td>10</td><td>S</td><td>S</td></tr><tr><td>2022/10/31 16:38:16</td><td>4</td><td>Manifiesto de Carga</td><td>TIPOVALORPACTADO</td><td>1</td><td>Varchar</td><td>N</td><td>Tipo de pacto del valor a pagar pactado del manifiesto: V por Viaje, K por Kilogramo, G por Galón, Si no se digita el sistema asume por Viaje</td><td>Si el tipo de valor pactado no se digita el RNDC asume que es por Viaje</td><td>Tipo ValorPactado</td><td>81</td><td>S</td><td>N</td></tr><tr><td>2022/10/31 16:32:13</td><td>4</td><td>Manifiesto de Carga</td><td>VIAJESDIA</td><td>8</td><td>Numérico</td><td>N</td><td>Cantidad de viajes planeados para realizar en un día, en los manifiestos de tipo Varios Viajes en el Día</td><td>La cantidad de viajes no puede ser mayor a la cantidad de tiempo del día, dividido por la duración de 1 viaje</td><td>Viajes Día</td><td>81</td><td>S</td><td>N</td></tr><tr><td>2022/10/31 16:24:19</td><td>4</td><td>Manifiesto de Carga</td><td>CODMUNICIPIINTERMEDIO</td><td>8</td><td>Numérico</td><td>N</td><td>Código del municipio intermedio de los viajes de Ida y Regreso según archivo Anexo a los Manuales RNDC tabla División Política Administrativa</td><td>El código del municipio intermedio debe existir en archivo Anexo a los Manuales RNDC tabla División Política Administrativa.</td><td>Municipio Intermedio</td><td>81</td><td>S</td><td>N</td></tr><tr><td>2021/07/13 07:56:51</td><td>34</td><td>Tarifas Generador</td><td>CODIDEMPRESA</td><td>1</td><td>Varchar</td><td>S</td><td>Código de la identificación de la empresa</td><td>[WS] Tipo de identificación de la Empresa: [C]Cédula Ciudadanía, [N] NIT, [P] Pasaporte, [E] Cédula Extranjería, [T] Tarjeta Identidad o [U] NIJR</td><td>Cod. Tipo Identificación Empresa</td><td>18</td><td>S</td><td>S</td></tr><tr><td>2020/03/28 12:23:41</td><td>4</td><td>Manifiesto de Carga</td><td>ACEPTACIONELECTRONICA</td><td>2</td><td>Varchar</td><td>N</td><td>Aceptacion de la firma electronica para el manifiesto (SI/NO)</td><td>Un SI o un NO</td><td>Aceptacion Electrónica</td><td>0</td><td>S</td><td>S</td></tr><tr><td>2018/03/06 13:23:36</td><td>34</td><td>Tarifas Generador</td><td>VALORTARIFA</td><td>11</td><td>Numérico</td><td>S</td><td>Valor de la Tarifa</td><td>El valor de la tarifa es según el tipo de pacto realizado con la Empresa de Transporte</td><td>Valor Tarifa</td><td>17</td><td>S</td><td>S</td></tr><tr><td>2018/03/06 13:17:39</td><td>34</td><td>Tarifas Generador</td><td>RADICADOREMESA</td><td>9</td><td>Numérico</td><td>N</td><td>Número Radicado de la Remesa</td><td>El número del radicado de la Remesa debe haber sido entregado por el RNDC.</td><td>Número Radicado Remesa</td><td>16</td><td>S</td><td>S</td></tr><tr><td>2018/03/06 13:16:11</td><td>34</td><td>Tarifas Generador</td><td>CONSECUTIVOREMESA</td><td>15</td><td>Varchar</td><td>N</td><td>Número de la Remesa</td><td>El número de la Remesa debe haber sido expedido por una Empresa de Transporte</td><td>Número Remesa</td><td>15</td><td>S</td><td>S</td></tr></table>

El usuario puede filtrar los mensajes escribiendo el dato en la línea en blanco que está ubicada al principio de cada columna. Ver, por ejemplo, la columna Proceso ID, en la casilla en mención se agregó el número 8.

![](images/973a62a51c0aa613bc6834bac1d0bd25918845c9027450198672a9901f5a94d3.jpg)

<details>
<summary>text_image</summary>

Haestro
Consultar otro Maestro
Maestro: Diccionario de Datos
Fecha Ingreso	Proceso 1D	PROCESO	VARIABLE	TAMAÑO	TIPO DATO	Requerido	Descripción Variable	Valdación	Etiqueta	Consecutivo	Web Service	Web Interactivi
	8																																																																																																					N
2012/11/18
09:43:28
8 Anular
Información del
Viaje
2012/03/17
16:28:50
8 Anular
Información del
Viaje
2011/08/18
14:09:53
8 Anular
Información del
Viaje
2011/08/18
14:48:32
8 Anular
Información del
Viaje
2011/08/18
14:47:49
8 Anular
Información del
Viaje
CONSECUTIVO INFORMACION VIAJE
15 Varchar
5 Consecutivo de la Información de
Viaje a anulas.
Solo se pueden anular Informaciones de Viaje que no han
sido convertidas a Manifiestos de Carga y cuyas
Informaciones de Carga asociadas no han sido convertidas
en Remass Terrestres de Carga.
Información del
Viaje
20 S
5
Solo se pueden anular Informaciones de Viaje que no han
sido convertidas a Manifiestos de Carga y cuyas
Informaciones de Carga asociadas no han sido convertidas
en Remass Terrestres de Carga.
Información del
Viaje
10 N
5
</details>

El usuario puede hacer clic en el botón: Transmitir Archivo Plano y puede obtener la información en un archivo en formato Excel en su PC.

# 8. Diccionario de Errores

Los usuarios pueden consultar el diccionario de errores para cada uno de los procesos. La consulta se debe hacer con la funcionalidad de CONSULTAR del menú del portal rndc.mintransporte.gov.co

Allí se deberá seleccionar: Consultar Maestros.

![](images/eb95aaa64756be51aab46d5e4c62ea48f2960de81355e5ea9819464114de812e.jpg)

COLOMBIA POTENCIA DE LA VIDA

![](images/16ecf2908900acec839c29360a659a54c5fe068c40ff9aa27508462a1fb7c085.jpg)

Transporte

RNDC
Registro Nacional
Despacho de Carga

![](images/8dd7650e098f67ff346dc38b28b47580b40256915bdadb0ee831693419b01c2d.jpg)

![](images/dba825d2d17b6919c7f9da7f72f1db86207fa89f2705fb5c19c4194f5ec75ed2.jpg)

<details>
<summary>text_image</summary>

Registrar
CONTROLADOR
Expedir
Cumplir
Reversar
Terceros Privados
Generador de Carga
Herramientas
domingo, 25 de junio de 2023
Consultas Públicas
Antes de consultar cualquier información, favor responder cuanto es 22 + 45
Empresas de Transporte Habilitadas por el Ministerio de Transporte
Consultar Empresas de Transp. Activas
Consultar Empresas de GPS
Consultas de Estadísticas RNDC desde Enero 2015.
Año Mes: 201501
Generar Archivo de estadísticas de las rutas y mercancías transportadas:
del Mes
del Año
Generar Archivo con los Tiempos Logísticos de cada viaje:
del Mes
Generar Archivo por Antigüedad de Vehículos y Combustible:
del Mes
del Año
soló Años 2020 y 2021
Consulta de Manifiestos de una Placa o Conductor
Placa Vehículo
Identificación Conductor
Radicado Manifiesto o Viaje Urbano
Fecha Inicial
2023/06/10
Fecha Final
2023/06/25
Estado Matrícula/Licencia
SOAT/Licencia
RTM
Consultar Manifiestos
Generar PDF Consulta
Consultar Estado Placa/Licencia
Consultar Documentos
Consultar Documentos Pendientes de Cumplir
Consultar Manístro
Consultar Manifiestos de una Placa/Cédula (VIGIA)
Información de Control del RNDC
Información Empresa
Control Solicitudes
Consultar Manifiestos SuperTransporte SiceTac
Consultar Cubos de Información
Registros de otras Entidades
Consultar Registro Gestión del Riesgo
yuda RNDC
SUARIO
de 06:00 a.m. a 10:00 p.m.
30 a.m. a 12:00 m.
ectrónico
porta.gov.co
ano@mintransporte.gov.co
Canal Telefórico
Línea (-601)3240800 opción 2
Nivel nacional 018000 112042
Canal virtual
Página Web: www.mintransporta.govico opción servicio al ciudadano
radicar PQRS
Canal Presencial
Presiva solicitud de cita a través de la página web del Ministerio de
Transporte. El horario de atención presencial será el de la sede
central.
Canal Video Llamada
Por medio de la página web www.mintransporta.govico a través de la
opción Servicios - PQRD - Agendamiento video/Llamada. Se podrá
asignar una cita de acuerdo con la disponibilidad de la agenda el
horario de atención es de lunes a viernes de 07:00 a.m. a 05:00 p.m.
NOTICIAS
</details>

# AGOSTO 12/2022

Desde las 11:00 a.m. v hasta las 18:30 p.m. del día de hoy no hubo servicio del RNDC. debido una falla

# El paso a seguir será seleccionar de la lista desplegable de los maestros el Diccionario de Errores

rndc.mintransporte.gov.co/tabid/69/ctl/Maestros/mid/396//Default.aspx

![](images/9dcfd9a39243bfe86cf6b06691f9af9a898a95a1f6a0cb401337674632debcdc.jpg)

COLOMBIA POTENCIA DE LA VIDA

![](images/fa4d33b476d0530345f01203aa293c1c53374aecad126aa82e4d622b47311ee6.jpg)

Transporte

RNDC

Registro Nacional
Despacho de Carga

![](images/ae49f8b53f9e1f4207cb6a4e40c71789540c572171351719136e9c307de502e8.jpg)

Registrar CONTROLADOR Expedir Cumptir Reversar Terceros Privados Generador de Carga Herramientas Consultar Estadísticas Normatividad Documentación Estado de las Vías
doningo, 25 de junio de 2023

![](images/14fbfdf94ab990ddbbbfd2c9b1dc641d3339f226ead019bebda0e9f97878a3c0.jpg)

<details>
<summary>text_image</summary>

Maestros
Máximo 50.000 registros
Maestro :
CAUSALES CANCELACIÓN CITAS-TURNOS PUERTOS
Capítulos Codificación Productos
Codificación de Productos
Combinación de Configuraciones
Configuración Vehículos
Diccionario de Datos
Diccionario de Eroses
División Política Administrativa
Empaques
Empresa Transportadora
Empresas Aseguradoras
Empresas Autorizadas por Generadores
Generador
Líneas de Vehículos
Marcas Semiremolques
</details>

Se visualizará en la pantalla la opción que permite hacer la consulta del mensaje de error. Asimismo, al dejar la casilla en blanco se visualizará una mayor información sobre distintos errores.

![](images/383a25428630a0c81a264c03dc171e289f6e795b250c73837655474008ccd07e.jpg)

COLOMBIA

POTENCIA DE LA

VIDA

![](images/0230e63af5ec9c7a4ab016feb57d2fe749605be664d5968995416a5ed6867e2a.jpg)

# Transporte

RNDC

Registro Nacional

Despacho de Carga

![](images/d2d9279e7e29f191544675bb236bc818f63b3fc787a599491fb7cb28c68cdf32.jpg)

Registrar CONTROLADOR Expedir Cumplir Reversar Terceros Privados Generador de Carga Herramientas Consultar Estadísticas Normatividad

domingo, 25 de junio de 2023

# Maestros

Diccionario de Errores

Maestro : Diccionario de Errores

PROCESO ID

CODIGO ERROR

Consultar Registros

Máximo 50,000 registros

rndc.mintransporte.gov.co/ProgramasRNDC/CrearDocumento/tabid/69/ctl/Maestro/mid/396/language/es-MX/Default.aspx

![](images/7aa8a1a873ec68260a9a4fc33957372294ec18b299961f281f6c484e44dbdeed.jpg)

COLOMBIA

POTENCIA DE LA
VIDA

![](images/abefa86aebd4d2615f5136f537a8761b8ad5387e344023ccf4bf60475039d007.jpg)

# Transporte

RNDC

Registro Nacional

Despacho de Carga

![](images/7ebab25454265cec7c95f5206462bdf36135d36391f02318d5b1bf3ab01bd931.jpg)

Registrar CONTROLADOR Expedir Cumplir Reversar Terceros Privados Generador de Carga Herramientas Consultar

domingo, 25 de junio de 2023

# Maestro

Consultar otro Maestro 

<table><tr><td>Fecha Ingreso</td><td>PROCESO I</td><td>CODIGO ERR</td><td>MENSAJE ERROR</td><td>VARIABLE</td><td>TIPO ERRC</td><td>PROCESO</td><td>SOLUCION</td></tr><tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>2023/06/23 06:09:41</td><td>86</td><td>FAC006</td><td>El NUMNITEMPRESATRANSPORTE debe coincidir con el Nit del Proveedor en el xml de la DIAN</td><td>NUMNITEMPRESATRAN</td><td>E</td><td>Factura Electronica</td><td>Verificar el dato NUMNITEMPRESATRANSPORTE o NITFACTURADOR.</td></tr><tr><td>2023/06/23 05:53:54</td><td>86</td><td>FAC005</td><td>Falta el NUMNITEMPRESATRANSPORTE</td><td>NUMNITEMPRESATRAN</td><td>E</td><td>Factura Electronica</td><td>Verificar el dato NUMNITEMPRESATRANSPORTE o NITFACTURADOR.</td></tr><tr><td>2023/06/13 12:37:24</td><td>39</td><td>INFOR016</td><td>ESTADO_MATRICULA</td><td>NEMPLACA</td><td>I</td><td>Control en Carretera</td><td>Estado de la matricula</td></tr><tr><td>2023/06/07 21:24:20</td><td>5</td><td>CRE101</td><td>El manifiesto asociado a la remesa tiene una cita pendiente de cerrar en una terminal portuaria</td><td>CONSECUTIVOREMESA</td><td>E</td><td>Cumplir Remesa</td><td>Verificar con la terminal portuaria la causa del no cierre de la cita del manifiesto</td></tr><tr><td>2023/06/05 21:34:54</td><td>5</td><td>CRE322</td><td>La fecha y hora de la salida del descargue no puede ser futura</td><td>FECHASALIDADESCARG</td><td>E</td><td>Cumplir Remesa</td><td>Verificar la fecha y hora de la salida del descargue</td></tr><tr><td>2023/06/05 10:37:38</td><td>81</td><td>RTU370</td><td>El factor de retencion de ICA no pueda ser mayor al 20 por mil</td><td>FACTORICA</td><td>E</td><td>Viaje Urbano</td><td>Verificar el factor de retencion de ICA</td></tr><tr><td>2023/05/24 23:33:28</td><td>86</td><td>FAC020</td><td>El xml reportado no tiene un nit de generador o adquirente</td><td>ARCHIVOBASE64</td><td>E</td><td>Factura Electronica</td><td>Verificar el nit del adquirente o Generador en el xml</td></tr><tr><td>2023/05/24 23:30:23</td><td>86</td><td>FAC002</td><td>El usuario no existe</td><td>ARCHIVOBASE64</td><td>E</td><td>Factura Electronica</td><td>Verificar el usuario</td></tr><tr><td>2023/05/24 23:29:01</td><td>86</td><td>FAC004</td><td>La Empresa de transporte del usuario no coincide con el reportado en el xml</td><td>ARCHIVOBASE64</td><td>E</td><td>Factura Electronica</td><td>Verificar el nit de la Empresa de transporte</td></tr></table>

El usuario puede filtrar los mensajes escribiendo el dato en la línea en blanco que tiene al principio cada columna. Ver ejemplo en la columna PROCESO ID, en primera fila se agregó el número 93.

![](images/23766c6c0d8b19671eff5616a9f6b8e84d31454b8e1e9bc0f303fe8501c1ff3e.jpg)

<details>
<summary>text_image</summary>

mdc.mintransporte.gov.co/ProgramasRNDC/CrearDocumento/tabid/69/ctl/Maestro/mid/396/language/es-MX/Default.aspx
COLOMBIA POTENCIA DE LA VIDA
Transporte
RNDC
Registro Nacional Despacho de Carga
Registrar CONTROLADOR Expedir Cumplir Reversar Terceros Privados Generador de Carga Herramientas Consultar Estadísticas Normatividad Documentación Estado de las Vías
domingo, 25 de junio de 2023
Maestro
Consultar otro Maestro
Fecha Ingreso PROCESO I CODIGO ERR MENSAJE ERROR VARIABLE TIPO ERRC PROCESO SOLUCION
93
2021/06/24 93 ACU070 El consecutivo de viaje urbano no existe o no está cumplido CONSECUTIVOURBANC E Anular Cumplido Vaje Urbano Verificar el consecutivo de viaje urbano
2021/06/24 93 ACU020 Falta el consecutivo de viaje urbano CONSECUTIVOURBANC E Anular Cumplido Vaje Urbano Verificar el consecutivo de viaje urbano
2021/06/24 93 ACU040 El motivo de anulacion no es correcto, debe ser D, O MOTIVOANULACION E Anular Cumplido Vaje Urbano Verificar el motivo de anulacion D Digitación o O Otro
Transmitir Archivo Plano
Maestro: Diccionario de Errores
</details>

Finalmente, el usuario podrá hacer clic en el botón: Transmitir Archivo
Plano y obtener la información en un archivo en formato Excel en su PC.
