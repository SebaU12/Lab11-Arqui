# Spotty — Requerimientos utilizados y priorización

**Base documental:** `rf.md` (Spotty v3) y `rnf.md` (Spotty v4).

**Propósito:** presentar la lista completa de requisitos empleados en el diseño de los 16 servicios y clasificarlos en **Must Have** y **Nice to Have**. La priorización se acordó durante el diseño; no altera el texto original de los requisitos.

## Resumen de priorización

| Tipo | Must Have | Nice to Have | Total |
|---|---:|---:|---:|
| Funcionales (RF) | 46 | 4 | 50 |
| No funcionales (RNF) | 34 | 4 | 38 |
| **Total** | **80** | **8** | **88** |

## Requerimientos funcionales — matriz de trazabilidad

| ID | Requerimiento | Prioridad | Servicio(s) principal(es) |
|---|---|---|---|
| RF-001 | Inicio de sesión institucional | **Must Have** | Access Service |
| RF-002 | Autorización por rol y curso | **Must Have** | Access / Course Service |
| RF-003 | Gestión de cursos | **Must Have** | Course Service |
| RF-004 | Vinculación de estudiantes | **Must Have** | Course Service |
| RF-005 | Creación de actividades | **Must Have** | Activity Service |
| RF-006 | Configuración de rúbricas | **Must Have** | Activity Service |
| RF-007 | Consulta de actividades | **Must Have** | Activity Service |
| RF-008 | Edición de actividades y recalificación | **Must Have** | Activity / Evaluation Orchestrator Service |
| RF-009 | Registro de entrega GitHub | **Must Have** | Submission Service |
| RF-010 | Reentrega y versión vigente | **Must Have** | Submission / Evaluation Orchestrator Service |
| RF-011 | Consulta de historial de entregas | **Nice to Have** | Submission Service |
| RF-012 | Solicitud asíncrona de evaluación | **Must Have** | Submission / Evaluation Orchestrator Service |
| RF-013 | Clasificación CPU y GPU | **Must Have** | Evaluation Scheduler Service |
| RF-014 | Priorización de evaluaciones | **Must Have** | Evaluation Scheduler Service |
| RF-015 | Ejecución de Programación | **Must Have** | Execution Service |
| RF-016 | Ejecución de Arquitectura | **Must Have** | Execution Service |
| RF-017 | Ejecución de Inteligencia Artificial | **Must Have** | Execution Service |
| RF-018 | Preparación de sandbox | **Must Have** | Execution Service |
| RF-019 | Control de límites de ejecución | **Must Have** | Execution Service |
| RF-020 | Persistencia de checkpoints | **Must Have** | Checkpoint / Execution Service |
| RF-021 | Detección de workers perdidos | **Must Have** | Evaluation Orchestrator / Spot Capacity Service |
| RF-022 | Recuperación de ejecuciones | **Must Have** | Evaluation Orchestrator / Checkpoint Service |
| RF-023 | Transiciones atómicas e intentos vigentes | **Must Have** | Evaluation Orchestrator Service |
| RF-024 | Resultados técnicos | **Must Have** | Execution / Evaluation Orchestrator Service |
| RF-025 | Cálculo automático de nota provisional | **Must Have** | Grading Service |
| RF-026 | Revisión docente de excepciones | **Must Have** | Grade Review Service |
| RF-027 | Publicación docente de calificaciones | **Must Have** | Grade Review Service |
| RF-028 | Conservación de notas y recalificaciones | **Must Have** | Grade Review Service |
| RF-029 | Consulta de estados de evaluación | **Must Have** | Evaluation Orchestrator Service |
| RF-030 | Notificaciones de eventos relevantes | **Must Have** | Notification Service |
| RF-031 | Monitoreo de cola y capacidad | **Must Have** | Evaluation Scheduler / Spot Capacity Service |
| RF-032 | Alertas por plazo académico | **Must Have** | Notification / Evaluation Scheduler Service |
| RF-033 | Solicitud de ajuste de capacidad | **Must Have** | Spot Capacity Service |
| RF-034 | Chat docente para crear actividades | **Must Have** | Activity Chat Service |
| RF-035 | Generación asistida de tarea y evaluación | **Must Have** | Activity Chat / LLM Access Service |
| RF-036 | Validación y aplicación docente de la propuesta | **Must Have** | Activity / Activity Chat Service |
| RF-037 | Gestión de presupuestos del LLM | **Must Have** | Token Budget / LLM Access Service |
| RF-038 | Reserva y conciliación del consumo de tokens | **Must Have** | Token Budget / LLM Access Service |
| RF-039 | Persistencia de presupuestos entre reintentos | **Must Have** | Token Budget Service |
| RF-040 | Manejo del agotamiento de tokens | **Nice to Have** | Token Budget Service |
| RF-041 | Registro de evidencia de confianza | **Must Have** | Execution / Grading Service |
| RF-042 | Cálculo de confidence level | **Must Have** | Grading Service |
| RF-043 | Visualización docente de nota y confianza | **Must Have** | Grading / Grade Review Service |
| RF-044 | Trazabilidad de uso del LLM y del skill | **Nice to Have** | LLM Access Service |
| RF-045 | Configuración y seguimiento de cuotas | **Nice to Have** | Token Budget Service |
| RF-046 | Compatibilidad con contratos legacy | **Must Have** | Legacy Compatibility Service |
| RF-047 | Acceso y preservación de información histórica legacy | **Must Have** | Legacy Compatibility Service |
| RF-048 | Coexistencia operativa entre legacy y Spotty | **Must Have** | Legacy Compatibility Service |
| RF-049 | Control de responsabilidad y consistencia de datos durante la transición | **Must Have** | Legacy Compatibility Service |
| RF-050 | Transición progresiva y reversión controlada | **Must Have** | Legacy Compatibility Service |

## Requerimientos no funcionales — matriz de priorización

