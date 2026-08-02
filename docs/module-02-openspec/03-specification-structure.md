# Estructura de una Specification OpenSpec

## Introducción

Una Specification no debe ser un documento libre donde cada equipo escribe información diferente.

Para que SDD funcione a escala, necesitamos una estructura consistente.

OpenSpec propone organizar el conocimiento de una funcionalidad mediante artefactos con responsabilidades claras.

Una Specification debe permitir responder:

* ¿Por qué existe este cambio?
* ¿Qué comportamiento esperamos?
* ¿Qué reglas aplican?
* ¿Cómo será implementado?
* ¿Cómo verificamos que funciona?

---

# Anatomía de una Specification

Una Specification típica tiene la siguiente estructura:

```text
specs/

└── feature-name/

    ├── spec.md
    ├── requirements.md
    ├── design.md
    ├── tasks.md
    ├── test-plan.md
    └── decisions/
```

Cada archivo tiene un propósito específico.

---

# 1. spec.md

## El contexto y propósito

Este es el documento principal.

Su responsabilidad es explicar:

* qué problema resolvemos;
* por qué existe la funcionalidad;
* cuál es el objetivo;
* cuál es el alcance.

No debe contener detalles excesivamente técnicos.

---

Ejemplo:

```markdown
# Customer Benefits


## Context

Actualmente los clientes no pueden consultar
sus beneficios disponibles.


## Goal

Permitir que clientes autenticados visualicen
sus beneficios desde el portal.


## Scope

Included:

- Visualización de beneficios.
- Fecha de expiración.


Excluded:

- Activación de beneficios.
- Compra de beneficios.
```

---

## Pregunta que responde

> ¿Qué estamos construyendo y por qué?

---

# 2. requirements.md

## Comportamiento esperado

Este archivo transforma la intención en requisitos verificables.

Aquí viven:

* reglas funcionales;
* escenarios;
* criterios de aceptación.

---

Ejemplo:

```markdown
# Requirement R001

## Authentication

Given:

A user without authentication.

When:

The user accesses benefits.

Then:

The system redirects to login.
```

---

Otro requisito:

```markdown
# Requirement R002

## Display Benefits

Given:

An authenticated customer.

When:

The customer opens benefits page.

Then:

Available benefits are displayed.
```

---

## Pregunta que responde

> ¿Qué debe hacer el sistema?

---

# 3. business-rules.md

## Reglas del negocio

Aunque algunas implementaciones mezclan reglas dentro de requirements, separar reglas de negocio suele ser beneficioso.

Ejemplo:

```markdown
# Business Rules


BR001

Only active customers can view benefits.


BR002

Expired benefits are hidden.


BR003

Benefits depend on customer category.
```

---

## Pregunta que responde

> ¿Qué restricciones del negocio debemos respetar?

---

# 4. design.md

## Diseño técnico

Aquí definimos cómo se implementará.

Incluye:

* arquitectura;
* componentes;
* servicios;
* integraciones;
* decisiones técnicas.

---

Ejemplo frontend:

```markdown
## Frontend


Components:

- BenefitsPageComponent


Services:

- BenefitsService


State:

- BenefitsStore
```

---

Ejemplo backend:

```markdown
## Backend


API:

GET /customers/{id}/benefits


Service:

BenefitsService
```

---

## Pregunta que responde

> ¿Cómo encaja esta funcionalidad dentro del sistema?

---

# 5. tasks.md

## Plan de ejecución

Transforma la Specification en trabajo realizable.

Ejemplo:

```markdown
# Tasks


TASK-001

Create benefits page.


TASK-002

Implement API integration.


TASK-003

Add loading state.


TASK-004

Create automated tests.
```

---

Una buena Task debe ser:

* concreta;
* asignable;
* verificable.

---

## Pregunta que responde

> ¿Qué debemos hacer para construirlo?

---

# 6. test-plan.md

## Validación

Define cómo sabremos que la implementación es correcta.

Ejemplo:

```markdown
# Test Scenario


Given:

Customer with active benefits.


When:

Customer opens benefits page.


Then:

Benefits list is displayed.
```

---

Debe incluir:

* casos positivos;
* casos negativos;
* errores;
* escenarios límite.

---

## Pregunta que responde

> ¿Cómo comprobamos que funciona?

---

# 7. decisions/

## Registro de decisiones técnicas

Aquí viven los ADR (Architecture Decision Records).

Ejemplo:

```text
decisions/

├── ADR-001-state-management.md

└── ADR-002-api-design.md
```

---

Ejemplo:

```markdown
# ADR-001

## Decision

Use existing application store.


## Reason

Maintain consistency with current architecture.
```

---

## Pregunta que responde

> ¿Por qué tomamos esta decisión?

---

# Relación entre artefactos

Los archivos no existen aislados.

Existe una relación:

```text
                 spec.md

                    |

                    ▼

            requirements.md

                    |

        ┌───────────┴───────────┐

        ▼                       ▼

   design.md              test-plan.md

        |

        ▼

    tasks.md
```

---

# Una Specification como paquete de contexto

Para un agente IA, una Specification completa representa:

```text
Context

+

Requirements

+

Constraints

+

Architecture

+

Validation
```

Ejemplo:

```text
Implement TASK-002.

Read:

/specs/customer-benefits/

Understand:

- requirements.md
- design.md
- test-plan.md

Follow:

existing architecture patterns.
```

---

# Relación con Pull Requests

Una práctica recomendada:

Una funcionalidad debería incluir:

```text
Pull Request

├── source code
├── tests
└── specification changes
```

La revisión analiza:

## Código

¿Está bien implementado?

---

## Specification

¿Representa correctamente la intención?

---

## Tests

¿Validan el comportamiento esperado?

---

# Errores comunes al estructurar Specifications

## Specification demasiado grande

Incorrecto:

```text
Customer Platform
```

Incluye demasiadas capacidades.

---

Correcto:

```text
Customer Benefits
Customer Address Update
Customer Invoice Download
```

---

## Mezclar intención con implementación

Incorrecto:

```text
Create Angular component with RxJS Subject.
```

Eso pertenece al diseño.

---

Correcto:

```text
The customer must see available benefits.
```

---

## No definir exclusiones

Si no definimos qué queda fuera, el alcance crece continuamente.

---

# Regla práctica

Cada Specification debe permitir que alguien nuevo en el equipo responda:

1. ¿Qué estamos haciendo?
2. ¿Por qué lo hacemos?
3. ¿Cómo debe comportarse?
4. ¿Cómo será construido?
5. ¿Cómo sabremos que está correcto?

Si no puede responderlas, la Specification está incompleta.

---

# Resumen

La estructura OpenSpec organiza el conocimiento de una funcionalidad:

| Artefacto         | Propósito                  |
| ----------------- | -------------------------- |
| spec.md           | Contexto y objetivo        |
| requirements.md   | Comportamiento esperado    |
| business-rules.md | Restricciones de negocio   |
| design.md         | Solución técnica           |
| tasks.md          | Plan de ejecución          |
| test-plan.md      | Validación                 |
| decisions/        | Decisiones arquitectónicas |

Esta estructura permite que una Specification sea útil para:

* equipos;
* desarrolladores;
* QA;
* arquitectos;
* agentes IA.

---

# Próximo capítulo

El siguiente archivo será:

```text
module-02-openspec/

└── 04-spec-lifecycle.md
```

donde veremos cómo nace, evoluciona y se mantiene una Specification durante todo el ciclo de vida del desarrollo.
