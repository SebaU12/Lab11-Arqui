# Requerimientos Funcionales — Spotty v3

> **Alcance:** plataforma académica completa y evaluación automática. Los RF describen **qué debe hacer** Spotty, no exigen un despliegue independiente por función. Estudiante, Profesor y Worker son los tres actores principales; Worker es un actor técnico. Las tecnologías concretas son decisiones del equipo y pueden revisarse en arquitectura/reliability. El LLM conversacional es un servicio de proveedor externo con un skill cargado directamente; **no es un usuario ni actor principal**. La Iteración 3 incorpora requisitos **de ámbito SISTEMA** para la coexistencia y transición del sistema legacy de Arquitectura de Software, basados en supuestos del equipo y sin asignarlos artificialmente a actores humanos.

## Actores

- **Estudiante:** consulta cursos y tareas, registra entregas y consulta estados y notas publicadas.
- **Profesor:** administra cursos, rúbricas, alumnos, revisiones y publicación de notas.
- **Worker:** ejecuta evaluaciones asignadas, envía checkpoints y resultados, y reporta su estado.
- **Externos:** identidad institucional, GitHub, AWS Spot y proveedor push y proveedor de LLM conversacional (con skill cargado).

---

1. **RF-001 — Inicio de sesión institucional**  
   **Usuarios:** Estudiante / Profesor

   El sistema deberá:
   * Autenticar a los usuarios mediante el proveedor de identidad institucional.
   * Permitir cerrar sesión.
   * No almacenar contraseñas institucionales como credenciales propias.

2. **RF-002 — Autorización por rol y curso**  
   **Usuarios:** Estudiante / Profesor

   El sistema deberá:
   * Determinar rol y cursos autorizados.
   * Restringir lecturas y modificaciones de actividades, entregas y notas según permisos.

3. **RF-003 — Gestión de cursos**  
   **Usuarios:** Profesor

   El sistema deberá:
   * Crear y consultar cursos autorizados.
   * Modificar los datos administrables de dichos cursos.

4. **RF-004 — Vinculación de estudiantes**  
   **Usuarios:** Profesor / Estudiante

   El sistema deberá:
   * Vincular o desvincular estudiantes de un curso por acción docente.
   * Permitir al estudiante consultar solo sus cursos vinculados.

5. **RF-005 — Creación de actividades**  
   **Usuarios:** Profesor

   El sistema deberá:
   * Crear actividades con instrucciones, modalidad y fecha límite.
   * Presentarlas a los estudiantes vinculados.

6. **RF-006 — Configuración de rúbricas**  
   **Usuarios:** Profesor

   El sistema deberá:
   * Definir criterios, reglas, matices y puntajes de evaluación.
   * Asociar una versión identificable de rúbrica a cada actividad y evaluación.

7. **RF-007 — Consulta de actividades**  
   **Usuarios:** Estudiante / Profesor

   El sistema deberá:
   * Consultar tareas, instrucciones, deadline y rúbrica publicada de cursos autorizados.

8. **RF-008 — Edición de actividades y recalificación**  
   **Usuarios:** Profesor

   El sistema deberá:
   * Permitir cambios en actividades o rúbricas.
   * Conservar versiones y generar nuevas evaluaciones para las entregas afectadas.

9. **RF-009 — Registro de entrega GitHub**  
   **Usuarios:** Estudiante

   El sistema deberá:
   * Recibir el enlace de GitHub de la tarea.
   * Resolver y registrar commit SHA, actividad, alumno y hora de recepción del servidor.
   * Confirmar aceptación o informar cuando no pueda registrarse válidamente.

10. **RF-010 — Reentrega y versión vigente**  
   **Usuarios:** Estudiante

   El sistema deberá:
   * Permitir reentregas antes del deadline.
   * Definir como vigente la última entrega válida aunque su nota sea menor.
   * Invalidar evaluaciones pendientes obsoletas e intentar cancelar las que ya corren.