| ID | Requerimiento | Prioridad |
|---|---|---|
| RNF-001 | Seguridad y aislamiento | **Must Have** |
| RNF-002 | Autorización académica | **Must Have** |
| RNF-003 | Protección de credenciales | **Must Have** |
| RNF-004 | Perfiles de ejecución | **Must Have** |
| RNF-005 | Carga en deadline | **Must Have** |
| RNF-006 | Escalabilidad diferenciada | **Must Have** |
| RNF-007 | Disponibilidad de la plataforma | **Must Have** |
| RNF-008 | Alta disponibilidad de persistencia | **Must Have** |
| RNF-009 | Confiabilidad ante interrupción Spot | **Must Have** |
| RNF-010 | Ventana de aviso de AWS Spot | **Must Have** |
| RNF-011 | Consistencia e idempotencia | **Must Have** |
| RNF-012 | Límites de ejecución | **Must Have** |
| RNF-013 | Eficiencia de imágenes | **Must Have** |
| RNF-014 | Cumplimiento de plazo | **Must Have** |
| RNF-015 | Trazabilidad de evaluación | **Must Have** |
| RNF-016 | Trazabilidad de notas | **Must Have** |
| RNF-017 | Disponibilidad de API | **Must Have** |
| RNF-018 | Degradación parcial | **Must Have** |
| RNF-019 | Observabilidad | **Must Have** |
| RNF-020 | Modularidad | **Must Have** |
| RNF-021 | Usabilidad | **Nice to Have** |
| RNF-022 | Capacidad mínima deseada | **Must Have** |
| RNF-023 | Compatibilidad de GPU | **Must Have** |
| RNF-024 | Límites finitos de tokens | **Must Have** |
| RNF-025 | Aislamiento de presupuestos | **Must Have** |
| RNF-026 | Durabilidad y no reinicio de consumo | **Must Have** |
| RNF-027 | Protección frente a respuestas no confiables del proveedor | **Must Have** |
| RNF-028 | Privilegios mínimos para integración LLM | **Must Have** |
| RNF-029 | Degradación ante indisponibilidad o cuota agotada | **Must Have** |
| RNF-030 | Explicabilidad del confidence level | **Must Have** |
| RNF-031 | Separación entre confianza y calificación | **Must Have** |
| RNF-032 | Trazabilidad del proveedor y del skill | **Nice to Have** |
| RNF-033 | Observabilidad y control de costos | **Nice to Have** |
| RNF-034 | Límites configurables y verificables | **Nice to Have** |
| RNF-035 | Compatibilidad retroactiva de contratos | **Must Have** |
| RNF-036 | Integridad y trazabilidad de información migrada | **Must Have** |
| RNF-037 | Continuidad operativa durante la transición | **Must Have** |
| RNF-038 | Reversibilidad y recuperación controlada de la migración | **Must Have** |

## Alcance de los Nice to Have

- **RF-011:** la pantalla de historial de entregas es opcional; mantener la última versión válida y el historial interno necesario **es obligatorio**.
- **RF-040:** el flujo avanzado de manejo de agotamiento es opcional; denegar llamadas sin presupuesto y evitar notas arbitrarias **es obligatorio**.
- **RF-044:** auditoría extendida de prompts y uso del skill opcional; reserva y conciliación mínima de tokens **obligatoria**.
- **RF-045:** configuración y monitoreo avanzado de cuotas opcional; límites predefinidos y control de consumo **obligatorios**.
- **RNF-021:** optimizaciones de usabilidad opcionales; las interfaces básicas necesarias siguen dentro del alcance funcional.
- **RNF-032, RNF-033 y RNF-034:** trazabilidad, métricas de costos y configurabilidad LLM avanzadas opcionales; seguridad, cuotas fijas, contabilidad y telemetría mínima **obligatorias**.

## Texto de referencia — requerimientos funcionales

> Se conserva la redacción de `rf.md`; las etiquetas de prioridad son añadidas para este entregable.

### RF-001 — Inicio de sesión institucional

**Prioridad:** Must Have · **Servicio(s):** Access Service

**Usuarios:** Estudiante / Profesor

   El sistema deberá:
   * Autenticar a los usuarios mediante el proveedor de identidad institucional.
   * Permitir cerrar sesión.
   * No almacenar contraseñas institucionales como credenciales propias.

### RF-002 — Autorización por rol y curso

**Prioridad:** Must Have · **Servicio(s):** Access / Course Service

**Usuarios:** Estudiante / Profesor

   El sistema deberá:
   * Determinar rol y cursos autorizados.
   * Restringir lecturas y modificaciones de actividades, entregas y notas según permisos.

### RF-003 — Gestión de cursos

**Prioridad:** Must Have · **Servicio(s):** Course Service

**Usuarios:** Profesor

   El sistema deberá:
   * Crear y consultar cursos autorizados.
   * Modificar los datos administrables de dichos cursos.

### RF-004 — Vinculación de estudiantes

**Prioridad:** Must Have · **Servicio(s):** Course Service

**Usuarios:** Profesor / Estudiante

   El sistema deberá:
   * Vincular o desvincular estudiantes de un curso por acción docente.
   * Permitir al estudiante consultar solo sus cursos vinculados.

### RF-005 — Creación de actividades

**Prioridad:** Must Have · **Servicio(s):** Activity Service

**Usuarios:** Profesor

   El sistema deberá:
   * Crear actividades con instrucciones, modalidad y fecha límite.
   * Presentarlas a los estudiantes vinculados.

### RF-006 — Configuración de rúbricas

**Prioridad:** Must Have · **Servicio(s):** Activity Service

**Usuarios:** Profesor

   El sistema deberá:
   * Definir criterios, reglas, matices y puntajes de evaluación.
   * Asociar una versión identificable de rúbrica a cada actividad y evaluación.

### RF-007 — Consulta de actividades

**Prioridad:** Must Have · **Servicio(s):** Activity Service

**Usuarios:** Estudiante / Profesor

   El sistema deberá:
   * Consultar tareas, instrucciones, deadline y rúbrica publicada de cursos autorizados.

### RF-008 — Edición de actividades y recalificación

**Prioridad:** Must Have · **Servicio(s):** Activity / Evaluation Orchestrator Service

**Usuarios:** Profesor

   El sistema deberá:
   * Permitir cambios en actividades o rúbricas.
   * Conservar versiones y generar nuevas evaluaciones para las entregas afectadas.

### RF-009 — Registro de entrega GitHub

**Prioridad:** Must Have · **Servicio(s):** Submission Service

**Usuarios:** Estudiante

   El sistema deberá:
   * Recibir el enlace de GitHub de la tarea.
   * Resolver y registrar commit SHA, actividad, alumno y hora de recepción del servidor.
   * Confirmar aceptación o informar cuando no pueda registrarse válidamente.

### RF-010 — Reentrega y versión vigente

**Prioridad:** Must Have · **Servicio(s):** Submission / Evaluation Orchestrator Service

**Usuarios:** Estudiante

   El sistema deberá:
   * Permitir reentregas antes del deadline.
   * Definir como vigente la última entrega válida aunque su nota sea menor.
   * Invalidar evaluaciones pendientes obsoletas e intentar cancelar las que ya corren.

