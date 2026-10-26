# Worker — Spotty

## Descripción del actor

**Worker** es un actor **técnico automatizado** de Spotty. Interactúa a través de plano de ejecución sobre AWS Spot.

## Objetivo

Su objetivo es ejecutar de forma aislada evaluaciones autorizadas, persistir resultados y recuperar avances cuando falla la capacidad Spot.

## Necesidades y restricciones de worker

### 1. Asignación de trabajo

Necesita poder:

* Tomar evaluaciones autorizadas de la cola CPU (Programación/Arquitectura) o GPU (IA).
* Respetar versiones vigentes, prioridades y cancelaciones informadas por el orquestador.
* Usar el SHA registrado para recuperar el contenido evaluable del repositorio.

### 2. Preparación y aislamiento

Necesita poder:

* Obtener la imagen base del curso, reutilizando la caché del nodo cuando exista.
* Preparar una microVM individual para la ejecución de código no confiable.
* Realizar análisis preventivo básico de contenido sospechoso sin asumir que el escaneo detecta todos los bucles o ataques.
* Ejecutar código, pruebas, análisis de diagramas o evaluaciones de IA de acuerdo con la tarea y la rúbrica.

### 3. Límites y evidencia

Necesita poder:

* Aplicar los límites asignados de duración, CPU, GPU, memoria, disco y procesos.
* Generar resultados técnicos por etapa y reportar fallos de código o límites excedidos.
* Solicitar decisión de ampliación de tiempo cuando corresponda; no ampliarlo de forma autónoma sin límite.
* Enviar resultados para calificación, sin publicar notas.

### 4. Uso controlado del LLM y presupuesto de tokens

Necesita poder:

* Identificar si una etapa de evaluación realmente requiere llamadas al LLM del proveedor; pruebas deterministas no gastan tokens de modelo.
* Solicitar autorización y reservar un presupuesto máximo antes de cada llamada al LLM.
* Respetar límites configurables por llamada (entrada/salida), por evaluación, por worker y por periodo, así como límites de concurrencia.
* Reportar tokens consumidos y metadatos de la llamada para conciliar reservas con consumo real.
* Mantener el presupuesto acumulado de la evaluación entre checkpoints, interrupciones, reintentos y reasignaciones a otro worker.
* Recibir rechazo explícito cuando no exista presupuesto y continuar solo con etapas que no necesiten el modelo, cuando sea posible.
* Marcar el resultado como incompleto/no concluyente para revisión cuando el agotamiento impida evaluar criterios necesarios.
* No realizar llamadas directas al proveedor eludiendo el componente autorizado de control de presupuesto.

### 5. Calificación provisional, evidencia y confidence level

Necesita poder:

* Reportar por criterio los resultados de pruebas, evidencias verificables, fallos, etapas incompletas y señales de incertidumbre.
* Producir o enviar los insumos de una calificación provisional según la rúbrica vigente, sin publicar una nota oficial.
* Reportar junto con la nota provisional un confidence level estimado por el mecanismo de confianza de Spotty, con su justificación y versión de cálculo.
* Tratar el confidence level como señal de calidad de evidencia, no como probabilidad matemática demostrada de exactitud.
* Identificar por separado el estado **no concluyente** cuando no exista evidencia suficiente para calcular una nota.
* Entregar a revisión docente los resultados de confianza baja o evaluación inconclusa.

### 6. Checkpoints y recuperación

Necesita poder:

* Persistir progreso por etapas y periódicamente en trabajos largos que permitan reanudación.
* Subir archivos de checkpoint al almacenamiento persistente y registrar sus metadatos.
* Restaurar el último progreso válido cuando el orquestador reasigne una evaluación.
* Aceptar que ciertas ejecuciones solo pueden reiniciarse desde una etapa y no desde el estado exacto del proceso.

### 7. Detección y finalización

Necesita poder:

* Emitir heartbeats mientras está activo.
* Atender avisos de interrupción Spot dejando de aceptar nuevas tareas y guardando el último progreso posible.
* Reportar finalización, errores o imposibilidad de completar la evaluación.
* Liberar microVM y recursos después de terminar o cancelar.
* Enviar resultados solo si el intento sigue autorizado mediante verificación atómica.

## Acciones prohibidas

* No puede consumir tokens ilimitados ni reiniciar cuotas debido a una interrupción Spot.
* No puede inventar un confidence level, ni considerarlo suficiente sin evidencia asociada.
* No puede publicar una nota provisional o convertir un resultado inconcluso en aprobado.


* No cambia el repositorio original ni la versión vigente.
* No modifica rúbricas, permisos, cursos o notas oficiales.
* No puede leer otras entregas o checkpoints no asignados.
* No ejecuta código no confiable en servicios de control ni utiliza credenciales privilegiadas.
* No garantiza que AWS Spot proporcione capacidad cuando se solicita.

## Consideraciones y límites

* Worker es actor técnico interno, no usuario humano externo.
* CPU y GPU son dos perfiles del mismo actor.
* La recuperación exacta de estado depende de cada programa y tecnología.