11. **RF-011 — Consulta de historial de entregas**  
   **Usuarios:** Estudiante / Profesor

   El sistema deberá:
   * Mostrar versiones y estados de entregas autorizadas.
   * Identificar la entrega vigente.

12. **RF-012 — Solicitud asíncrona de evaluación**  
   **Usuarios:** Estudiante / Worker

   El sistema deberá:
   * Generar solicitud de evaluación al aceptar una entrega.
   * Confirmar recepción independientemente de la disponibilidad inmediata de un worker.

13. **RF-013 — Clasificación CPU y GPU**  
   **Usuarios:** Worker

   El sistema deberá:
   * Dirigir Programación y Arquitectura a la cola CPU.
   * Dirigir IA a la cola GPU.

14. **RF-014 — Priorización de evaluaciones**  
   **Usuarios:** Worker / Profesor

   El sistema deberá:
   * Ordenar trabajo según el deadline de la actividad y la urgencia de publicación.
   * Aplicar reparto justo entre cursos.
   * Dar preferencia razonable a reanudaciones con progreso, sin bloquear indefinidamente otros trabajos.

15. **RF-015 — Ejecución de Programación**  
   **Usuarios:** Worker

   El sistema deberá:
   * Ejecutar código y pruebas unitarias dentro del entorno asignado.
   * Obtener resultados técnicos y errores verificables.

16. **RF-016 — Ejecución de Arquitectura**  
   **Usuarios:** Worker

   El sistema deberá:
   * Procesar proyectos de código y diagramas según la rúbrica configurada.
   * Guardar resultados por comprobación o etapa cuando sea posible.

17. **RF-017 — Ejecución de Inteligencia Artificial**  
   **Usuarios:** Worker

   El sistema deberá:
   * Procesar modelos y pruebas que requieran GPU.
   * Reportar resultados técnicos y uso de recursos según la tarea.

18. **RF-018 — Preparación de sandbox**  
   **Usuarios:** Worker

   El sistema deberá:
   * Preparar el entorno usando la imagen base correspondiente al curso.
   * Ejecutar código del estudiante dentro de microVM aislada.

19. **RF-019 — Control de límites de ejecución**  
   **Usuarios:** Worker

   El sistema deberá:
   * Supervisar el presupuesto configurado de tiempo, memoria y demás recursos.
   * Reportar excedentes y permitir extensión condicionada cuando esté autorizada.
   * Cerrar intento y solicitar revisión cuando se alcance el máximo sin resultado confiable.

20. **RF-020 — Persistencia de checkpoints**  
   **Usuarios:** Worker

   El sistema deberá:
   * Guardar avances por etapas y periódicamente en tareas largas que lo permitan.
   * Persistir checkpoint y sus metadatos fuera de la instancia Spot.

21. **RF-021 — Detección de workers perdidos**  
   **Usuarios:** Worker

   El sistema deberá:
   * Recibir heartbeats y eventos de infraestructura.
   * Detectar intentos abandonados o interrumpidos, distinguiéndolos de errores del estudiante.

22. **RF-022 — Recuperación de ejecuciones**  
   **Usuarios:** Worker

   El sistema deberá:
   * Reprogramar evaluaciones interrumpidas.
   * Restaurar el último checkpoint recuperable y continuar desde allí o desde la última etapa finalizada.

23. **RF-023 — Transiciones atómicas e intentos vigentes**  
   **Usuarios:** Worker

   El sistema deberá:
   * Actualizar estados de evaluación de manera atómica.
   * Rechazar resultados de versiones o intentos anteriores que ya no están autorizados.

24. **RF-024 — Resultados técnicos**  
   **Usuarios:** Worker / Profesor

   El sistema deberá:
   * Persistir el resultado y evidencias de criterios ejecutados.
   * Distinguir ejecución completa, fallo de código, interrupción y evaluación inconclusa.

