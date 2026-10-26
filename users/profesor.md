# Profesor — Spotty

## Descripción del actor

**Profesor** es un actor **humano** de Spotty. Interactúa a través de plataforma web de escritorio.

## Objetivo

Su objetivo es administrar cursos y publicar calificaciones a partir de evidencia automática y revisión de excepciones.

## Necesidades y restricciones de profesor

### 1. Acceso y ámbito académico

Necesita poder:

* Iniciar y cerrar sesión mediante identidad institucional.
* Consultar y administrar solo cursos autorizados.
* Vincular y desvincular estudiantes de sus cursos.
* Consultar nómina de alumnos vinculados.

### 2. Gestión de actividades

Necesita poder:

* Crear actividades e indicar instrucciones, tipo de evaluación y deadline.
* Definir libremente rúbricas, criterios, puntajes, reglas y matices.
* Modificar actividades y rúbricas; conservar sus versiones.
* Provocar la recalificación de entregas afectadas al cambiar la rúbrica.

### 3. Creación asistida de actividades mediante chat

Necesita poder:

* Abrir una conversación para preparar una actividad dentro de uno de sus cursos autorizados.
* Describir en lenguaje natural los objetivos, contenidos, tipo de entrega y evaluación esperada.
* Utilizar un LLM conversacional de un proveedor externo, al cual Spotty carga directamente un skill de generación de actividades y configuración de evaluación.
* Obtener una propuesta editable de enunciado, rúbrica, criterios, pesos y parámetros de evaluación.
* Refinar la propuesta conversando con el modelo, dentro de límites de contexto, solicitudes y tokens.
* Revisar errores de validación de la propuesta y corregirlos manualmente o mediante el chat.
* Confirmar explícitamente la creación o modificación de la actividad; ninguna respuesta del modelo debe aplicarse por sí sola.
* Consultar advertencias cuando la cuota del chat esté agotada o el proveedor no esté disponible, sin perder los cambios ya guardados.

### 4. Supervisión de entregas

Necesita poder:

* Consultar enlaces GitHub, SHA y versiones registradas.
* Consultar cola, avance, fallos y estados de evaluación por actividad.
* Consultar evidencias técnicas y notas provisionales por rúbrica.

### 5. Confianza y revisión de resultados

Necesita poder:

* Consultar, junto con la nota provisional, el **confidence level** y los motivos o evidencias que lo sustentan.
* Distinguir evaluaciones completas con confianza alta, media o baja de evaluaciones **no concluyentes** sin nota confiable.
* Filtrar o identificar entregas que necesitan revisión debido a baja confianza, discrepancias o presupuesto de tokens agotado.
* Consultar el modelo, versión de rúbrica y el estado de los criterios evaluados cuando se haya usado un LLM.
* Tomar la decisión final de revisión y publicación; el confidence level no sustituye su criterio académico.

### 6. Revisión y publicación

Necesita poder:

* Revisar entregas no concluyentes, límites de tiempo y excepciones.
* Registrar correcciones o decisiones académicas justificadas.
* Aprobar y publicar notas.
* Conservar la nota publicada hasta aprobar una recalificación nueva.
* Consultar historial de cambios y publicaciones.

### 7. Seguimiento del plazo

Necesita poder:

* Consultar avance global de evaluaciones de sus cursos.
* Recibir alertas de riesgo para publicar notas dentro de las 48 horas posteriores al cierre.

## Acciones prohibidas

* No puede delegar en el LLM la publicación automática de actividades, rúbricas o notas sin su confirmación.
* No puede anular desde el chat los límites y permisos del sistema.


* No administra cursos ajenos.
* No accede directamente al plano de control de AWS ni a microVM de otros trabajos.
* No publica una nota provisional sin una acción docente de publicación.
* Los scripts de evaluación configurados, si los hay, no se ejecutan con permisos administrativos de Spotty.

## Consideraciones y límites

* Las propuestas generadas por el chat pasan validación técnica mínima (estructura, consistencia de puntajes y compatibilidad), distinta de una aprobación académica previa obligatoria de la rúbrica; el profesor sigue siendo responsable de su contenido.
* Más de un profesor autorizado por curso es un supuesto de diseño, no una exigencia del enunciado.