### RF-011 — Consulta de historial de entregas

**Prioridad:** Nice to Have · **Servicio(s):** Submission Service

**Usuarios:** Estudiante / Profesor

   El sistema deberá:
   * Mostrar versiones y estados de entregas autorizadas.
   * Identificar la entrega vigente.

### RF-012 — Solicitud asíncrona de evaluación

**Prioridad:** Must Have · **Servicio(s):** Submission / Evaluation Orchestrator Service

**Usuarios:** Estudiante / Worker

   El sistema deberá:
   * Generar solicitud de evaluación al aceptar una entrega.
   * Confirmar recepción independientemente de la disponibilidad inmediata de un worker.

### RF-013 — Clasificación CPU y GPU

**Prioridad:** Must Have · **Servicio(s):** Evaluation Scheduler Service

**Usuarios:** Worker

   El sistema deberá:
   * Dirigir Programación y Arquitectura a la cola CPU.
   * Dirigir IA a la cola GPU.

### RF-014 — Priorización de evaluaciones

**Prioridad:** Must Have · **Servicio(s):** Evaluation Scheduler Service

**Usuarios:** Worker / Profesor

   El sistema deberá:
   * Ordenar trabajo según el deadline de la actividad y la urgencia de publicación.
   * Aplicar reparto justo entre cursos.
   * Dar preferencia razonable a reanudaciones con progreso, sin bloquear indefinidamente otros trabajos.

### RF-015 — Ejecución de Programación

**Prioridad:** Must Have · **Servicio(s):** Execution Service

**Usuarios:** Worker

   El sistema deberá:
   * Ejecutar código y pruebas unitarias dentro del entorno asignado.
   * Obtener resultados técnicos y errores verificables.

### RF-016 — Ejecución de Arquitectura

**Prioridad:** Must Have · **Servicio(s):** Execution Service

**Usuarios:** Worker

   El sistema deberá:
   * Procesar proyectos de código y diagramas según la rúbrica configurada.
   * Guardar resultados por comprobación o etapa cuando sea posible.

### RF-017 — Ejecución de Inteligencia Artificial

**Prioridad:** Must Have · **Servicio(s):** Execution Service

**Usuarios:** Worker

   El sistema deberá:
   * Procesar modelos y pruebas que requieran GPU.
   * Reportar resultados técnicos y uso de recursos según la tarea.

### RF-018 — Preparación de sandbox

**Prioridad:** Must Have · **Servicio(s):** Execution Service

**Usuarios:** Worker

   El sistema deberá:
   * Preparar el entorno usando la imagen base correspondiente al curso.
   * Ejecutar código del estudiante dentro de microVM aislada.

### RF-019 — Control de límites de ejecución

**Prioridad:** Must Have · **Servicio(s):** Execution Service

**Usuarios:** Worker

   El sistema deberá:
   * Supervisar el presupuesto configurado de tiempo, memoria y demás recursos.
   * Reportar excedentes y permitir extensión condicionada cuando esté autorizada.
   * Cerrar intento y solicitar revisión cuando se alcance el máximo sin resultado confiable.

### RF-020 — Persistencia de checkpoints

**Prioridad:** Must Have · **Servicio(s):** Checkpoint / Execution Service

**Usuarios:** Worker

   El sistema deberá:
   * Guardar avances por etapas y periódicamente en tareas largas que lo permitan.
   * Persistir checkpoint y sus metadatos fuera de la instancia Spot.

### RF-021 — Detección de workers perdidos

**Prioridad:** Must Have · **Servicio(s):** Evaluation Orchestrator / Spot Capacity Service

**Usuarios:** Worker

   El sistema deberá:
   * Recibir heartbeats y eventos de infraestructura.
   * Detectar intentos abandonados o interrumpidos, distinguiéndolos de errores del estudiante.

### RF-022 — Recuperación de ejecuciones

**Prioridad:** Must Have · **Servicio(s):** Evaluation Orchestrator / Checkpoint Service

**Usuarios:** Worker

   El sistema deberá:
   * Reprogramar evaluaciones interrumpidas.
   * Restaurar el último checkpoint recuperable y continuar desde allí o desde la última etapa finalizada.

### RF-023 — Transiciones atómicas e intentos vigentes

**Prioridad:** Must Have · **Servicio(s):** Evaluation Orchestrator Service

**Usuarios:** Worker

   El sistema deberá:
   * Actualizar estados de evaluación de manera atómica.
   * Rechazar resultados de versiones o intentos anteriores que ya no están autorizados.

### RF-024 — Resultados técnicos

**Prioridad:** Must Have · **Servicio(s):** Execution / Evaluation Orchestrator Service

**Usuarios:** Worker / Profesor

   El sistema deberá:
   * Persistir el resultado y evidencias de criterios ejecutados.
   * Distinguir ejecución completa, fallo de código, interrupción y evaluación inconclusa.

### RF-025 — Cálculo automático de nota provisional

**Prioridad:** Must Have · **Servicio(s):** Grading Service

**Usuarios:** Profesor

   El sistema deberá:
   * Aplicar la versión correspondiente de la rúbrica sobre evidencias verificadas.
   * Presentar una nota provisional sin publicarla automáticamente.

### RF-026 — Revisión docente de excepciones

**Prioridad:** Must Have · **Servicio(s):** Grade Review Service

**Usuarios:** Profesor

   El sistema deberá:
   * Mostrar evaluaciones con resultados no confiables o límite máximo agotado.
   * Permitir decisión o ajuste manual fundamentado y dejar evidencia.

### RF-027 — Publicación docente de calificaciones

**Prioridad:** Must Have · **Servicio(s):** Grade Review Service

**Usuarios:** Profesor / Estudiante

   El sistema deberá:
   * Permitir que el profesor publique la calificación.
   * Mostrar a estudiantes únicamente notas publicadas.

### RF-028 — Conservación de notas y recalificaciones

**Prioridad:** Must Have · **Servicio(s):** Grade Review Service

**Usuarios:** Profesor / Estudiante

   El sistema deberá:
   * Mantener la nota publicada previa mientras la nueva está en revisión.
   * Requerir publicación docente de la nueva nota y conservar historial.

### RF-029 — Consulta de estados de evaluación

**Prioridad:** Must Have · **Servicio(s):** Evaluation Orchestrator Service

**Usuarios:** Estudiante / Profesor

   El sistema deberá:
   * Mostrar a cada actor estados de las evaluaciones autorizadas.
   * Reflejar cola, ejecución, recuperación, revisión y publicación.

