# Tasks y plan de ejecución en OpenSpec

## Introducción

Una Specification define:

* qué problema resolvemos;
* qué comportamiento esperamos;
* cómo será construida la solución.

Pero todavía falta responder:

> ¿Qué pasos concretos debemos ejecutar para construirla?

El archivo `tasks.md` transforma una Specification en un plan de trabajo accionable.

---

# De Design a Tasks

La relación completa es:

```text id="m5v8kx"
Business Need

      ↓

Specification

      ↓

Requirements

      ↓

Design

      ↓

Tasks

      ↓

Implementation
```

---

# ¿Qué es una Task?

Una Task es una unidad concreta de trabajo.

Debe responder:

* ¿qué hay que hacer?
* ¿por qué?
* ¿qué parte de la Specification implementa?
* ¿cómo sabemos que está terminada?

---

Ejemplo:

```markdown id="z2p8mq"
TASK-001

Title:

Create benefits page component.


Description:

Implement the UI required
to display customer benefits.


Related Requirement:

R002


Validation:

Component tests completed.
```

---

# Task versus User Story

Estos conceptos suelen confundirse.

## User Story

Representa valor de negocio.

Ejemplo:

```text id="a8m3qy"
Como cliente quiero ver mis beneficios.
```

---

## Task

Representa trabajo técnico.

Ejemplo:

```text id="s7k2nf"
Create BenefitsPageComponent.
```

---

La relación:

```text id="c4p9vx"
User Story

      ↓

Specification

      ↓

Requirements

      ↓

Tasks
```

---

# Características de una buena Task

Una Task debe ser:

## Específica

Incorrecto:

```text id="1r5m7z"
Implement benefits.
```

Demasiado amplio.

---

Correcto:

```text id="8x2q7m"
Create BenefitsService
to consume customer benefits API.
```

---

## Limitada

Una Task debe tener un alcance claro.

Incorrecto:

```text id="y4v8sd"
Implement entire customer platform.
```

---

Correcto:

```text id="k8m1pz"
Add benefits loading state.
```

---

## Verificable

Debe poder determinarse si terminó.

Ejemplo:

```text id="n3x7wv"
Done when:

- Component renders benefits.
- Tests pass.
```

---

# Tipos de Tasks

Una Specification normalmente tiene diferentes tipos de tareas.

---

# 1. Development Tasks

Implementación directa.

Ejemplo:

```text id="f5z8kh"
TASK-001

Create BenefitsComponent.
```

---

# 2. Integration Tasks

Conexión con sistemas existentes.

Ejemplo:

```text id="q9m3vb"
TASK-002

Integrate BenefitsService
with API endpoint.
```

---

# 3. Testing Tasks

Validación.

Ejemplo:

```text id="w6p1cz"
TASK-003

Create unit tests
for benefits states.
```

---

# 4. Documentation Tasks

Actualización de conocimiento.

Ejemplo:

```text id="r7k2mn"
TASK-004

Update API documentation.
```

---

# 5. Migration Tasks

Cambios evolutivos.

Ejemplo:

```text id="t4m9vx"
TASK-005

Migrate existing component
to new architecture pattern.
```

---

# Organización de tareas

Una Specification puede organizar tareas por fases.

Ejemplo:

```markdown id="b7q3xp"
# Tasks


## Phase 1 - Backend

TASK-001

Create benefits endpoint.


## Phase 2 - Frontend

TASK-002

Create benefits component.


## Phase 3 - Testing

TASK-003

Add automated tests.
```

---

# Dependencias entre Tasks

No todas las tareas son independientes.

Ejemplo:

```text id="p8m2qw"
TASK-001

Create API


       ↓


TASK-002

Create Frontend Integration


       ↓


TASK-003

Create End-to-End Tests
```

---

Esto permite definir orden de ejecución.

---

# Task Metadata

Para equipos grandes es útil agregar información adicional.

Ejemplo:

