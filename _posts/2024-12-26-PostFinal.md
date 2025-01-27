---
title: Examen Final
date: 2024-12-26 00:20:00 -0500
categories: [Cybersecurity,Ethical Hacking,Pentesting,Exploitation Techniques]
tags: [Examen Final, evaluation]     # TAG names should always be lowercase
---
<!-- <hr style="border: none; height: 10px; background-color: #003b00;" />

# <font color="#87CEEB">Examen Parcial.</font>

<hr style="border: none; height: 10px; background-color: #003b00;" /> -->

<style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
            text-align: justify;
        }
        .flowchart {
            background-color: white;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            padding: 20px;
            width: 90%;
            max-width: 800px;
        }
        .step {
            border: 2px solid #3498db;
            border-radius: 5px;
            padding: 10px;
            margin: 10px 0;
            text-align: center;
            background-color: #e6f2ff;
        }
        .arrow {
            text-align: center;
            font-size: 24px;
            color: #2ecc71;
        }
    </style>
## Preguntas

### 1. ¿Cómo podrías utilizar Procmon y Sysmon juntos para investigar la actividad de un proceso sospechoso? (5 ptos)

Antes de explicar como se podria utilizar Procmon y Sysmon se dará una breve concepto de ambos terminos.

-   **Procmon**: Cuya descripcion real es Process Monitor, es una herramienta avanzada de monitoreo de sistemas Windows que captura eventos en tiempo real relacionados con la Actividad del Sistema de Archivos y los registros de windows. Como indica Mark R.[1] en su libro Windows Internals, Procmon es una herramienta de monitoreo de eventos del sistema el cual captura actividades en tiempo real del kernel.

    _[https://learn.microsoft.com/en-us/sysinternals/downloads/procmon](https://hcisj.com/data/file/article/2023080005/13-39.pdf)_

-   **Sysmon**:  Cuya descripcion real es Sistema Monitor, es una herramienta avanzada de monitoreo de eventos de Windows desarrollada por Microsoft Sysinternals para Registrar eventos de sistema en profundidad, Capturar actividades críticas de seguridad, Proporcionar logs detallados para análisis forense.

    _[https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon](https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon)_

    Para investigar y analizar un proceso potencialmente malicioso, es recomendable emplear de forma conjunta las herramientas Process Monitor (Procmon) y System Monitor (Sysmon). Estas aplicaciones, al utilizarse de manera complementaria, permiten obtener un panorama integral y detallado sobre las operaciones del sistema y el comportamiento de los distintos procesos, mejorando significativamente el análisis de seguridad.

#### -   Explica los tipos de eventos que Procmon y Sysmon pueden capturar de forma complementaria.

<table>
	<thead>
		<tr>
			<th>Process Monitor Procmon</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Creación y terminación de procesos</td>
			<td>Procmon puede capturar eventos relacionados con la creación y finalización de procesos, lo que permite ver cuando un proceso sospechoso se inicia o se detiene.</td>
		</tr>
		<tr>
			<td>Acceso a archivos y registros</td>
			<td>Captura operaciones de lectura y escritura en archivos y claves del registro, lo que ayuda a identificar cambios en la configuración del sistema o la creación de archivos maliciosos.</td>
		</tr>
		<tr>
			<td>Conexiones de red</td>
			<td>Procmon puede mostrar intentos de conexión de red, lo que es crucial para identificar comunicaciones no autorizadas.</td>
		</tr>
	</tbody>
</table>

<table>
	<thead>
		<tr>
			<th>System Monitor (Sysmon)</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Monitoreo detallado de procesos</td>
			<td>Esta herramienta registra la iniciación de procesos, ofreciendo información enriquecida que incluye los comandos específicos empleados para su lanzamiento.</td>
		</tr>
		<tr>
			<td>Supervisión de comunicaciones de red</td>
			<td>Sysmon captura y documenta las conexiones de red establecidas por diferentes procesos, proporcionando una visión clara de las comunicaciones del sistema.</td>
		</tr>
		<tr>
			<td>Seguimiento de modificaciones de archivos</td>
			<td>La aplicación realiza un registro exhaustivo de las transformaciones en los archivos, permitiendo identificar creaciones, alteraciones o eliminaciones que pueden ser indicativas de actividad maliciosa.</td>
		</tr>
	</tbody>
</table>

_M. Russinovich, D. Solomon, and A. Ionescu, "Windows Internals, Part 1: User Mode and System Architecture, Developer Reference," 7th ed. Redmond, WA, USA: Microsoft Press, 2017._


#### -   Proporciona un ejemplo práctico de cómo identificar un posible comportamiento malicioso en un proceso utilizando ambas herramientas.

En un escenario de investigación de seguridad, la identificación de comportamiento malicioso requiere una estrategia meticulosa utilizando Process Monitor y System Monitor de manera complementaria. El proceso comienza configurando filtros específicos en ambas herramientas para capturar eventos relevantes del proceso sospechoso, seguido de un monitoreo detallado que implica ejecutar el proceso y analizar minuciosamente sus interacciones con el sistema. Durante la evaluación, se examinan aspectos críticos como el acceso a archivos del sistema, modificaciones del registro, líneas de comandos inusuales, creación de procesos y conexiones de red. La combinación de datos de Procmon y Sysmon permite construir un perfil comprehensivo que revela potenciales indicadores de actividad maliciosa, como el acceso a ubicaciones de sistema no habituales, establecimiento de conexiones a dominios desconocidos o ejecución de procesos mediante comandos sospechosos. Esta metodología proporciona a los analistas de seguridad una perspectiva integral que facilita la detección temprana de amenazas y permite una respuesta rápida y efectiva ante posibles incidentes de seguridad.

  <div class="flowchart">
        <div class="step">Configuración de Herramientas
            <ul>
                <li>Configurar filtros en Procmon</li>
                <li>Configurar registros en Sysmon</li>
            </ul>
        </div>
        <div class="arrow">↓</div>
        <div class="step">Monitoreo de Proceso Sospechoso
            <ul>
                <li>Ejecutar proceso</li>
                <li>Capturar eventos en Procmon</li>
                <li>Capturar eventos en Sysmon</li>
            </ul>
        </div>
        <div class="arrow">↓</div>
        <div class="step">Análisis de Eventos
            <ul>
                <li>Revisar acceso a archivos</li>
                <li>Verificar modificaciones de registro</li>
                <li>Analizar conexiones de red</li>
                <li>Examinar líneas de comandos</li>
            </ul>
        </div>
        <div class="arrow">↓</div>
        <div class="step">Evaluación de Comportamiento
            <ul>
                <li>Identificar actividades sospechosas</li>
                <li>Correlacionar eventos de Procmon y Sysmon</li>
                <li>Detectar posibles indicadores de amenaza</li>
            </ul>
        </div>
        <div class="arrow">↓</div>
        <div class="step">Conclusión
            <ul>
                <li>Generar perfil de comportamiento</li>
                <li>Determinar nivel de riesgo</li>
                <li>Planificar respuesta de seguridad</li>
            </ul>
        </div>
    </div>

### 2. En Sysmon, ¿qué diferencias existen entre los eventos `ProcessCreate` y `ProcessAccess`, y qué utilidad tienen cada uno para un analista de seguridad? (5 ptos)

 En el contexto de la monitorización de seguridad con Sysmon, los eventos de creación `ProcessCreate` y acceso a procesos `ProcessAccess` representan herramientas esenciales para comprender la dinámica de ejecución de programas en un entorno informático. Estos eventos ofrecen una perspectiva detallada sobre las interacciones y el comportamiento de los procesos, permitiendo a los analistas de seguridad identificar patrones sospechosos y potenciales vectores de amenaza. La distinción entre los eventos de creación y acceso de procesos resulta crucial para realizar un análisis exhaustivo de la actividad del sistema, proporcionando información valiosa que puede revelar intentos de compromiso o actividades maliciosas.

*Diferencias entre ProcessCreate y ProcessAccess*
<table>
        <thead>
            <tr>
                <th>Tipo de Evento</th>
                <th>Descripción</th>
                <th>Utilidad</th>
                <th>Características Principales</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>ProcessCreate</td>
                <td>Registro de iniciación de un nuevo proceso en el sistema</td>
                <td>Rastrear el origen y condiciones de ejecución de procesos</td>
                <td>
                    <ul>
                        <li>Documenta el inicio del proceso</li>
                        <li>Captura parámetros de ejecución</li>
                        <li>Permite identificar ejecuciones potencialmente maliciosas</li>
                    </ul>
                </td>
            </tr>
            <tr>
                <td>ProcessAccess</td>
                <td>Evento que registra las interacciones entre procesos</td>
                <td>Detectar comportamientos sospechosos de comunicación entre programas</td>
                <td>
                    <ul>
                        <li>Monitorea accesos entre procesos</li>
                        <li>Identifica manipulaciones de memoria</li>
                        <li>Revela intentos de interacción no autorizados</li>
                    </ul>
                </td>
            </tr>
        </tbody>
</table>

#### - Describe los atributos principales de ambos eventos.

<table>
        <thead>
            <tr>
                <th>Tipo de Evento</th>
                <th>Atributos</th>
                <th>Descripción</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td rowspan="7">ProcessCreate (Event ID: 1)</td>
                <td>Image</td>
                <td>Ruta del ejecutable del proceso creado</td>
            </tr>
            <tr>
                <td>CommandLine</td>
                <td>Línea de comandos utilizada para iniciar el proceso</td>
            </tr>
            <tr>
                <td>User</td>
                <td>Usuario que inició el proceso</td>
            </tr>
            <tr>
                <td>ParentImage</td>
                <td>Ruta del ejecutable del proceso padre que creó el nuevo proceso</td>
            </tr>
            <tr>
                <td>ProcessId</td>
                <td>ID del nuevo proceso</td>
            </tr>
            <tr>
                <td>ThreadId</td>
                <td>ID del hilo que creó el proceso</td>
            </tr>
            <tr>
                <td>Event ID</td>
                <td>1 (Identificador de evento de creación de proceso)</td>
            </tr>
            <tr>
                <td rowspan="6">ProcessAccess (Event ID: 10)</td>
                <td>TargetImage</td>
                <td>Ruta del ejecutable del proceso al que se accede</td>
            </tr>
            <tr>
                <td>TargetProcessId</td>
                <td>ID del proceso objetivo</td>
            </tr>
            <tr>
                <td>SourceImage</td>
                <td>Ruta del ejecutable del proceso que realiza el acceso</td>
            </tr>
            <tr>
                <td>SourceProcessId</td>
                <td>ID del proceso que realiza el acceso</td>
            </tr>
            <tr>
                <td>AccessMask</td>
                <td>Máscara de acceso que define los permisos o tipo de operación</td>
            </tr>
            <tr>
                <td>Event ID</td>
                <td>10 (Identificador de evento de acceso a proceso)</td>
            </tr>
        </tbody>
</table>

#### - Investiga y menciona al menos dos escenarios donde cada evento podría ser clave en la detección de amenazas.

**A. Escenarios de Alerta en ProcessCreate:**<br>
*Detección de Código Malicioso:* El análisis de eventos de creación de procesos permite identificar ejecuciones sospechosas cuando se detectan programas iniciándose desde ubicaciones no convencionales o con configuraciones de línea de comandos inusuales, lo que podría revelar la presencia de software malicioso.<br>
*Mecanismos de Persistencia:* La identificación de procesos que se autoinician durante el arranque del sistema representa un indicador crítico para comprender las estrategias de permanencia utilizadas por atacantes, como la implementación de servicios ocultos o tareas programadas maliciosas.<br>
**B. Escenarios de Riesgo en ProcessAccess:**<br>
*Manipulación de Procesos:* La observación de accesos anómalos entre procesos, especialmente cuando programas legítimos intentan interactuar con sistemas de seguridad o procesos críticos, puede señalar intentos de inyección de código o manipulación del entorno de ejecución.<br>
*Exfiltración de Datos Sensibles:* Los eventos que revelan accesos de procesos desconocidos a aplicaciones de gestión de credenciales o navegadores web representan señales de alerta sobre potenciales intentos de extracción de información confidencial.

### 3. En Procmon, ¿qué operación(es) corresponde(n) al evento `FileCreateStreamHash` en Sysmon, y cómo podrías configurarlo en Sysmon para detectar un posible uso malicioso de Alternate Data Streams (ADS)? (5 ptos)

#### - Investiga qué son los Alternate Data Streams y por qué podrían ser usados por atacantes.

**Alternate Data Streams (ADS): Mecanismo de Ocultación Digital**<br>
*Fundamentos de los ADS en NTFS*
En la arquitectura del sistema de archivos NTFS, los archivos poseen una estructura de almacenamiento compleja que va más allá del flujo de datos principal. Los Alternate Data Streams representan flujos de información secundarios que pueden anexarse a un archivo sin modificar su apariencia externa, constituyendo un mecanismo de ocultamiento digital sofisticado.

**Motivaciones de los Atacantes para Usar ADS**<br>
*a. Estrategias de Ocultamiento*
- Camuflaje de Malware: Incrustación de ejecutables maliciosos en flujos ocultos de archivos aparentemente legítimos.<br>
- Técnicas de Persistencia: Almacenamiento de scripts y configuraciones que se activan automáticamente.<br>
- Exfiltración Encubierta: Almacenamiento temporal de datos robados en espacios invisibles.<br>

*b. Ventajas Técnicas*
- Invisibilidad para herramientas convencionales
- Evasión de mecanismos tradicionales de detección
- Difícil rastreo por soluciones de seguridad estándar<br>

**Estructura y Sintaxis de ADS**<br>
*Formato de Identificación*
- Sintaxis: nombre_archivo:nombre_stream<br>
- Ejemplo: documento.txt:codigo<br>

**Tipos de Streams Comunes**
- :$DATA: Flujo de datos predeterminado<br>
- :Zone.Identifier: Metadatos de origen del archivo

#### - Especifica qué operaciones de Procmon están relacionadas con este tipo de actividad.

*Identificación de Interacciones Potencialmente Maliciosas:*

Las operaciones del sistema que involucran manipulación de archivos con estructura de flujos alternativos (nombre_archivo:stream) pueden ser indicadores cruciales de comportamientos anómalos o intentos de ocultamiento digital[5]. Tres operaciones fundamentales merecen especial atención:

*Operaciones Críticas de Archivo*<br>

a. WriteFile<br>
- Escritura en flujos alternativos
- Potencial introducción de contenido oculto
- Mecanismo de inserción de datos maliciosos<br>

b. SetInformationFile<br>
- Modificación de metadatos de archivo
- Alteración de propiedades de flujos
- Posible reconfiguración encubierta<br>

c. CreateFile<br>
- Generación de nuevos flujos de datos
- Creación de estructuras de almacenamiento alternativo
- Punto de entrada para técnicas de ocultamiento

### 4. En Sysmon, ¿qué ventajas ofrece el uso de filtros avanzados en comparación con capturar todos los eventos de forma indiscriminada? (5 ptos)

Beneficios de los Filtros Avanzados en Sysmon
Estrategias de Monitoreo Inteligente
Los filtros avanzados en Sysmon representan una aproximación selectiva y estratégica para la captura de eventos del sistema, ofreciendo múltiples ventajas operativas:

a. Depuración Inteligente de Información
Concepto: Eliminación de eventos irrelevantes
Beneficio: Simplificación de la detección de actividades críticas y potencialmente sospechosas
b. Optimización de Recursos Computacionales
Impacto: Reducción de la carga del sistema
Resultado: Mejora del rendimiento y eficiencia en el análisis de eventos
c. Focalización del Análisis de Seguridad
Método: Concentración en eventos significativos
Ventaja: Aceleración en la identificación y respuesta a incidentes de seguridad
d. Gestión Económica de Almacenamiento
Consecuencia: Minimización de registros
Beneficio: Reducción de costos de almacenamiento y procesamiento
e. Personalización de la Detección de Amenazas
Enfoque: Adaptación a las particularidades del entorno organizacional
Resultado: Incremento de la efectividad de las medidas de seguridad

*Conclusión*
Los filtros avanzados en Sysmon no son simplemente una herramienta técnica, sino una estrategia inteligente de monitoreo que permite una gestión más eficiente, selectiva y enfocada de los eventos del sistema.

#### - Investiga cómo un mal diseño de filtros podría afectar el desempeño del sistema y la calidad de los logs.

La configuración inadecuada de filtros en sistemas de monitoreo puede generar consecuencias críticas para la infraestructura de seguridad. Un diseño deficiente provoca una sobrecarga computacional significativa, saturando los recursos del sistema con la captura excesiva de eventos, lo que deteriora el rendimiento y complejiza la gestión de información de seguridad. Esta saturación informativa dificulta la identificación de eventos realmente relevantes, consumiendo recursos valiosos y aumentando exponencialmente el tiempo de análisis.

Los riesgos se profundizan cuando los filtros son demasiado restrictivos, generando vulnerabilidades por omisión de eventos críticos. La pérdida de visibilidad sobre actividades potencialmente maliciosas puede crear puntos ciegos en la detección temprana de amenazas, comprometiendo la capacidad de respuesta y prevención. Esta limitación no solo afecta la eficacia del monitoreo, sino que también puede representar un riesgo significativo para la integridad de los sistemas.

El impacto trasciende lo técnico, afectando directamente el cumplimiento normativo y los procesos de auditoría. La degradación en la calidad de los registros puede generar complicaciones legales y dificultar la trazabilidad de incidentes, poniendo en riesgo la conformidad con estándares de seguridad. Por ello, es fundamental implementar filtros inteligentes que mantengan un equilibrio óptimo entre la reducción de ruido informático y la preservación de una cobertura comprehensiva de monitoreo.

#### - Proporciona un ejemplo de un filtro efectivo para reducir ruido en un entorno de producción.

````bash
<Sysmon schemaversion="4.80">
  <EventFiltering>
    <!-- Excluir procesos de sistema rutinarios -->
    <ProcessCreate onmatch="exclude">
      <Image condition="contains">\\Windows\\System32\</Image>
      <Image condition="contains">\\Program Files\\</Image>
      <ParentImage condition="contains">\\Windows\\explorer.exe</ParentImage>
    </ProcessCreate>

    <!-- Monitorear procesos críticos -->
    <ProcessCreate onmatch="include">
      <Image condition="contains">powershell.exe</Image>
      <Image condition="contains">cmd.exe</Image>
      <Image condition="contains">wscript.exe</Image>
      <Image condition="contains">cscript.exe</Image>
    </ProcessCreate>

    <!-- Alertar sobre ejecuciones desde ubicaciones sospechosas -->
    <ProcessCreate onmatch="include">
      <Image condition="contains">C:\Users\Public\</Image>
      <Image condition="contains">C:\Temp\</Image>
      <Image condition="contains">C:\Windows\Temp\</Image>
    </ProcessCreate>
  </EventFiltering>
</Sysmon>
````

### Referencias
*[1] M. Russinovich, “Process Monitor,” Microsoft Docs, 2023. [Online]. Available: https://learn.microsoft.com/en-us/sysinternals/downloads/procmon*

*[2] Sysinternals, “Sysmon Documentation,” Microsoft Docs, 2023. [Online]. Available: https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon*

*[3] Huang, Y. T., Guo, Y. R., Wong, G. W., & Chen, M. C. 2024. A Cascade Approach for APT Campaign Attribution in System Event Logs: Technique Hunting and Subgraph Matching. arXiv preprint arXiv:2410.22602.*

*[4] Breed, J., Baker, P., Chu, K. D., Starr, C., Fox, J., & Baitinger, M. 2000. The spacecraft emergency response system (SERS) for autonomous mission operations. Reducing the Cost of Spacecraft Ground Systems and Operations, 2021*

*[5] K. Harris, “Monitoring NTFS Streams with Procmon,” Forensic Analysis Weekly, 2023.*