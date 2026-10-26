# Requerimientos No Funcionales — Spotty v4 — Definición cerrada para laboratorio

> **Alcance:** atributos de calidad de la plataforma completa y del motor de ejecución. Para este laboratorio, las variables ausentes del enunciado se cierran con **supuestos operativos del EQUIPO** (valores de diseño, no hechos de la UTC ni garantías de AWS). Origen: **CASO** = enunciado oficial, **EQUIPO** = decisiones conversadas, **CURSO** = principio metodológico.

## RNF-001 — Seguridad y aislamiento

**Origen:** EQUIPO  
**Requisito:** Cada entrega de código no confiable deberá ejecutarse en su propio entorno microVM aislado, con restricciones de red, procesos, CPU, memoria y almacenamiento.

## RNF-002 — Autorización académica

**Origen:** EQUIPO  
**Requisito:** Las consultas y modificaciones deberán respetar identidad institucional, rol y vinculación con cursos; los workers solo accederán a datos de su evaluación autorizada.

## RNF-003 — Protección de credenciales

**Origen:** EQUIPO  
**Requisito:** El código del estudiante no deberá recibir credenciales institucionales ni privilegios de administración del plano central.

## RNF-004 — Perfiles de ejecución

**Origen:** CASO  
**Requisito:** La solución deberá soportar los perfiles de corrección de Programación, Arquitectura e IA. Se interpretan los P99 de 1 minuto (Programación), 10 minutos (Arquitectura) y 40 minutos o más (IA) como latencia de procesamiento de la evaluación desde el inicio efectivo del worker hasta producir el resultado técnico, excluyendo espera de cola y publicación docente. Para pruebas del laboratorio se adopta P99 objetivo de 40 minutos en trabajos IA estándar; los trabajos de IA extendidos se clasifican y reportan por separado sin prometer ese umbral.

## RNF-005 — Carga en deadline

**Origen:** CASO  
**Requisito:** El sistema deberá diseñarse para una carga concentrada de entregas en los últimos 30 minutos previos al cierre de la actividad, modelando, como supuesto del equipo, 1,200 alumnos distribuidos en 30 cursos, 80 % de 1,200 entregas dentro de esa ventana (960 entregas/30 min, media de 0.53 entregas/segundo) y un factor de pico de 5 veces esa media (2.67 entregas/segundo). Se probará además un escenario de estrés de 4,800 entregas/30 min.

## RNF-006 — Escalabilidad diferenciada

**Origen:** EQUIPO  
**Requisito:** La capacidad de procesamiento deberá poder variar independientemente para CPU y GPU según trabajo pendiente y utilización de CPU, GPU y memoria.

## RNF-007 — Disponibilidad de la plataforma

**Origen:** EQUIPO  
**Requisito:** La consulta de cursos, entregas y notas deberá poder funcionar aunque temporalmente no haya capacidad Spot para nuevas evaluaciones.

## RNF-008 — Alta disponibilidad de persistencia

**Origen:** EQUIPO  
**Requisito:** La base de datos académica y de estado de evaluación deberá emplear replicación y failover; la durabilidad de checkpoints no deberá depender del disco del worker.

## RNF-009 — Confiabilidad ante interrupción Spot

**Origen:** EQUIPO  
**Requisito:** Una entrega aceptada no deberá desaparecer por el reclamo de un worker. Deberá poder reprogramarse desde el último progreso recuperable, o repetir una etapa cuando el estado exacto no se pueda restaurar.

## RNF-010 — Ventana de aviso de AWS Spot

**Origen:** CASO  
**Requisito:** El diseño deberá contemplar que AWS puede reclamar la instancia con aproximadamente 2 minutos de aviso y que puede no existir capacidad Spot de reemplazo.

## RNF-011 — Consistencia e idempotencia

**Origen:** EQUIPO  
**Requisito:** Un resultado obsoleto, duplicado o procedente de una versión reemplazada no deberá modificar la nota vigente. Las transiciones críticas deberán ser atómicas.

## RNF-012 — Límites de ejecución

**Origen:** EQUIPO  
**Requisito:** Cada sandbox tendrá límite de 2 vCPU, 4 GiB RAM, 10 GiB de disco efímero y 128 procesos para Programación; 4 vCPU, 8 GiB RAM, 15 GiB y 128 procesos para Arquitectura; y 8 vCPU, 24 GiB RAM, 30 GiB y una GPU compatible para IA. La ejecución máxima será de 3, 20 y 90 minutos respectivamente; se permite una ampliación docente de hasta 50 % del límite inicial por intento, una sola vez. Exceder memoria o tiempo finalizará el intento con evidencia para revisión, sin castigar automáticamente al estudiante por fallo de infraestructura.

## RNF-013 — Eficiencia de imágenes

**Origen:** CASO/EQUIPO  
**Requisito:** El diseño deberá considerar imágenes base por curso de 3 a 5 GB y permitir reutilizarlas desde la caché local mientras el nodo exista.

## RNF-014 — Cumplimiento de plazo