### RF-030 — Notificaciones de eventos relevantes

**Prioridad:** Must Have · **Servicio(s):** Notification Service

**Usuarios:** Estudiante

   El sistema deberá:
   * Generar aviso push de cambios relevantes o nota publicada.
   * Permitir siempre consultar la versión actual del estado, aunque no llegue el aviso.

### RF-031 — Monitoreo de cola y capacidad

**Prioridad:** Must Have · **Servicio(s):** Evaluation Scheduler / Spot Capacity Service

**Usuarios:** Profesor / Worker

   El sistema deberá:
   * Registrar evaluaciones pendientes y activas por pool.
   * Exponer información sobre saturación y capacidad para la operación del sistema.

### RF-032 — Alertas por plazo académico

**Prioridad:** Must Have · **Servicio(s):** Notification / Evaluation Scheduler Service

**Usuarios:** Profesor

   El sistema deberá:
   * Estimar riesgo de no terminar a tiempo para publicar dentro de 48 horas desde el deadline.
   * Informar al profesor sobre riesgo o falta de capacidad.

### RF-033 — Solicitud de ajuste de capacidad

**Prioridad:** Must Have · **Servicio(s):** Spot Capacity Service

**Usuarios:** Worker

   El sistema deberá:
   * Emitir solicitudes de ampliación o reemplazo de capacidad Spot por demanda, uso de recursos o riesgo de plazo.
   * Permitir opciones compatibles de familia, zona y región según las restricciones del equipo.



---

## Iteración 2 — Chat de creación de actividades, control de tokens y confidence level

### RF-034 — Chat docente para crear actividades

**Prioridad:** Must Have · **Servicio(s):** Activity Chat Service

**Usuario:** Profesor

    El sistema deberá:
    * Permitir iniciar y continuar una conversación asociada a un curso y a una actividad en preparación.
    * Enviar las instrucciones autorizadas del profesor al LLM conversacional del proveedor con el skill de creación de actividades cargado.
    * Mantener un historial de conversación limitado por la política de contexto y sesión.
    * Informar cuando el proveedor de LLM no esté disponible o la cuota esté agotada.

### RF-035 — Generación asistida de tarea y evaluación

**Prioridad:** Must Have · **Servicio(s):** Activity Chat / LLM Access Service

**Usuario:** Profesor

    El sistema deberá:
    * Obtener del skill una propuesta estructurada con enunciado, objetivos, criterios, pesos, rúbrica y parámetros de evaluación.
    * Permitir al profesor refinar y editar la propuesta.
    * Distinguir explícitamente contenido sugerido del contenido aprobado.

### RF-036 — Validación y aplicación docente de la propuesta

**Prioridad:** Must Have · **Servicio(s):** Activity / Activity Chat Service

**Usuario:** Profesor

    El sistema deberá:
    * Validar estructura, criterios obligatorios, coherencia de puntajes y parámetros admitidos antes de guardar la propuesta.
    * Mostrar errores de validación para corrección.
    * Requerir confirmación explícita del profesor para crear o modificar la actividad.
    * Versionar la configuración aprobada y aplicar las reglas ya definidas de recalificación cuando se modifique una rúbrica vigente.
    * No permitir que la respuesta del proveedor aplique cambios por sí misma.

### RF-037 — Gestión de presupuestos del LLM

**Prioridad:** Must Have · **Servicio(s):** Token Budget / LLM Access Service

**Usuarios:** Profesor / Worker

    El sistema deberá:
    * Aplicar presupuestos configurables a chat docente y evaluaciones que usan LLM.
    * Verificar los límites de tokens de entrada, salida, sesión docente, evaluación y worker antes de cada solicitud.
    * Considerar cuotas agregadas por actividad y límites de concurrencia cuando correspondan.
    * Autorizar o rechazar solicitudes según disponibilidad de presupuesto.

### RF-038 — Reserva y conciliación del consumo de tokens

**Prioridad:** Must Have · **Servicio(s):** Token Budget / LLM Access Service

**Usuarios:** Profesor / Worker

    El sistema deberá:
    * Reservar de manera atómica un presupuesto máximo antes de iniciar una llamada al modelo.
    * Registrar el consumo reportado por el proveedor para tokens de entrada y salida, cuando sea posible.
    * Conciliar el uso registrado con las reservas y liberar las partes no consumidas cuando exista evidencia.
    * Evitar doble gasto por solicitudes concurrentes o duplicadas.
    * Mantener reservas conservadoras cuando una llamada falle sin reportar uso verificable, hasta su conciliación o expiración controlada.

### RF-039 — Persistencia de presupuestos entre reintentos

**Prioridad:** Must Have · **Servicio(s):** Token Budget Service

**Usuario:** Worker

    El sistema deberá:
    * Asociar el consumo acumulado al identificador lógico de la evaluación, no solamente al worker o intento.
    * Conservar consumo y reservas entre checkpoints, interrupciones, nuevas asignaciones y reintentos.
    * Impedir que una reasignación reinicie el presupuesto de tokens.

### RF-040 — Manejo del agotamiento de tokens

**Prioridad:** Nice to Have · **Servicio(s):** Token Budget Service

**Usuarios:** Profesor / Worker

    El sistema deberá:
    * Bloquear llamadas al LLM que excedan el presupuesto autorizado.
    * Informar al profesor que el chat no puede continuar por cuota cuando corresponda.
    * Permitir continuar únicamente etapas deterministas que no requieran llamadas al modelo.
    * Registrar la evaluación como parcial o no concluyente si faltan criterios necesarios, evitando asignar una nota arbitraria.
    * Escalar a revisión docente según la política definida.

### RF-041 — Registro de evidencia de confianza

**Prioridad:** Must Have · **Servicio(s):** Execution / Grading Service

**Usuario:** Worker

    El sistema deberá:
    * Registrar por criterio pruebas ejecutadas, comprobaciones exitosas, errores, faltantes e incertidumbre relevante.
    * Distinguir evidencia determinista de juicios generados con apoyo del LLM.
    * Asociar las evidencias a entrega, SHA, rúbrica, intento y versión del evaluador/modelo que corresponda.

### RF-042 — Cálculo de confidence level

**Prioridad:** Must Have · **Servicio(s):** Grading Service

**Usuarios:** Worker / Profesor

    El sistema deberá:
    * Producir una nota provisional cuando haya evidencia suficiente para calcularla.
    * Calcular un indicador de confianza basado en completitud, verificabilidad, errores e incertidumbre de la evaluación, de acuerdo con una política versionada.
    * Registrar nivel alto, medio o bajo y sus razones, con umbrales configurables todavía TBD.
    * Marcar **no concluyente** en lugar de asignar confianza o calificación ficticia cuando falte evidencia esencial.
    * No tratar una autodeclaración del LLM como evidencia suficiente de confianza.

