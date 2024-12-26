---
title: Examen Final
date: 2024-12-26 00:20:00 -0500
categories: [Cybersecurity,Ethical Hacking,Pentesting,Exploitation Techniques]
tags: [Examen Final, evaluation]     # TAG names should always be lowercase
---
<!-- <hr style="border: none; height: 10px; background-color: #003b00;" />

# <font color="#87CEEB">Examen Parcial.</font>

<hr style="border: none; height: 10px; background-color: #003b00;" /> -->

## Preguntas

1. ¿Cómo podrías utilizar Procmon y Sysmon juntos para investigar la actividad de un proceso sospechoso? (5 ptos)

Antes de explicar como se podria utilizar Procmon y Sysmon se dará una breve concepto de ambos terminos.

-   **Procmon**: Cuya descripcion real es Process Monitor, es una herramienta avanzada de monitoreo de sistemas Windows que captura eventos en tiempo real relacionados con la Actividad del Sistema de Archivos y los registros de windows. Como indica Mark R. en su libro Windows Internals, Procmon es una herramienta de monitoreo de eventos del sistema el cual captura actividades en tiempo real del kernel.

    _[https://learn.microsoft.com/en-us/sysinternals/downloads/procmon](https://hcisj.com/data/file/article/2023080005/13-39.pdf)_

-   **Sysmon**:  Cuya descripcion real es Sistema Monitor, es una herramienta avanzada de monitoreo de eventos de Windows desarrollada por Microsoft Sysinternals para Registrar eventos de sistema en profundidad, Capturar actividades críticas de seguridad, Proporcionar logs detallados para análisis forense.

    _[https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon](https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon)_

-   Explica los tipos de eventos que Procmon y Sysmon pueden capturar de forma complementaria.

| Year  | Attack Name                | Target/System Affected                                    |
|-------|----------------------------|-----------------------------------------------------------|
| 2010  | Stuxnet Worm               | Iranian Nuclear CPS                                       |
| 2015  | BlackEnergy Malware        | Ukrainian Power Grid                                      |
| 2016  | CrashOverride Malware      | Ukrainian Power Grid                                      |
| 2017  | Triton Malware             | Petrochemical plant in Saudi Arabia                       |
| 2017  | NotPetya Ransomware        | Cyber-physical systems of Maersk and Merck                |
| 2021  | Oldsmar APT                | Chemical levels in the water plant supply (US)            |
| 2021  | Colonial Pipeline Ransomware | Fuel pipelines in the US                                |
| 2021  | Water Sector Attacks       | Chemical levels in water treatment facilities (US)        |
| 2021  | Iranian Railway System Attack | Iran's railway system                                  |


_M. Russinovich, D. Solomon, and A. Ionescu, "Windows Internals, Part 1: User Mode and System Architecture, Developer Reference," 7th ed. Redmond, WA, USA: Microsoft Press, 2017._


-   Proporciona un ejemplo práctico de cómo identificar un posible comportamiento malicioso en un proceso utilizando ambas herramientas.

2. En Sysmon, ¿qué diferencias existen entre los eventos `ProcessCreate` y `ProcessAccess`, y qué utilidad tienen cada uno para un analista de seguridad? (5 ptos)

    - Describe los atributos principales de ambos eventos.
    - Investiga y menciona al menos dos escenarios donde cada evento podría ser clave en la detección de amenazas.

3. En Procmon, ¿qué operación(es) corresponde(n) al evento `FileCreateStreamHash` en Sysmon, y cómo podrías configurarlo en Sysmon para detectar un posible uso malicioso de Alternate Data Streams (ADS)? (5 ptos)

    - Investiga qué son los Alternate Data Streams y por qué podrían ser usados por atacantes.

    - Especifica qué operaciones de Procmon están relacionadas con este tipo de actividad.

4. En Sysmon, ¿qué ventajas ofrece el uso de filtros avanzados en comparación con capturar todos los eventos de forma indiscriminada? (5 ptos)

    - Investiga cómo un mal diseño de filtros podría afectar el desempeño del sistema y la calidad de los logs.

    - Proporciona un ejemplo de un filtro efectivo para reducir ruido en un entorno de producción.