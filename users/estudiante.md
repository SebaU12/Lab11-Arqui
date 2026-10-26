# Estudiante — Spotty

## Descripción del actor

**Estudiante** es un actor **humano** de Spotty. Interactúa a través de aplicación móvil.

## Objetivo

Su objetivo es registrar sus entregas académicas y conocer su avance y calificaciones.

## Necesidades y restricciones de estudiante

### 1. Autenticación institucional

Necesita poder:

* Iniciar y cerrar sesión con identidad institucional.
* Consultar únicamente información vinculada a su identidad y matrícula.

### 2. Consulta de cursos y actividades

Necesita poder:

* Ver cursos en los que está vinculado.
* Consultar actividades, instrucciones, rúbricas publicadas y fecha límite.

### 3. Entrega por GitHub

Necesita poder:

* Registrar el enlace del repositorio de su trabajo.
* Recibir confirmación de recepción con fecha del servidor y SHA de commit.
* Reentregar antes del deadline; la última versión válida será la única vigente, aunque tenga menor nota.
* Consultar su historial de versiones y el estado de la vigente.

### 4. Seguimiento de evaluación

Necesita poder:

* Consultar los estados recibida, en cola, evaluando, reanudando, evaluada, en revisión y publicada.
* Distinguir una entrega recibida de una evaluación completada.
* Recibir notificaciones push relevantes y consultar el estado actual al abrir la aplicación.

### 5. Consulta de calificaciones

Necesita poder:

* Consultar solo calificaciones publicadas.
* Conocer una nota actualizada únicamente después de la nueva publicación docente.
* Consultar historial de notas publicadas cuando corresponda.

## Acciones prohibidas

* No puede acceder al chat de configuración docente ni a la configuración interna del skill.
* No puede consultar el confidence level interno de las evaluaciones, salvo decisión académica posterior que lo habilite.


* No crea cursos ni actividades.
* No altera rúbricas, resultados técnicos ni calificaciones.
* No accede a trabajos o notas de otros estudiantes.
* No controla workers ni recursos de AWS.

## Consideraciones y límites

* El commit SHA identifica la versión registrada, pero no garantiza disponibilidad futura del repositorio.
* El estudiante puede consultar su entrega aunque todavía no haya capacidad de ejecución.
* Una evaluación inconclusa por falta de presupuesto de tokens no implica automáticamente una nota desaprobatoria.