**Origen:** CASO/EQUIPO  
**Requisito:** El diseño deberá buscar que los profesores puedan publicar notas como máximo 48 horas después del cierre, monitoreando el riesgo; no se afirmará garantía absoluta si AWS Spot carece de capacidad.

## RNF-015 — Trazabilidad de evaluación

**Origen:** EQUIPO  
**Requisito:** Deberá conservarse evidencia de qué SHA, versión de rúbrica, intento, checkpoint y resultados técnicos produjeron cada nota provisional o publicada.

## RNF-016 — Trazabilidad de notas

**Origen:** EQUIPO  
**Requisito:** Toda recalificación y publicación posterior deberá conservar historial; una nota publicada no se reemplazará sin nueva publicación docente.

## RNF-017 — Disponibilidad de API

**Origen:** EQUIPO  
**Requisito:** Los contratos para web y mobile deberán ser atendidos por backends stateless con réplicas y balanceo de carga.

## RNF-018 — Degradación parcial

**Origen:** EQUIPO  
**Requisito:** La indisponibilidad del servicio push no deberá impedir que el estudiante consulte su estado o nota publicada.

## RNF-019 — Observabilidad

**Origen:** EQUIPO  
**Requisito:** Deberán observarse tamaño y espera de colas, evaluaciones activas, interrupciones, fallos, heartbeats, utilización CPU/GPU/memoria y riesgo de plazo.

## RNF-020 — Modularidad

**Origen:** CURSO  
**Requisito:** La solución deberá mantener responsabilidades coherentes, alta cohesión y bajo acoplamiento entre gestión académica, evaluación y ejecución.

## RNF-021 — Usabilidad

**Origen:** EQUIPO  
**Requisito:** La app del estudiante y la web docente deberán presentar estados, resultados y errores en términos comprensibles para sus respectivos usuarios.

## RNF-022 — Capacidad mínima deseada

**Origen:** EQUIPO  
**Requisito:** Como objetivo de operación, el orquestador solicitará al menos dos instancias Spot por pool CPU y GPU cuando exista demanda y cuota aprobada; el mínimo real podrá ser cero si Spot no dispone de capacidad. Se fija un techo de 12 instancias CPU y 6 GPU solicitadas, con máximo de 4 sandboxes simultáneos por host CPU y 1 por host GPU, sujeto a los recursos reales del host. El control de admisión impedirá sobreasignación de memoria.

## RNF-023 — Compatibilidad de GPU

**Origen:** EQUIPO  
**Requisito:** La recuperación de tareas GPU deberá tener en cuenta la compatibilidad del estado recuperable con el hardware seleccionado; donde no sea compatible se requerirá repetición desde etapa válida.

## Acuerdos cuantitativos de la iteración 1 (supuestos EQUIPO)

- **Carga de referencia:** 30 cursos, 1,200 estudiantes, 960 entregas en los últimos 30 minutos, pico de admisión 2.67 entregas/s; estrés 4,800 entregas/30 min.
- **API:** P95 de inicio de sesión <= 1.5 s; P95 de aceptación de entrega <= 2 s; P95 de consulta de estado <= 800 ms. Disponibilidad mensual objetivo del plano académico: 99.9 %, medida sin penalizar falta de capacidad Spot para la evaluación asíncrona.
- **Persistencia:** RPO objetivo <= 5 min y RTO objetivo <= 30 min para servicios de control y datos académicos; una entrega confirmada debe contar con registro durable antes de responder.
- **Checkpoints:** tareas de Programación guardan evidencia al final de cada prueba; Arquitectura al terminar cada etapa o cada 3 min; IA cada 5 min o por época cuando sea viable. Checkpoint individual <= 2 GiB; si excede ese tamaño se conserva un resultado por etapa, no la imagen exacta del proceso.
- **Interrupción:** al aviso Spot se cesa admisión inmediata de nuevas tareas y se intenta subir un checkpoint en 90 s; si no concluye, se reinicia desde el último checkpoint durable.
- **Supervisión:** heartbeat cada 15 s; tras 60 s sin heartbeat un intento queda sospechoso y tras 120 s se considera recuperable por reasignación, previa invalidación atómica del lease anterior.
- **Escalamiento:** reevaluación cada 60 s; solicitar ampliación cuando la espera estimada > 5 min para CPU o > 15 min para GPU o utilización de memoria > 75 % por 3 min; reducción tras 15 min sin trabajos y sin ejecuciones activas. La solicitud nunca constituye garantía de capacidad Spot.
- **Presupuesto de laboratorio:** techo referencial mensual de USD 1,500 para workers Spot y almacenamiento temporal de evaluación; gasto real sujeto a los precios Spot efectivos. Cuando se alcance el techo, se retienen evaluaciones en cola y se alerta por riesgo del plazo académico.
- **Disponibilidad de procesamiento:** Spot puede no ofrecer capacidad; las metas P99 aplican a trabajos que efectivamente inician y no constituyen garantía absoluta del plazo de 48 h.

---

## Iteración 2 — Requisitos de calidad para LLM y confianza

## RNF-024 — Límites finitos de tokens

