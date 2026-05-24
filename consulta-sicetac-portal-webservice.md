---
title: "Consulta de SiceTac desde RNDC"
source: "Consulta de SiceTac desde webservice y portal web_compressed(1).pdf"
date_converted: "2026-05-24"
total_sections: 8
---

# Consulta de SiceTac desde RNDC

**Documento original:** Agosto 2021

## Tabla de Contenido

- [Introducción](#introducción)
- [Conceptos Generales del SICETAC](#conceptos-generales-del-sicetac)
- [Consulta desde el Portal Web](#consulta-desde-el-portal-web)
- [Consulta desde Webservice SOAP](#consulta-desde-webservice-soap)
- [Ejemplo General de Consulta XML](#ejemplo-general-de-consulta-xml)
- [Consultas Filtradas](#consultas-filtradas)
- [Manejo de Errores](#manejo-de-errores)
- [Portal Logístico de Colombia](#portal-logístico-de-colombia)
- [TipoValorPactado](#tipovalorpactado)

---

## Introducción

La consulta de los valores de referencia de los costos eficientes del transporte de carga por carretera SICETAC se puede realizar desde el webservice del RNDC y desde el portal web interactivo del RNDC.

El RNDC envía un mensaje de alerta a la empresa de transporte que registre en el manifiesto de carga un valor a pagar por debajo del SiceTac.

### Modalidades

- Para el caso de los de webservice
- Para los del portal WEB interactivo

---

## Conceptos Generales del SICETAC

El valor del SiceTac es un valor fijo para cada mes, por lo tanto el primer parámetro que debe tener en cuenta la empresa de transporte cuando hace la consulta es el AñoMes o Periodo.

### Componentes del valor SICETAC

El valor del SiceTac está compuesto por tres datos importantes:

- Valor de movilización
- Valor de la hora
- Valor de la tonelada de movilización

### Fórmula del valor mínimo del viaje

Valor mínimo a pagar del viaje =

```text
Valor movilización + (valorhora * horas pactadas de cargue, descargue y de espera)
```

---

## Consulta desde el Portal Web

Desde el portal web interactivo se debe entrar al menú de:

```text
Consultas – Consultar Maestros
```

Después seleccionar el Maestro SiceTac.

Luego se debe escribir el periodo.

Y aparece el resultado, el cual se puede descargar a Excel si desea el usuario.

---

## Consulta desde Webservice SOAP

La tecnología del webservice es SOAP.

### URLs WSDL

```text
Rndcws.mintransporte.gov.co:8080/ws
Rndcws2.mintransporte.gov.co:8080/ws
```

La estructura del XML está compuesta por un grupo `<variables>` y un grupo `<documento>`.

---

## Ejemplo General de Consulta XML

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
<acceso>
 <username>xxxx</username>
 <password>xxxx</password>
</acceso>
<solicitud>
 <tipo>2</tipo>
 <procesoid>26</procesoid>
</solicitud>
<variables>
NOMBREUNIDADTRANSPORTE, NOMBRETIPOCARGA, NOMBRERUTA, VALOR, VALORTONELADA, VALORHORA, DISTANCIA
</variables>
<documento>
 <PERIODO>'202108'</PERIODO>
 <CONFIGURACION>'3S3'</CONFIGURACION>
 <ORIGEN>'11001000'</ORIGEN>
 <DESTINO>'5001000'</DESTINO>
</documento>
</root>
```

### Variables sugeridas

- NombreUnidadTransporte
- NombreTipoCarga
- NombreRuta
- Valor
- ValorTonelada
- ValorHora
- Distancia

### Definiciones

- `Valor` = Costo de Movilización de la carga en una ruta y una configuración.
- `ValorTonelada` = Costo de Movilización de la Tonelada en esa ruta.

### Etiquetas obligatorias del grupo `<documento>`

| Etiqueta | Descripción |
|---|---|
| PERIODO | AñoMes (yyyymm) |
| CONFIGURACION | 2, 3, 2S2, 2S3, 3S2, 3S3 |
| ORIGEN | Código divipola de 8 dígitos. Los últimos tres deben ser 000 |
| DESTINO | Código divipola de 8 dígitos. Los últimos tres deben ser 000 |

> Todos los datos deben escribirse entre comillas sencillas.

### Ejemplo Completo

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
<acceso>
 <username>JAIROVESGA@xxxx</username>
 <password>xxxxxxxx</password>
</acceso>
<solicitud>
 <tipo>2</tipo>
 <procesoid>26</procesoid>
</solicitud>
<variables>
RUTA, NOMBREUNIDADTRANSPORTE, NOMBRETIPOCARGA, NOMBRERUTA, VALOR, VALORTONELADA, VALORHORA, DISTANCIA
</variables>
<documento>
 <PERIODO>'202108'</PERIODO>
 <CONFIGURACION>'3S3'</CONFIGURACION>
 <ORIGEN>'11001000'</ORIGEN>
 <DESTINO>'5001000'</DESTINO>
</documento>
</root>
```

### Respuesta XML

```xml
<?xml version="1.0" encoding="ISO-8859-1" ?>
<root>
<documento>
<ruta>106</ruta>
<nombreunidadtransporte>TERMOKING</nombreunidadtransporte>
<nombretipocarga>Carga Refrigerada</nombretipocarga>
<nombreruta>BOGOTÁ _ MEDELLÍN</nombreruta>
<valor>2693308.96</valor>
<valortonelada>79214.97</valortonelada>
<valorhora>55118</valorhora>
<distancia>416</distancia>
</documento>

<documento>
<ruta>106</ruta>
<nombreunidadtransporte>ESTACAS</nombreunidadtransporte>
<nombretipocarga>Granel Sólido</nombretipocarga>
<nombreruta>BOGOTÁ _ MEDELLÍN</nombreruta>
<valor>2441830.65</valor>
<valortonelada>71818.55</valortonelada>
<valorhora>38566.03</valorhora>
<distancia>416</distancia>
</documento>

<documento>
<ruta>106</ruta>
<nombreunidadtransporte>ESTACAS</nombreunidadtransporte>
<nombretipocarga>General</nombretipocarga>
<nombreruta>BOGOTÁ _ MEDELLÍN</nombreruta>
<valor>2478949.67</valor>
<valortonelada>72910.28</valortonelada>
<valorhora>37926.89</valorhora>
<distancia>416</distancia>
</documento>

<documento>
<ruta>106</ruta>
<nombreunidadtransporte>TRAYLER</nombreunidadtransporte>
<nombretipocarga>Contenedor</nombretipocarga>
<nombreruta>BOGOTÁ _ MEDELLÍN</nombreruta>
<valor>2478949.67</valor>
<valortonelada>72910.28</valortonelada>
<valorhora>37926.89</valorhora>
<distancia>416</distancia>
</documento>
</root>
```

---

## Consultas Filtradas

### Consulta por Unidad de Transporte: ESTACAS

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
<acceso>
 <username>JAIROVESGA@1715</username>
 <password>098754321</password>
</acceso>
<solicitud>
 <tipo>2</tipo>
 <procesoid>26</procesoid>
</solicitud>
<variables>
NOMBRETIPOCARGA, NOMBRERUTA, VALOR, VALORTONELADA, VALORHORA, DISTANCIA
</variables>
<documento>
 <PERIODO>'202108'</PERIODO>
 <CONFIGURACION>'3S3'</CONFIGURACION>
 <ORIGEN>'11001000'</ORIGEN>
 <DESTINO>'5001000'</DESTINO>
 <NOMBREUNIDADTRANSPORTE>'ESTACAS'</NOMBREUNIDADTRANSPORTE>
</documento>
</root>
```

### Respuesta

```xml
<?xml version="1.0" encoding="ISO-8859-1" ?>
<root>
<documento>
 <nombretipocarga>Granel Sólido</nombretipocarga>
 <nombreruta>BOGOTÁ _ MEDELLÍN</nombreruta>
 <valor>2441830.65</valor>
 <valortonelada>71818.55</valortonelada>
 <valorhora>38566.03</valorhora>
 <distancia>416</distancia>
</documento>

<documento>
 <nombretipocarga>General</nombretipocarga>
 <nombreruta>BOGOTÁ _ MEDELLÍN</nombreruta>
 <valor>2478949.67</valor>
 <valortonelada>72910.28</valortonelada>
 <valorhora>37926.89</valorhora>
 <distancia>416</distancia>
</documento>
</root>
```

### Consulta por Tipo de Carga y Unidad

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
<acceso>
 <username>JAIROVESGA@xxxx</username>
 <password>xxxxxx</password>
</acceso>
<solicitud>
 <tipo>2</tipo>
 <procesoid>26</procesoid>
</solicitud>
<variables>
 NOMBRERUTA, VALOR, VALORTONELADA, VALORHORA, DISTANCIA
</variables>
<documento>
 <PERIODO>'202108'</PERIODO>
 <CONFIGURACION>'3S3'</CONFIGURACION>
 <ORIGEN>'11001000'</ORIGEN>
 <DESTINO>'5001000'</DESTINO>
 <NOMBREUNIDADTRANSPORTE>'ESTACAS'</NOMBREUNIDADTRANSPORTE>
 <NOMBRETIPOCARGA>'General'</NOMBRETIPOCARGA>
</documento>
</root>
```

### Respuesta

```xml
<?xml version="1.0" encoding="ISO-8859-1" ?>
<root>
<documento>
<nombreruta>BOGOTÁ _ MEDELLÍN</nombreruta>
<valor>2478949.67</valor>
<valortonelada>72910.28</valortonelada>
<valorhora>37926.89</valorhora>
<distancia>416</distancia>
</documento>
</root>
```

### Valores permitidos para `nombretipocarga`

- General (Los de granel sólido se incluyen en el mismo de General)
- Contenedor
- Carga Refrigerada

### Valores permitidos para `nombreunidadtransporte`

- ESTACAS (los de Furgón se incluyen en el mismo de estacas)
- TRAYLER (los tractocamiones con semirremolque)
- TERMOKING (los que llevan carga refrigerada)

---

## Manejo de Errores

Si se realiza la consulta de una configuración que no tiene el SiceTac aparece en la respuesta el mensaje de error:

```text
Documento no encontrado
```

### Ejemplo consultando configuración inválida 3S1

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
<acceso>
 <username>JAIROVESGA@1715</username>
 <password>09854321</password>
</acceso>
<solicitud>
 <tipo>2</tipo>
 <procesoid>26</procesoid>
</solicitud>
<variables>
 NOMBRETIPOCARGA,NOMBRERUTA,VALOR,VALORTONELADA,VALORHORA,DISTANCIA
</variables>
<documento>
 <PERIODO>'202108'</PERIODO>
 <CONFIGURACION>'3S1'</CONFIGURACION>
 <ORIGEN>'11001000'</ORIGEN>
 <DESTINO>'5001000'</DESTINO>
 <NOMBREUNIDADTRANSPORTE>'ESTACAS'</NOMBREUNIDADTRANSPORTE>
 <NOMBRETIPOCARGA>'General'</NOMBRETIPOCARGA>
</documento>
</root>
```

### Respuesta de Error

```xml
<?xml version="1.0" encoding="ISO-8859-1" ?>
<root>
<ErrorMSG>Error RNDC11: Documento no encontrado. </ErrorMSG>
</root>
```

---

## Portal Logístico de Colombia

Si las empresas desean ver el detalle de los valores consultados previamente, éstas se pueden realizar en el Portal Logístico de Colombia.

```text
https://plc.mintransporte.gov.co
```

Se da click a la funcionalidad SICETAC y se digitan los parámetros.

La consulta muestra los detalles.

---

## TipoValorPactado

Si las Empresas de Transporte pactan con el generador de Carga un valor que depende de las toneladas o galones transportados, y así mismo, lo hacen con el tercero vinculado que les prestará el servicio, pueden notificar al RNDC, al momento de registrar el manifiesto, que el valor pactado es por: Kilogramo o por Galón.

Si la empresa de transporte no envía ese dato, el RNDC asume que el valor pactado es por Viaje.

Cuando el RNDC recibe esa variable llamada `TIPOVALORPACTADO` con una `K` (que significa kilogramo), realiza la multiplicación de la cantidad transportada por el valor de la tonelada de movilización del SiceTac dividido por 1000, luego le suma el valor de los tiempos de espera y ese resultado será el valor del viaje a comparar con el valor pactado del manifiesto.

A continuación se muestra la pantalla que recibe la información de un manifiesto y se observa a la derecha del valor pactado, el nuevo campo:

```text
TipoValorPactado
```

### Ejemplo XML

```xml
<?xml version='1.0' encoding='ISO-8859-1' ?>
<root>
<acceso>
 <username>USUARIO1</username>
 <password>PASSWORD1</password>
</acceso>
<solicitud>
 <tipo>1</tipo>
 <procesoid>4</procesoid>
</solicitud>
<variables>
 <NUMNITEMPRESATRANSPORTE>8999990554</NUMNITEMPRESATRANSPORTE>
 <NUMMANIFIESTOCARGA>4564</NUMMANIFIESTOCARGA>
 <VALORFLETEPACTADOVIAJE>3560000</VALORFLETEPACTADOVIAJE>
 <TIPOVALORPACTADO>K</TIPOVALORPACTADO>
 <REMESASMAN procesoid="43">
 </REMESASMAN>
</variables>
</root>
```

------- FIN ----------