25. **RF-025 — Cálculo automático de nota provisional**  
   **Usuarios:** Profesor

   El sistema deberá:
   * Aplicar la versión correspondiente de la rúbrica sobre evidencias verificadas.
   * Presentar una nota provisional sin publicarla automáticamente.

26. **RF-026 — Revisión docente de excepciones**  
   **Usuarios:** Profesor

   El sistema deberá:
   * Mostrar evaluaciones con resultados no confiables o límite máximo agotado.
   * Permitir decisión o ajuste manual fundamentado y dejar evidencia.

27. **RF-027 — Publicación docente de calificaciones**  
   **Usuarios:** Profesor / Estudiante

   El sistema deberá:
   * Permitir que el profesor publique la calificación.
   * Mostrar a estudiantes únicamente notas publicadas.

28. **RF-028 — Conservación de notas y recalificaciones**  
   **Usuarios:** Profesor / Estudiante

   El sistema deberá:
   * Mantener la nota publicada previa mientras la nueva está en revisión.
   * Requerir publicación docente de la nueva nota y conservar historial.

29. **RF-029 — Consulta de estados de evaluación**  
   **Usuarios:** Estudiante / Profesor

   El sistema deberá:
   * Mostrar a cada actor estados de las evaluaciones autorizadas.
   * Reflejar cola, ejecución, recuperación, revisión y publicación.

30. **RF-030 — Notificaciones de eventos relevantes**  
   **Usuarios:** Estudiante

   El sistema deberá:
   * Generar aviso push de cambios relevantes o nota publicada.
   * Permitir siempre consultar la versión actual del estado, aunque no llegue el aviso.

31. **RF-031 — Monitoreo de cola y capacidad**  
   **Usuarios:** Profesor / Worker

   El sistema deberá:
   * Registrar evaluaciones pendientes y activas por pool.
   * Exponer información sobre saturación y capacidad para la operación del sistema.

32. **RF-032 — Alertas por plazo académico**  
   **Usuarios:** Profesor

   El sistema deberá:
   * Estimar riesgo de no terminar a tiempo para publicar dentro de 48 horas desde el deadline.
   * Informar al profesor sobre riesgo o falta de capacidad.

33. **RF-033 — Solicitud de ajuste de capacidad**  
   **Usuarios:** Worker

   El sistema deberá:
   * Emitir solicitudes de ampliación o reemplazo de capacidad Spot por demanda, uso de recursos o riesgo de plazo.
   * Permitir opciones compatibles de familia, zona y región según las restricciones del equipo.



---

## Iteración 2 — Chat de creación de actividades, control de tokens y confidence level

34. **RF-034 — Chat docente para crear actividades**  
    **Usuario:** Profesor

    El sistema deberá:
    * Permitir iniciar y continuar una conversación asociada a un curso y a una actividad en preparación.
    * Enviar las instrucciones autorizadas del profesor al LLM conversacional del proveedor con el skill de creación de actividades cargado.
    * Mantener un historial de conversación limitado por la política de contexto y sesión.
    * Informar cuando el proveedor de LLM no esté disponible o la cuota esté agotada.

35. **RF-035 — Generación asistida de tarea y evaluación**  
    **Usuario:** Profesor

    El sistema deberá:
    * Obtener del skill una propuesta estructurada con enunciado, objetivos, criterios, pesos, rúbrica y parámetros de evaluación.
    * Permitir al profesor refinar y editar la propuesta.
    * Distinguir explícitamente contenido sugerido del contenido aprobado.

36. **RF-036 — Validación y aplicación docente de la propuesta**  
    **Usuario:** Profesor

    El sistema deberá:
    * Validar estructura, criterios obligatorios, coherencia de puntajes y parámetros admitidos antes de guardar la propuesta.
    * Mostrar errores de validación para corrección.
    * Requerir confirmación explícita del profesor para crear o modificar la actividad.
    * Versionar la configuración aprobada y aplicar las reglas ya definidas de recalificación cuando se modifique una rúbrica vigente.
    * No permitir que la respuesta del proveedor aplique cambios por sí misma.

