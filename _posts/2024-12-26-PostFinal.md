---
title: Examen Final
date: 2024-12-26 00:20:00 -0500
categories: [Cybersecurity,Ethical Hacking,Pentesting,Exploitation Techniques]
tags: [Examen Final, evaluation]     # TAG names should always be lowercase
---


## Preguntas

1. ¿Cómo podrías utilizar Procmon y Sysmon juntos para investigar la actividad de un proceso sospechoso? (5 ptos)

    - Explica los tipos de eventos que Procmon y Sysmon pueden capturar de forma complementaria.

    - Proporciona un ejemplo práctico de cómo identificar un posible comportamiento malicioso en un proceso utilizando ambas herramientas.

2. En Sysmon, ¿qué diferencias existen entre los eventos `ProcessCreate` y `ProcessAccess`, y qué utilidad tienen cada uno para un analista de seguridad? (5 ptos)

    - Describe los atributos principales de ambos eventos.
    - Investiga y menciona al menos dos escenarios donde cada evento podría ser clave en la detección de amenazas.

3. En Procmon, ¿qué operación(es) corresponde(n) al evento `FileCreateStreamHash` en Sysmon, y cómo podrías configurarlo en Sysmon para detectar un posible uso malicioso de Alternate Data Streams (ADS)? (5 ptos)

    - Investiga qué son los Alternate Data Streams y por qué podrían ser usados por atacantes.

    - Especifica qué operaciones de Procmon están relacionadas con este tipo de actividad.

4. En Sysmon, ¿qué ventajas ofrece el uso de filtros avanzados en comparación con capturar todos los eventos de forma indiscriminada? (5 ptos)

    - Investiga cómo un mal diseño de filtros podría afectar el desempeño del sistema y la calidad de los logs.

    - Proporciona un ejemplo de un filtro efectivo para reducir ruido en un entorno de producción.