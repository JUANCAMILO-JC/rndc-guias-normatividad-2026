# Consulta de SICETAC desde RNDC

**Documento original:** Agosto 2021  
**Formato:** Markdown optimizado para RAG/LLM

---

# Introducción

La consulta de los valores de referencia de los costos eficientes del transporte de carga por carretera SICETAC se puede realizar desde:

- El webservice del RNDC
- El portal web interactivo del RNDC

El RNDC envía un mensaje de alerta a la empresa de transporte que registre en el manifiesto de carga un valor a pagar por debajo del SICETAC.

---

# Conceptos Básicos

El valor del SICETAC es un valor fijo para cada mes.

## Componentes

- Valor de movilización
- Valor de la hora
- Valor de la tonelada de movilización

## Fórmula

```text
Valor mínimo a pagar del viaje =
Valor movilización + (valorhora * horas pactadas de cargue, descargue y espera)
```

---

# URLs del Webservice

```text
Rndcws.mintransporte.gov.co:8080/ws
Rndcws2.mintransporte.gov.co:8080/ws
```

---

# XML Base de Consulta

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
NOMBREUNIDADTRANSPORTE,
NOMBRETIPOCARGA,
NOMBRERUTA,
VALOR,
VALORTONELADA,
VALORHORA,
DISTANCIA
</variables>

<documento>
    <PERIODO>'202108'</PERIODO>
    <CONFIGURACION>'3S3'</CONFIGURACION>
    <ORIGEN>'11001000'</ORIGEN>
    <DESTINO>'5001000'</DESTINO>
</documento>

</root>
```

---

# Variables Recomendadas

| Variable | Descripción |
|---|---|
| NombreUnidadTransporte | Tipo de unidad de transporte |
| NombreTipoCarga | Tipo de carga |
| NombreRuta | Nombre de la ruta |
| Valor | Costo de movilización |
| ValorTonelada | Costo por tonelada |
| ValorHora | Valor de tiempos logísticos |
| Distancia | Distancia de la ruta |

---

# Configuraciones Permitidas

```text
2
3
2S2
2S3
3S2
3S3
```

---

# Tipos de Carga Permitidos

- General
- Contenedor
- Carga Refrigerada

---

# Unidades de Transporte Permitidas

- ESTACAS
- TRAYLER
- TERMOKING

---

# Ejemplo de Error

```xml
<?xml version="1.0" encoding="ISO-8859-1" ?>

<root>
    <ErrorMSG>Error RNDC11: Documento no encontrado.</ErrorMSG>
</root>
```

---

# Portal Logístico de Colombia

```text
https://plc.mintransporte.gov.co
```

---

# TIPOVALORPACTADO

| Valor | Significado |
|---|---|
| K | Kilogramo |
| G | Galón |
| Viaje | Valor por viaje |

---

# Ejemplo XML con TIPOVALORPACTADO

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

---

# FIN