37. **RF-037 — Gestión de presupuestos del LLM**  
    **Usuarios:** Profesor / Worker

    El sistema deberá:
    * Aplicar presupuestos configurables a chat docente y evaluaciones que usan LLM.
    * Verificar los límites de tokens de entrada, salida, sesión docente, evaluación y worker antes de cada solicitud.
    * Considerar cuotas agregadas por actividad y límites de concurrencia cuando correspondan.
    * Autorizar o rechazar solicitudes según disponibilidad de presupuesto.

38. **RF-038 — Reserva y conciliación del consumo de tokens**  
    **Usuarios:** Profesor / Worker

    El sistema deberá:
    * Reservar de manera atómica un presupuesto máximo antes de iniciar una llamada al modelo.
    * Registrar el consumo reportado por el proveedor para tokens de entrada y salida, cuando sea posible.
    * Conciliar el uso registrado con las reservas y liberar las partes no consumidas cuando exista evidencia.
    * Evitar doble gasto por solicitudes concurrentes o duplicadas.
    * Mantener reservas conservadoras cuando una llamada falle sin reportar uso verificable, hasta su conciliación o expiración controlada.

39. **RF-039 — Persistencia de presupuestos entre reintentos**  
    **Usuario:** Worker

    El sistema deberá:
    * Asociar el consumo acumulado al identificador lógico de la evaluación, no solamente al worker o intento.
    * Conservar consumo y reservas entre checkpoints, interrupciones, nuevas asignaciones y reintentos.
    * Impedir que una reasignación reinicie el presupuesto de tokens.

40. **RF-040 — Manejo del agotamiento de tokens**  
    **Usuarios:** Profesor / Worker

    El sistema deberá:
    * Bloquear llamadas al LLM que excedan el presupuesto autorizado.
    * Informar al profesor que el chat no puede continuar por cuota cuando corresponda.
    * Permitir continuar únicamente etapas deterministas que no requieran llamadas al modelo.
    * Registrar la evaluación como parcial o no concluyente si faltan criterios necesarios, evitando asignar una nota arbitraria.
    * Escalar a revisión docente según la política definida.

41. **RF-041 — Registro de evidencia de confianza**  
    **Usuario:** Worker

    El sistema deberá:
    * Registrar por criterio pruebas ejecutadas, comprobaciones exitosas, errores, faltantes e incertidumbre relevante.
    * Distinguir evidencia determinista de juicios generados con apoyo del LLM.
    * Asociar las evidencias a entrega, SHA, rúbrica, intento y versión del evaluador/modelo que corresponda.

42. **RF-042 — Cálculo de confidence level**  
    **Usuarios:** Worker / Profesor

    El sistema deberá:
    * Producir una nota provisional cuando haya evidencia suficiente para calcularla.
    * Calcular un indicador de confianza basado en completitud, verificabilidad, errores e incertidumbre de la evaluación, de acuerdo con una política versionada.
    * Registrar nivel alto, medio o bajo y sus razones, con umbrales configurables todavía TBD.
    * Marcar **no concluyente** en lugar de asignar confianza o calificación ficticia cuando falte evidencia esencial.
    * No tratar una autodeclaración del LLM como evidencia suficiente de confianza.

43. **RF-043 — Visualización docente de nota y confianza**  
    **Usuario:** Profesor

    El sistema deberá:
    * Mostrar conjuntamente la nota provisional, el confidence level, su explicación y las evidencias relevantes.
    * Destacar confianza baja, criterios incompletos y evaluación no concluyente para revisión.
    * Mantener la decisión y publicación final en manos del profesor.

