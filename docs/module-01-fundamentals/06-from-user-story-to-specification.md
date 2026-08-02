# De User Story a Specification

## Introducción

En la mayoría de organizaciones que utilizan metodologías ágiles, Azure DevOps, Jira u otras herramientas similares son el punto de entrada para nuevas funcionalidades.

Normalmente el flujo comienza con una User Story:

```text
Como usuario quiero realizar una acción
para obtener un beneficio determinado.
```

La User Story es una excelente forma de capturar intención de negocio.

Sin embargo, para desarrollar software complejo necesitamos transformar esa intención en conocimiento estructurado.

Ese proceso es uno de los objetivos principales de Specification-Driven Development.

---

# El flujo tradicional

Un flujo común en equipos ágiles es:

```text
Azure DevOps

    ↓

User Story

    ↓

Developer analiza

    ↓

Código

    ↓

Testing

    ↓

Release
```

El problema es que una gran parte del análisis ocurre dentro de la cabeza de las personas.

Ejemplo:

Un desarrollador lee:

> "Como cliente quiero ver mis beneficios disponibles."

Y debe descubrir:

* ¿Qué beneficios existen?
* ¿Cómo se calculan?
* ¿Qué usuarios pueden verlos?
* ¿Qué API existe?
* ¿Cómo se manejan errores?
* ¿Qué estados debe tener la pantalla?

Ese conocimiento normalmente queda distribuido.

---

# El flujo con SDD

SDD agrega una etapa explícita:

```text
Azure DevOps

    ↓

User Story

    ↓

Specification

    ↓

Design

    ↓

Tasks

    ↓

Implementation

    ↓

Tests
```

La Specification actúa como puente entre negocio y tecnología.

---

# Ejemplo práctico

Supongamos esta User Story:

```text
US-4587

Como cliente

quiero consultar mis beneficios disponibles

para conocer las promociones que puedo utilizar.
```

Esta historia tiene intención.

Ahora debemos convertirla en una Specification.

---

# Paso 1 - Context

Primero documentamos el problema.

Archivo:

```text
spec.md
```

Ejemplo:

```markdown
## Context

Actualmente los clientes deben comunicarse
con atención al cliente para conocer sus beneficios.

Queremos permitir que puedan consultar
sus beneficios desde el portal web.
```

La pregunta que responde:

> ¿Por qué hacemos este cambio?

---

# Paso 2 - Objetivo

Definimos el resultado esperado.

Ejemplo:

```markdown
## Goal

Permitir que clientes autenticados puedan
visualizar sus beneficios disponibles
desde el portal.
```

La pregunta:

> ¿Qué queremos lograr?

---

# Paso 3 - Requirements

Transformamos la historia en comportamientos verificables.

Archivo:

```text
requirements.md
```

Ejemplo:

```markdown
# Requirement R001

The user must be authenticated.

Given:
A user without authentication.

When:
The user accesses benefits page.

Then:
The system redirects to login.
```

---

Segundo requisito:

```markdown
# Requirement R002

The user can see available benefits.

Given:
A customer with active benefits.

When:
The customer opens benefits page.

Then:
The system displays available benefits.
```

---

# Paso 4 - Business Rules

Aquí documentamos reglas que normalmente quedan ocultas.

Ejemplo:

```markdown
## Business Rules

BR001

Only active customers can see benefits.


BR002

Expired benefits must not be displayed.


BR003

Benefits depend on customer category.
```

---

# Paso 5 - Design

Ahora definimos cómo construiremos la solución.

Archivo:

```text
design.md
```

Ejemplo:

```markdown
## Frontend

Components:

BenefitsPageComponent

Services:

BenefitsService


State:

BenefitsStore
```

---

Backend:

```markdown
## API

GET

/api/customers/{id}/benefits
```

---

# Paso 6 - Tasks

La Specification se transforma en trabajo ejecutable.

Archivo:

```text
tasks.md
```

Ejemplo:

```markdown
TASK-001

Create benefits page component.


TASK-002

Implement benefits service.


TASK-003

Add loading and error states.


TASK-004

Create unit tests.
```

---

# Paso 7 - Test Plan

Los requisitos generan validaciones.

Archivo:

```text
test-plan.md
```

Ejemplo:

```markdown
Scenario:

Authenticated customer with benefits.


Expected:

Benefits are displayed.
```

---

# Resultado final

La User Story inicial:

```text
Como cliente quiero ver mis beneficios.
```

se transforma en:

```text
specs/

└── customer-benefits/

    ├── spec.md

    ├── requirements.md

    ├── design.md

    ├── tasks.md

    └── test-plan.md
```

Ahora existe un contexto completo.

---

# Relación con Azure DevOps

SDD no reemplaza Azure DevOps.

Lo complementa.

Un modelo posible:

```text
Azure DevOps

Epic
 |
 Feature
 |
 User Story
 |
 Task


        +

OpenSpec

Specification
 |
 Requirements
 |
 Design
 |
 Tests
```

---

# ¿Dónde vive cada cosa?

## Azure DevOps

Responsable de:

* planificación;
* seguimiento;
* estados;
* asignaciones;
* métricas.

---

## OpenSpec

Responsable de:

* conocimiento técnico;
* comportamiento esperado;
* decisiones;
* contexto.

---

## Git

Responsable de:

* versionar código;
* versionar Specifications;
* relacionar cambios.

---

# Uso con GitHub Copilot y Claude Code

Una vez creada la Specification, la IA recibe contexto.

Ejemplo:

```text
Implement TASK-002.

Read:

/specs/customer-benefits/

Files:

- spec.md
- requirements.md
- design.md

Rules:

- Follow existing Angular architecture.
- Use Signals.
- Add Jest tests.
```

La IA ya no necesita adivinar.

---

# Beneficio principal

La transformación:

```text
User Story

"Qué queremos"

        +

Specification

"Qué significa exactamente"

        +

Design

"Cómo lo construiremos"

        +

Tests

"Cómo sabemos que funciona"
```

genera una cadena completa de conocimiento.

---

# Errores comunes

## Convertir User Story directamente en código

Incorrecto:

```text
Story

↓

Prompt IA

↓

Código
```

---

Correcto:

```text
Story

↓

Specification

↓

Prompt IA

↓

Código
```

---

## Crear Specifications demasiado grandes

Incorrecto:

```text
Customer Platform
```

Correcto:

```text
Customer Benefits Feature
```

---

## Crear documentación después

La Specification debe formar parte del cambio.

No es documentación histórica.

---

# Resumen

Transformar User Stories en Specifications permite:

* reducir ambigüedad;
* alinear equipos;
* mejorar colaboración;
* entregar contexto a IA;
* mantener trazabilidad.

La User Story explica una necesidad.

La Specification transforma esa necesidad en una solución construible.

---

# Próximo capítulo

El siguiente archivo será:

```text
07-sdd-and-ai-development.md
```

donde veremos cómo SDD cambia la forma de trabajar con GitHub Copilot, Claude Code y agentes de IA.