### RF-043 — Visualización docente de nota y confianza

**Prioridad:** Must Have · **Servicio(s):** Grading / Grade Review Service

**Usuario:** Profesor

    El sistema deberá:
    * Mostrar conjuntamente la nota provisional, el confidence level, su explicación y las evidencias relevantes.
    * Destacar confianza baja, criterios incompletos y evaluación no concluyente para revisión.
    * Mantener la decisión y publicación final en manos del profesor.

### RF-044 — Trazabilidad de uso del LLM y del skill

**Prioridad:** Nice to Have · **Servicio(s):** LLM Access Service

**Usuarios:** Profesor / Worker

    El sistema deberá:
    * Registrar identificadores de solicitud, tipo de uso (chat o evaluación), proveedor, modelo y versión del skill cuando corresponda.
    * Registrar tokens presupuestados, consumidos y pendientes de conciliación; estado y motivo del fallo.
    * Asociar resultados del chat a la propuesta de actividad aprobada y resultados de evaluación a la entrega y rúbrica vigentes.
    * Restringir el acceso a esos registros según permisos y evitar guardar secretos en ellos.

### RF-045 — Configuración y seguimiento de cuotas

**Prioridad:** Nice to Have · **Servicio(s):** Token Budget Service

**Usuarios beneficiados:** Profesor / Worker

    El sistema deberá:
    * Permitir gestionar mediante configuración operativa autorizada los límites de contexto, salida, sesión, evaluación, worker, actividad y concurrencia.
    * Exponer métricas y alertas de consumo, agotamiento, errores del proveedor y evaluaciones afectadas.
    * No requerir un nuevo usuario administrativo para realizar estas configuraciones dentro del alcance actual.



---

## Iteración 3 — Compatibilidad, coexistencia y transición del legacy de Arquitectura de Software

> **Origen: EQUIPO (supuestos del laboratorio).** El enunciado confirma que ya existe un sistema de corrección del curso de Arquitectura de Software en una laptop, pero no describe sus interfaces ni su base de datos. Para esta iteración, el equipo **asume** que ese sistema legacy posee contratos propios y almacenamiento independiente, y que será necesario mantenerlo operando durante una transición progresiva hacia Spotty. Los siguientes RF son de **ámbito SISTEMA**, no se atribuyen a Estudiante, Profesor ni Worker. No prescriben un patrón de arquitectura concreto.

### RF-046 — Compatibilidad con contratos legacy

**Prioridad:** Must Have · **Servicio(s):** Legacy Compatibility Service

**Ámbito:** SISTEMA  
    **Origen:** EQUIPO

    El sistema deberá:
    * Permitir la interoperabilidad con los contratos existentes del sistema legacy de Arquitectura de Software durante el periodo de transición.
    * Adaptar las entradas y salidas necesarias para que los consumidores existentes puedan continuar operando sin modificaciones inmediatas de sus contratos.
    * Identificar y manejar incompatibilidades de datos o versiones de contrato sin alterar silenciosamente su significado.

### RF-047 — Acceso y preservación de información histórica legacy

**Prioridad:** Must Have · **Servicio(s):** Legacy Compatibility Service

**Ámbito:** SISTEMA  
    **Origen:** EQUIPO

    El sistema deberá:
    * Permitir recuperar o incorporar las entregas, evaluaciones y calificaciones históricas necesarias del sistema legacy.
    * Conservar la relación entre cada registro histórico y sus identificadores de origen al consultarlo o incorporarlo a Spotty.
    * Evitar que la incorporación de información histórica publique o modifique automáticamente calificaciones oficiales vigentes.

### RF-048 — Coexistencia operativa entre legacy y Spotty

**Prioridad:** Must Have · **Servicio(s):** Legacy Compatibility Service

**Ámbito:** SISTEMA  
    **Origen:** EQUIPO

    El sistema deberá:
    * Permitir que el legacy continúe atendiendo los procesos que aún no hayan sido transferidos a Spotty.
    * Identificar qué sistema debe atender cada operación comprendida en la transición.
    * Evitar el procesamiento contradictorio de una misma operación por ambos sistemas durante la coexistencia.

### RF-049 — Control de responsabilidad y consistencia de datos durante la transición

**Prioridad:** Must Have · **Servicio(s):** Legacy Compatibility Service

**Ámbito:** SISTEMA  
    **Origen:** EQUIPO

    El sistema deberá:
    * Mantener identificada la fuente autoritativa de entregas, resultados y calificaciones según la fase de transición correspondiente.
    * Controlar la correspondencia entre identificadores legacy y Spotty cuando sea necesaria para la interoperabilidad o migración.
    * Detectar y manejar duplicaciones o conflictos antes de aceptar cambios que afecten la información académica vigente.

### RF-050 — Transición progresiva y reversión controlada

**Prioridad:** Must Have · **Servicio(s):** Legacy Compatibility Service

**Ámbito:** SISTEMA  
    **Origen:** EQUIPO

    El sistema deberá:
    * Permitir transferir gradualmente a Spotty los flujos o capacidades previamente atendidos por el legacy.
    * Registrar qué flujos se mantienen en el legacy y cuáles han sido transferidos.
    * Permitir suspender o revertir de manera controlada una transición fallida, sin perder el historial ni invalidar cambios confirmados sin reconciliación.

### Supuestos de la Iteración 3

- **SUP-001:** El sistema legacy de Arquitectura de Software dispone de contratos propios para recibir o consultar entregas y resultados.
- **SUP-002:** El legacy conserva sus datos en un almacenamiento propio, independiente del almacenamiento nuevo de Spotty.
- **SUP-003:** El legacy debe seguir operando al menos durante una parte de la transición.
- **SUP-004:** La información académica histórica del legacy debe preservarse.
- **SUP-005:** La sustitución de capacidades del legacy por Spotty se realizará progresivamente.

> **Pendiente para Discovery y arquitectura:** inventariar contratos legacy, identificar entidades y dueños de datos, definir unidad de migración y condiciones de corte y reversión. La elección de Strangler Pattern, adaptadores o mecanismos de sincronización corresponde a la fase arquitectónica, no a estos RF.

## Texto de referencia — requerimientos no funcionales

> Se conserva la redacción de `rnf.md` para cada RNF. Los acuerdos cuantitativos adicionales del documento fuente se reproducen después de esta sección.