```markdown id="x3n7mv"
TASK-001


Owner:

Frontend Team


Priority:

High


Dependencies:

API Contract


Related:

R002
```

---

# Tasks y Azure DevOps

En tu escenario actual:

Azure DevOps puede continuar gestionando:

* backlog;
* sprint;
* asignación;
* seguimiento.

OpenSpec agrega contexto.

Modelo:

```text id="u7m4pz"
Azure DevOps

User Story

        ↓


OpenSpec

tasks.md

        ↓


Azure DevOps Tasks
```

---

# Dos estrategias posibles

## Estrategia 1 - Tasks en Azure DevOps

La Specification define las tareas.

Azure DevOps las representa como work items.

Ejemplo:

```text id="x5m9kc"
OpenSpec

TASK-001


        ↕

Azure DevOps

Task #45821
```

---

## Estrategia 2 - Tasks versionadas en Git

Las tareas viven junto al código.

Ejemplo:

```text id="w8q2vn"
repository/

specs/

customer-benefits/

tasks.md
```

---

En equipos maduros normalmente se utilizan ambas.

---

# Tasks y agentes IA

Este punto es clave.

Una Task bien definida puede convertirse en una instrucción para un agente.

Ejemplo:

```text id="d3m8qx"
Implement TASK-002.


Specification:

customer-benefits


Task:

Create BenefitsService.


Requirements:

R002


Constraints:

- Use existing HTTP client.
- Follow service patterns.


Validation:

Add Jest tests.
```

---

La IA no recibe solamente:

> "crea un servicio"

Recibe:

* propósito;
* restricciones;
* arquitectura;
* validación.

---

# Task como unidad de ejecución

Podemos pensar una Task como:

```text id="m2x7vn"
Specification

      ↓

Task

      ↓

AI Agent / Developer

      ↓

Code Change

      ↓

Review
```

---

# Definition of Done para Tasks

Una Task no debería considerarse completa solamente porque existe código.

Ejemplo:

```text id="k9p4vz"
Task completed when:

✓ Code implemented

✓ Tests created

✓ Specification updated

✓ Review approved
```

---

# Ejemplo completo

Specification:

```text id="h8m4qp"
Customer Invoice Download
```

Tasks:

```markdown id="w2c6mz"
TASK-001

Create invoice download endpoint.


TASK-002

Add download button.


TASK-003

Handle loading state.


TASK-004

Handle authorization errors.


TASK-005

Add automated tests.
```

---

# Errores comunes

## Crear tareas antes del Design

Incorrecto:

```text id="q4v9xn"
Create component.
```

sin saber arquitectura.

---

Correcto:

```text id="m7p2kc"
Design defines component.

Task implements component.
```

---

## Tasks demasiado grandes

Incorrecto:

```text id="b3x8mq"
Implement customer module.
```

---

## Tasks sin relación con Requirements

Una Task debe responder:

> ¿Qué requisito estoy implementando?

---

# Checklist de tasks

Antes de aprobar:

✅ ¿Cada task tiene un objetivo claro?
✅ ¿Está relacionada con un requirement?
✅ ¿Puede validarse?
✅ ¿Tiene dependencias conocidas?
✅ ¿Puede ser ejecutada por una persona o agente?

---

# Resumen

El archivo `tasks.md` convierte una Specification en ejecución.

La cadena completa queda:

```text id="n8m3vp"
Business Goal

      ↓

Specification

      ↓

Requirements

      ↓

Design

      ↓

Tasks

      ↓

Code

      ↓

Tests
```

Una buena Task reduce la distancia entre intención y código.

---

# Próximo capítulo

El siguiente archivo será:

```text id="c5z8mq"
docs/module-02-openspec/

└── 08-spec-versioning-and-git-workflow.md
```

donde veremos cómo versionar Specifications junto al código y cómo integrarlas con Pull Requests, ramas y flujos reales de desarrollo.