**Origen:** EQUIPO  
**Requisito:** Toda llamada a un LLM deberá estar sujeta a límites configurables de tokens de entrada, salida, contexto y presupuesto acumulado según el origen de uso. Se aplican los límites concretos del cuadro de políticas del laboratorio incluido al final de la iteración 2.

## RNF-025 — Aislamiento de presupuestos

**Origen:** EQUIPO  
**Requisito:** El consumo concurrente de chat y evaluaciones no deberá eludir los presupuestos por sesión, evaluación, worker y actividad; las reservas deberán gestionarse de forma atómica.

## RNF-026 — Durabilidad y no reinicio de consumo

**Origen:** EQUIPO  
**Requisito:** La contabilidad de consumo y reservas deberá persistir fuera de la instancia Spot y sobrevivir a reintentos, interrupciones y reasignaciones, sin volver a disponer del presupuesto gastado.

## RNF-027 — Protección frente a respuestas no confiables del proveedor

**Origen:** EQUIPO  
**Requisito:** El texto generado por el LLM, incluidos resultados del skill y contenido de repositorios estudiantiles, se tratará como entrada no confiable. No podrá alterar permisos, ejecutar herramientas no autorizadas ni efectuar publicaciones sin validación y aprobación docente.

## RNF-028 — Privilegios mínimos para integración LLM

**Origen:** EQUIPO  
**Requisito:** La integración con el proveedor y el skill solo deberá disponer de contexto y herramientas necesarios para cada tarea; no tendrá acceso administrativo a cursos, notas oficiales, credenciales ni al plano de control de workers.

## RNF-029 — Degradación ante indisponibilidad o cuota agotada

**Origen:** EQUIPO  
**Requisito:** Una falla del proveedor LLM, la saturación de llamadas o el agotamiento de tokens no deberá inutilizar el resto de la plataforma ni convertir automáticamente una evaluación inconclusa en nota desaprobatoria.

## RNF-030 — Explicabilidad del confidence level

**Origen:** EQUIPO  
**Requisito:** Todo confidence level emitido deberá acompañarse de evidencia y de la versión de la regla de cálculo. Una cifra producida exclusivamente por autovaloración del LLM no será válida como medida de confianza.

## RNF-031 — Separación entre confianza y calificación

**Origen:** EQUIPO  
**Requisito:** El indicador de confianza no deberá modificar directamente el puntaje obtenido según rúbrica ni reemplazar la revisión humana; los resultados no concluyentes deberán diferenciarse de notas bajas.

## RNF-032 — Trazabilidad del proveedor y del skill

**Origen:** EQUIPO  
**Requisito:** Deberán registrarse el proveedor, identificadores de modelo y skill, versiones relevantes, presupuestos, uso reportado y resultados sin exponer secretos ni almacenar datos sensibles innecesariamente.

## RNF-033 — Observabilidad y control de costos

**Origen:** EQUIPO  
**Requisito:** Se deberán monitorizar consumo de tokens de entrada y salida, reservas pendientes, errores de proveedor, saturación, llamadas rechazadas, presupuestos agotados y costo estimado por actividad y evaluación.

## RNF-034 — Límites configurables y verificables

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

## Iteración 3 — Compatibilidad y transición del sistema legacy

> **Origen:** EQUIPO. Para el laboratorio se asume que el sistema existente de corrección del curso de Arquitectura de Software mantiene contratos de integración y persistencia propios. Estos atributos complementan los RNF anteriores; no imponen todavía un patrón de migración. Para este ejercicio el EQUIPO fija los contratos, ventanas y metas detallados a continuación.

## RNF-035 — Compatibilidad retroactiva de contratos

**Origen:** EQUIPO  
**Atributo:** Compatibilidad / Interoperabilidad  
**Requisito:** Durante el período de coexistencia, las interfaces existentes del sistema legacy que se declaren vigentes deberán mantener un comportamiento compatible para sus consumidores autorizados. Los cambios de formato, semántica o versión deberán gestionarse explícitamente, sin exigir una migración simultánea de todos los consumidores.

## RNF-036 — Integridad y trazabilidad de información migrada

**Origen:** EQUIPO  
**Atributo:** Integridad / Consistencia / Trazabilidad  
**Requisito:** La integración o migración de entregas, evaluaciones y calificaciones históricas deberá preservar su correspondencia con alumno, curso, actividad, versión y estado, según los datos disponibles en el legacy. Se deberán detectar registros duplicados o conflictivos, identificar el origen y registrar las transformaciones aplicadas. No se considerará exitosa una migración con pérdida silenciosa de información.

## RNF-037 — Continuidad operativa durante la transición

**Origen:** EQUIPO  
**Atributo:** Disponibilidad / Reliability  
**Requisito:** La transición del legacy a Spotty deberá minimizar interrupciones de las operaciones académicas vigentes. Un fallo de integración o de una etapa de migración no deberá bloquear indiscriminadamente los cursos ya operativos en la plataforma que no dependan de esa etapa; el alcance de cualquier degradación deberá ser explícito y observable.

## RNF-038 — Reversibilidad y recuperación controlada de la migración

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