### RNF-001 — Seguridad y aislamiento

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** Cada entrega de código no confiable deberá ejecutarse en su propio entorno microVM aislado, con restricciones de red, procesos, CPU, memoria y almacenamiento.

### RNF-002 — Autorización académica

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** Las consultas y modificaciones deberán respetar identidad institucional, rol y vinculación con cursos; los workers solo accederán a datos de su evaluación autorizada.

### RNF-003 — Protección de credenciales

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** El código del estudiante no deberá recibir credenciales institucionales ni privilegios de administración del plano central.

### RNF-004 — Perfiles de ejecución

**Prioridad:** Must Have

**Origen:** CASO  
**Requisito:** La solución deberá soportar los perfiles de corrección de Programación, Arquitectura e IA. Se interpretan los P99 de 1 minuto (Programación), 10 minutos (Arquitectura) y 40 minutos o más (IA) como latencia de procesamiento de la evaluación desde el inicio efectivo del worker hasta producir el resultado técnico, excluyendo espera de cola y publicación docente. Para pruebas del laboratorio se adopta P99 objetivo de 40 minutos en trabajos IA estándar; los trabajos de IA extendidos se clasifican y reportan por separado sin prometer ese umbral.

### RNF-005 — Carga en deadline

**Prioridad:** Must Have

**Origen:** CASO  
**Requisito:** El sistema deberá diseñarse para una carga concentrada de entregas en los últimos 30 minutos previos al cierre de la actividad, modelando, como supuesto del equipo, 1,200 alumnos distribuidos en 30 cursos, 80 % de 1,200 entregas dentro de esa ventana (960 entregas/30 min, media de 0.53 entregas/segundo) y un factor de pico de 5 veces esa media (2.67 entregas/segundo). Se probará además un escenario de estrés de 4,800 entregas/30 min.

### RNF-006 — Escalabilidad diferenciada

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** La capacidad de procesamiento deberá poder variar independientemente para CPU y GPU según trabajo pendiente y utilización de CPU, GPU y memoria.

### RNF-007 — Disponibilidad de la plataforma

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** La consulta de cursos, entregas y notas deberá poder funcionar aunque temporalmente no haya capacidad Spot para nuevas evaluaciones.

### RNF-008 — Alta disponibilidad de persistencia

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** La base de datos académica y de estado de evaluación deberá emplear replicación y failover; la durabilidad de checkpoints no deberá depender del disco del worker.

### RNF-009 — Confiabilidad ante interrupción Spot

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** Una entrega aceptada no deberá desaparecer por el reclamo de un worker. Deberá poder reprogramarse desde el último progreso recuperable, o repetir una etapa cuando el estado exacto no se pueda restaurar.

### RNF-010 — Ventana de aviso de AWS Spot

**Prioridad:** Must Have

**Origen:** CASO  
**Requisito:** El diseño deberá contemplar que AWS puede reclamar la instancia con aproximadamente 2 minutos de aviso y que puede no existir capacidad Spot de reemplazo.

### RNF-011 — Consistencia e idempotencia

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** Un resultado obsoleto, duplicado o procedente de una versión reemplazada no deberá modificar la nota vigente. Las transiciones críticas deberán ser atómicas.

### RNF-012 — Límites de ejecución

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** Cada sandbox tendrá límite de 2 vCPU, 4 GiB RAM, 10 GiB de disco efímero y 128 procesos para Programación; 4 vCPU, 8 GiB RAM, 15 GiB y 128 procesos para Arquitectura; y 8 vCPU, 24 GiB RAM, 30 GiB y una GPU compatible para IA. La ejecución máxima será de 3, 20 y 90 minutos respectivamente; se permite una ampliación docente de hasta 50 % del límite inicial por intento, una sola vez. Exceder memoria o tiempo finalizará el intento con evidencia para revisión, sin castigar automáticamente al estudiante por fallo de infraestructura.

### RNF-013 — Eficiencia de imágenes

**Prioridad:** Must Have

**Origen:** CASO/EQUIPO  
**Requisito:** El diseño deberá considerar imágenes base por curso de 3 a 5 GB y permitir reutilizarlas desde la caché local mientras el nodo exista.

### RNF-014 — Cumplimiento de plazo

**Prioridad:** Must Have

**Origen:** CASO/EQUIPO  
**Requisito:** El diseño deberá buscar que los profesores puedan publicar notas como máximo 48 horas después del cierre, monitoreando el riesgo; no se afirmará garantía absoluta si AWS Spot carece de capacidad.

### RNF-015 — Trazabilidad de evaluación

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** Deberá conservarse evidencia de qué SHA, versión de rúbrica, intento, checkpoint y resultados técnicos produjeron cada nota provisional o publicada.

### RNF-016 — Trazabilidad de notas

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** Toda recalificación y publicación posterior deberá conservar historial; una nota publicada no se reemplazará sin nueva publicación docente.

### RNF-017 — Disponibilidad de API

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** Los contratos para web y mobile deberán ser atendidos por backends stateless con réplicas y balanceo de carga.

### RNF-018 — Degradación parcial

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** La indisponibilidad del servicio push no deberá impedir que el estudiante consulte su estado o nota publicada.

### RNF-019 — Observabilidad

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** Deberán observarse tamaño y espera de colas, evaluaciones activas, interrupciones, fallos, heartbeats, utilización CPU/GPU/memoria y riesgo de plazo.

### RNF-020 — Modularidad

**Prioridad:** Must Have

**Origen:** CURSO  
**Requisito:** La solución deberá mantener responsabilidades coherentes, alta cohesión y bajo acoplamiento entre gestión académica, evaluación y ejecución.

### RNF-021 — Usabilidad

**Prioridad:** Nice to Have

**Origen:** EQUIPO  
**Requisito:** La app del estudiante y la web docente deberán presentar estados, resultados y errores en términos comprensibles para sus respectivos usuarios.

### RNF-022 — Capacidad mínima deseada

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** Como objetivo de operación, el orquestador solicitará al menos dos instancias Spot por pool CPU y GPU cuando exista demanda y cuota aprobada; el mínimo real podrá ser cero si Spot no dispone de capacidad. Se fija un techo de 12 instancias CPU y 6 GPU solicitadas, con máximo de 4 sandboxes simultáneos por host CPU y 1 por host GPU, sujeto a los recursos reales del host. El control de admisión impedirá sobreasignación de memoria.