44. **RF-044 — Trazabilidad de uso del LLM y del skill**  
    **Usuarios:** Profesor / Worker

    El sistema deberá:
    * Registrar identificadores de solicitud, tipo de uso (chat o evaluación), proveedor, modelo y versión del skill cuando corresponda.
    * Registrar tokens presupuestados, consumidos y pendientes de conciliación; estado y motivo del fallo.
    * Asociar resultados del chat a la propuesta de actividad aprobada y resultados de evaluación a la entrega y rúbrica vigentes.
    * Restringir el acceso a esos registros según permisos y evitar guardar secretos en ellos.

45. **RF-045 — Configuración y seguimiento de cuotas**  
    **Usuarios beneficiados:** Profesor / Worker

    El sistema deberá:
    * Permitir gestionar mediante configuración operativa autorizada los límites de contexto, salida, sesión, evaluación, worker, actividad y concurrencia.
    * Exponer métricas y alertas de consumo, agotamiento, errores del proveedor y evaluaciones afectadas.
    * No requerir un nuevo usuario administrativo para realizar estas configuraciones dentro del alcance actual.



---

## Iteración 3 — Compatibilidad, coexistencia y transición del legacy de Arquitectura de Software

> **Origen: EQUIPO (supuestos del laboratorio).** El enunciado confirma que ya existe un sistema de corrección del curso de Arquitectura de Software en una laptop, pero no describe sus interfaces ni su base de datos. Para esta iteración, el equipo **asume** que ese sistema legacy posee contratos propios y almacenamiento independiente, y que será necesario mantenerlo operando durante una transición progresiva hacia Spotty. Los siguientes RF son de **ámbito SISTEMA**, no se atribuyen a Estudiante, Profesor ni Worker. No prescriben un patrón de arquitectura concreto.

46. **RF-046 — Compatibilidad con contratos legacy**  
    **Ámbito:** SISTEMA  
    **Origen:** EQUIPO

    El sistema deberá:
    * Permitir la interoperabilidad con los contratos existentes del sistema legacy de Arquitectura de Software durante el periodo de transición.
    * Adaptar las entradas y salidas necesarias para que los consumidores existentes puedan continuar operando sin modificaciones inmediatas de sus contratos.
    * Identificar y manejar incompatibilidades de datos o versiones de contrato sin alterar silenciosamente su significado.

47. **RF-047 — Acceso y preservación de información histórica legacy**  
    **Ámbito:** SISTEMA  
    **Origen:** EQUIPO

    El sistema deberá:
    * Permitir recuperar o incorporar las entregas, evaluaciones y calificaciones históricas necesarias del sistema legacy.
    * Conservar la relación entre cada registro histórico y sus identificadores de origen al consultarlo o incorporarlo a Spotty.
    * Evitar que la incorporación de información histórica publique o modifique automáticamente calificaciones oficiales vigentes.

48. **RF-048 — Coexistencia operativa entre legacy y Spotty**  
    **Ámbito:** SISTEMA  
    **Origen:** EQUIPO

    El sistema deberá:
    * Permitir que el legacy continúe atendiendo los procesos que aún no hayan sido transferidos a Spotty.
    * Identificar qué sistema debe atender cada operación comprendida en la transición.
    * Evitar el procesamiento contradictorio de una misma operación por ambos sistemas durante la coexistencia.

49. **RF-049 — Control de responsabilidad y consistencia de datos durante la transición**  
    **Ámbito:** SISTEMA  
    **Origen:** EQUIPO

    El sistema deberá:
    * Mantener identificada la fuente autoritativa de entregas, resultados y calificaciones según la fase de transición correspondiente.
    * Controlar la correspondencia entre identificadores legacy y Spotty cuando sea necesaria para la interoperabilidad o migración.
    * Detectar y manejar duplicaciones o conflictos antes de aceptar cambios que afecten la información académica vigente.

50. **RF-050 — Transición progresiva y reversión controlada**  
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