### RNF-023 — Compatibilidad de GPU

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** La recuperación de tareas GPU deberá tener en cuenta la compatibilidad del estado recuperable con el hardware seleccionado; donde no sea compatible se requerirá repetición desde etapa válida.

### RNF-024 — Límites finitos de tokens

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** Toda llamada a un LLM deberá estar sujeta a límites configurables de tokens de entrada, salida, contexto y presupuesto acumulado según el origen de uso. Se aplican los límites concretos del cuadro de políticas del laboratorio incluido al final de la iteración 2.

### RNF-025 — Aislamiento de presupuestos

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** El consumo concurrente de chat y evaluaciones no deberá eludir los presupuestos por sesión, evaluación, worker y actividad; las reservas deberán gestionarse de forma atómica.

### RNF-026 — Durabilidad y no reinicio de consumo

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** La contabilidad de consumo y reservas deberá persistir fuera de la instancia Spot y sobrevivir a reintentos, interrupciones y reasignaciones, sin volver a disponer del presupuesto gastado.

### RNF-027 — Protección frente a respuestas no confiables del proveedor

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** El texto generado por el LLM, incluidos resultados del skill y contenido de repositorios estudiantiles, se tratará como entrada no confiable. No podrá alterar permisos, ejecutar herramientas no autorizadas ni efectuar publicaciones sin validación y aprobación docente.

### RNF-028 — Privilegios mínimos para integración LLM

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** La integración con el proveedor y el skill solo deberá disponer de contexto y herramientas necesarios para cada tarea; no tendrá acceso administrativo a cursos, notas oficiales, credenciales ni al plano de control de workers.

### RNF-029 — Degradación ante indisponibilidad o cuota agotada

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** Una falla del proveedor LLM, la saturación de llamadas o el agotamiento de tokens no deberá inutilizar el resto de la plataforma ni convertir automáticamente una evaluación inconclusa en nota desaprobatoria.

### RNF-030 — Explicabilidad del confidence level

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** Todo confidence level emitido deberá acompañarse de evidencia y de la versión de la regla de cálculo. Una cifra producida exclusivamente por autovaloración del LLM no será válida como medida de confianza.

### RNF-031 — Separación entre confianza y calificación

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Requisito:** El indicador de confianza no deberá modificar directamente el puntaje obtenido según rúbrica ni reemplazar la revisión humana; los resultados no concluyentes deberán diferenciarse de notas bajas.

### RNF-032 — Trazabilidad del proveedor y del skill

**Prioridad:** Nice to Have

**Origen:** EQUIPO  
**Requisito:** Deberán registrarse el proveedor, identificadores de modelo y skill, versiones relevantes, presupuestos, uso reportado y resultados sin exponer secretos ni almacenar datos sensibles innecesariamente.

### RNF-033 — Observabilidad y control de costos

**Prioridad:** Nice to Have

**Origen:** EQUIPO  
**Requisito:** Se deberán monitorizar consumo de tokens de entrada y salida, reservas pendientes, errores de proveedor, saturación, llamadas rechazadas, presupuestos agotados y costo estimado por actividad y evaluación.

### RNF-034 — Límites configurables y verificables

**Prioridad:** Nice to Have

**Origen:** EQUIPO  
**Requisito:** Los límites máximos de tokens, contexto, concurrencia, sesiones y umbrales de confianza deberán estar centralizados, documentados y sujetos a verificación mediante pruebas de aceptación. Para el laboratorio se usan los valores aprobados como supuestos del equipo y se comprueban mediante pruebas de aceptación.

## Política LLM y confianza de la iteración 2 (supuestos EQUIPO)

- **Proveedor de referencia:** API compatible con OpenAI, modelo de chat `gpt-4o-mini` y modelo de evaluación `gpt-4o-mini`, como elecciones de arquitectura para el ejercicio; las funciones deterministas no deben llamar al LLM.
- **Skill:** contrato `activity-draft-v1`, salida JSON validada por esquema con `title`, `description`, `criteria[]`, `weights[]`, `limits` y `rubric_version`. Es una convención adoptada para Spotty, no un contrato suministrado por el laboratorio.
- **Por llamada:** entrada máxima 8,000 tokens, salida máxima 2,000 y contexto acumulado máximo 16,000 tokens.
- **Chat docente:** 30,000 tokens combinados por sesión y 150,000 por profesor/día.
- **Evaluación:** 20,000 tokens combinados por evaluación lógica completa, compartidos por todos los reintentos; techo de 100,000 tokens por worker/día y 500,000 tokens por actividad/día.
- **Concurrencia:** hasta 10 llamadas LLM globales, 2 por profesor y 1 por evaluación simultáneamente; se reserva el máximo antes de llamar al proveedor.
- **Contabilidad:** si el proveedor no informa consumo debido a fallo/timeout, retener la reserva durante 24 h y conciliar mediante evidencia de facturación o registro del proveedor; nunca liberar automáticamente consumo desconocido antes de resolverlo.
- **Confianza:** `alta` si completitud verificable >= 90 % sin criterios críticos ausentes; `media` si >= 70 % y < 90 %; `baja` si < 70 % pero existen pruebas suficientes para calcular calificación provisional; `no concluyente` si falta evidencia de cualquier criterio obligatorio o si no puede determinarse puntaje. El indicador representa cobertura de evidencia, no probabilidad estadística de corrección.

---

### RNF-035 — Compatibilidad retroactiva de contratos

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Atributo:** Compatibilidad / Interoperabilidad  
**Requisito:** Durante el período de coexistencia, las interfaces existentes del sistema legacy que se declaren vigentes deberán mantener un comportamiento compatible para sus consumidores autorizados. Los cambios de formato, semántica o versión deberán gestionarse explícitamente, sin exigir una migración simultánea de todos los consumidores.

### RNF-036 — Integridad y trazabilidad de información migrada

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Atributo:** Integridad / Consistencia / Trazabilidad  
**Requisito:** La integración o migración de entregas, evaluaciones y calificaciones históricas deberá preservar su correspondencia con alumno, curso, actividad, versión y estado, según los datos disponibles en el legacy. Se deberán detectar registros duplicados o conflictivos, identificar el origen y registrar las transformaciones aplicadas. No se considerará exitosa una migración con pérdida silenciosa de información.

### RNF-037 — Continuidad operativa durante la transición

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Atributo:** Disponibilidad / Reliability  
**Requisito:** La transición del legacy a Spotty deberá minimizar interrupciones de las operaciones académicas vigentes. Un fallo de integración o de una etapa de migración no deberá bloquear indiscriminadamente los cursos ya operativos en la plataforma que no dependan de esa etapa; el alcance de cualquier degradación deberá ser explícito y observable.

### RNF-038 — Reversibilidad y recuperación controlada de la migración

**Prioridad:** Must Have

**Origen:** EQUIPO  
**Atributo:** Recoverability / Operabilidad  
**Requisito:** Cada fase de transición deberá contar con un procedimiento verificable para detener o revertir el enrutamiento de nuevas operaciones cuando se detecten fallos, sin sobrescribir cambios legítimos ni perder operaciones ya confirmadas. Si una reversión de datos no es segura, deberá definirse recuperación o conciliación controlada en lugar de prometer rollback automático.

## Supuestos de diseño de la iteración 3

- **SUP-001:** El sistema legacy de Arquitectura de Software expone contratos existentes que deben respetarse durante la transición.
- **SUP-002:** El legacy posee persistencia y modelo de datos propios.
- **SUP-003:** Legacy y Spotty coexistirán durante alguna etapa de incorporación progresiva.
- **SUP-004:** Los registros históricos disponibles de entregas y calificaciones deben preservarse.
- **SUP-005:** La incorporación de las capacidades legacy a Spotty podrá hacerse por etapas.

## Contrato de coexistencia legacy definido para el laboratorio (supuestos EQUIPO)

- **Contratos legacy vigentes:** `POST /legacy/v1/submissions` (registro), `GET /legacy/v1/submissions/{id}` (estado), `GET /legacy/v1/results/{id}` (resultado). El payload mínimo de una entrega es `legacy_submission_id`, `student_id`, `course_id`, `assignment_id`, `repository_url`, `commit_sha` y `submitted_at`. Los identificadores y endpoints son inventario asumido para el ejercicio, no extraído de la laptop original.
- **Propiedad inicial de datos:** durante la fase 1, legacy es fuente autoritativa para entregas y resultados históricos de Arquitectura; Spotty lo es para los cursos nuevos. En fase 2, Spotty asume nuevos registros de Arquitectura desde una fecha de corte versionada; legacy conserva solo lectura de históricos.
- **Correspondencia:** tabla persistente `legacy_submission_id` ↔ `spotty_submission_id`; claves de deduplicación `(course_id, assignment_id, student_id, commit_sha, submitted_at)` y huella del origen; conflictos se envían a conciliación, no se resuelven sobrescribiendo.
- **Ventana de compatibilidad:** conservar `/legacy/v1` durante 90 días tras el corte; comunicación de deprecación 30 días antes de retirarlo. La retirada solo se autoriza tras verificar ausencia de consumidores activos y aprobarla el equipo.
- **Migración por lotes:** primero histórico en modo lectura, luego un curso piloto, después el resto. Verificación de 100 % de conteos por lote, 100 % de identificadores únicos y comparación de hashes cuando estén disponibles; toda discrepancia bloquea la aprobación del lote.
- **Objetivos de transición:** ventana máxima planificada de indisponibilidad de escritura del curso migrado de 15 min; RPO = 0 para operaciones de entrega confirmadas (mediante registro durable y reconciliación) y RTO <= 30 min para restablecer ruta del contrato legado tras un fallo del corte.
- **Reversión:** ante error en contratos, divergencia de conteos o pérdida de escrituras, detener el cambio de ruta y volver temporalmente al propietario anterior solo si se han conciliado las escrituras ya aceptadas; nunca hacer rollback destructivo de datos confirmados.

## Estado de definición

**CERRADO PARA EL LABORATORIO.** Todos los números, contratos, políticas y límites no expresados originalmente en el enunciado son **hipótesis de diseño aprobadas para el ejercicio**, no datos observados de producción ni garantías de infraestructura. Podrán ajustarse posteriormente en pruebas o por indicación del docente, con control de versiones.

## Acuerdos cuantitativos del laboratorio (RNF v4)

- **Carga de referencia:** 30 cursos, 1,200 estudiantes, 960 entregas en los últimos 30 minutos, pico de admisión 2.67 entregas/s; estrés 4,800 entregas/30 min.
- **API:** P95 de inicio de sesión <= 1.5 s; P95 de aceptación de entrega <= 2 s; P95 de consulta de estado <= 800 ms. Disponibilidad mensual objetivo del plano académico: 99.9 %, medida sin penalizar falta de capacidad Spot para la evaluación asíncrona.
- **Persistencia:** RPO objetivo <= 5 min y RTO objetivo <= 30 min para servicios de control y datos académicos; una entrega confirmada debe contar con registro durable antes de responder.
- **Checkpoints:** tareas de Programación guardan evidencia al final de cada prueba; Arquitectura al terminar cada etapa o cada 3 min; IA cada 5 min o por época cuando sea viable. Checkpoint individual <= 2 GiB; si excede ese tamaño se conserva un resultado por etapa, no la imagen exacta del proceso.
- **Interrupción:** al aviso Spot se cesa admisión inmediata de nuevas tareas y se intenta subir un checkpoint en 90 s; si no concluye, se reinicia desde el último checkpoint durable.
- **Supervisión:** heartbeat cada 15 s; tras 60 s sin heartbeat un intento queda sospechoso y tras 120 s se considera recuperable por reasignación, previa invalidación atómica del lease anterior.
- **Escalamiento:** reevaluación cada 60 s; solicitar ampliación cuando la espera estimada > 5 min para CPU o > 15 min para GPU o utilización de memoria > 75 % por 3 min; reducción tras 15 min sin trabajos y sin ejecuciones activas. La solicitud nunca constituye garantía de capacidad Spot.
- **Presupuesto de laboratorio:** techo referencial mensual de USD 1,500 para workers Spot y almacenamiento temporal de evaluación; gasto real sujeto a los precios Spot efectivos. Cuando se alcance el techo, se retienen evaluaciones en cola y se alerta por riesgo del plazo académico.
- **Disponibilidad de procesamiento:** Spot puede no ofrecer capacidad; las metas P99 aplican a trabajos que efectivamente inician y no constituyen garantía absoluta del plazo de 48 h.

## Nota sobre evidencia arquitectónica

Que un RF/RNF esté incluido y asignado a un servicio **no demuestra por sí mismo su cumplimiento**. Los diagramas describen responsabilidades y relaciones; los atributos de calidad deben validarse con pruebas/fitness functions (p. ej., P95, reanudación Spot, atomicidad, costos).

El aprovisionamiento explícito `POST /users/provision` del diagrama se añadió para atender el criterio Security Minion y **no es un RF adicional numerado** en `rf.md`; debe mantenerse restringido al proceso institucional.

