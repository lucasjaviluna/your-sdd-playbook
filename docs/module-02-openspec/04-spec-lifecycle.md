# Ciclo de vida de una Specification OpenSpec

## Introducción

Una de las diferencias más importantes entre documentación tradicional y Specification-Driven Development es que una Specification no representa solamente una descripción del sistema.

Representa una intención activa de cambio.

Por lo tanto, una Specification tiene un ciclo de vida:

```text id="6r4m1s"
Idea

 ↓

Draft Specification

 ↓

Review

 ↓

Approved Specification

 ↓

Implementation

 ↓

Validation

 ↓

Evolution
```

---

# Por qué una Specification necesita ciclo de vida

En muchos equipos ocurre este patrón:

```text id="5txj0a"
User Story

    ↓

Código

    ↓

Documentación opcional
```

El problema:

La documentación aparece tarde o nunca.

Con SDD:

```text id="j2c8wm"
Necesidad

    ↓

Specification

    ↓

Código

    ↓

Specification actualizada
```

La Specification acompaña el cambio desde el inicio.

---

# Estados de una Specification

Una Specification puede tener diferentes estados.

Ejemplo:

```text id="l8f4ma"
DRAFT

  ↓

REVIEW

  ↓

APPROVED

  ↓

IMPLEMENTING

  ↓

VALIDATED

  ↓

ACTIVE
```

---

# 1. Draft Specification

## Objetivo

Capturar la idea inicial.

En esta etapa todavía existe incertidumbre.

Puede contener:

* preguntas abiertas;
* alternativas;
* hipótesis.

---

Ejemplo:

```markdown id="ax7xq5"
# Customer Benefits

Status:

Draft


Open Questions:

- Should expired benefits appear?
- Can users share benefits?
- Is activation required?
```

---

En esta etapa no buscamos perfección.

Buscamos reducir incertidumbre.

---

# 2. Review

## Validación colaborativa

Antes de implementar, la Specification debe ser revisada.

Participan:

* Product Owner;
* Arquitectura;
* Desarrollo;
* QA;
* Seguridad cuando aplica.

---

Preguntas de revisión:

## Negocio

¿Resuelve el problema correcto?

---

## Desarrollo

¿Es técnicamente viable?

---

## QA

¿Puede probarse?

---

## Arquitectura

¿Respeta los estándares existentes?

---

# 3. Approved Specification

Una vez revisada, pasa a estado aprobado.

Significa:

* el objetivo está claro;
* los requisitos están definidos;
* existe una estrategia técnica;
* los criterios de aceptación son verificables.

---

Ejemplo:

```text id="4e9m8a"
Specification:

customer-benefits

Status:

Approved

Ready for implementation.
```

---

# 4. Implementation

La Specification guía el desarrollo.

El flujo:

```text id="m6y3pd"
Developer / AI Agent

        ↓

Read Specification

        ↓

Implement Tasks

        ↓

Create Code

        ↓

Create Tests
```

---

Una tarea debería estar vinculada con la Specification.

Ejemplo:

```text id="t8r6lz"
TASK-003

Source:

customer-benefits specification

Action:

Create BenefitsComponent
```

---

# 5. Validation

Después de implementar:

debemos verificar:

## ¿El código cumple la Specification?

Ejemplo:

Specification:

```text
Customer sees active benefits.
```

Código:

```typescript
showAllBenefits();
```

Existe un problema.

---

## ¿Los tests validan requisitos?

Debe existir relación:

```text id="4s8q2a"
Requirement

       ↓

Test Case

       ↓

Execution Result
```

---

# 6. Active Specification

Una vez liberada la funcionalidad, la Specification pasa a representar el comportamiento actual esperado.

Ahora sirve como referencia futura.

Ejemplo:

Nuevo desarrollador pregunta:

> ¿Por qué esta API funciona así?

Respuesta:

Consultar:

```text
specs/customer-benefits/
```

---

# Cambios durante el tiempo

El software cambia constantemente.

Una Specification debe evolucionar.

Ejemplo:

Versión inicial:

```text id="8k7n3s"
Customer can view benefits.
```

Nuevo requerimiento:

```text id="w2x8vq"
Customer can filter benefits by category.
```

No creamos documentación aparte.

Actualizamos la Specification.

---

# Specification versioning

Las Specifications deben versionarse igual que el código.

Ejemplo:

```text id="r5z0pk"
customer-benefits

v1.0

Initial implementation


v1.1

Added filtering capability


v2.0

New benefits engine
```

---

# Relación con Git

Una práctica recomendada:

```text id="4hj7y0"
commit

feat: add customer benefits filter


changes:

src/

+

specs/customer-benefits/

```

La Specification viaja con el cambio.

---

# Pull Request basado en Specification

Una PR debería poder responder:

## ¿Qué cambia?

Referencia a la Specification.

---

## ¿Por qué cambia?

Contexto del problema.

---

## ¿Cómo cambia?

Design.

---

## ¿Cómo validamos?

Tests.

---

Ejemplo:

```text id="m0x7yq"
PR #452

Feature:

Customer Benefits Filter


Specification:

specs/customer-benefits/


Validation:

Test plan completed.
```

---

# Specification Drift durante el ciclo de vida

El principal riesgo es:

```text id="p6k0sa"
Specification

      ❌

Código
```

Ejemplo:

Specification:

```text
Users can filter by category.
```

Código:

```typescript
loadAllBenefits();
```

La solución:

* actualizar código;
* actualizar Specification;
* rechazar cambios incompletos.

---

# OpenSpec como sistema de memoria

Una organización madura usa Specifications como memoria operacional.

Ejemplo:

Después de varios años:

```text id="z4p2js"
Repository

├── src
├── tests
└── specs

    ├── payments
    ├── customers
    ├── benefits
    └── authentication
```

El conocimiento queda almacenado.

---

# Relación con equipos ágiles

OpenSpec no elimina Scrum o Agile.

Los complementa.

Modelo:

```text id="b5k8w9"
Sprint Planning

        ↓

Select User Stories

        ↓

Create / Update Specifications

        ↓

Implementation

        ↓

Review
```

---

# Automatización del ciclo de vida

En equipos maduros pueden agregarse validaciones.

Ejemplo:

Pull Request:

```text id="v9n3cx"
Check:

Does feature have specification?

        |

        ├── Yes → Continue

        └── No → Require update
```

---

# Regla fundamental

Una Specification debe estar siempre en uno de estos estados:

```text id="h7m2px"
Definiendo intención

        o

Describiendo comportamiento actual
```

Nunca debe quedar abandonada.

---

# Resumen

El ciclo de vida OpenSpec es:

```text id="7p2d9m"
Draft

 ↓

Review

 ↓

Approved

 ↓

Implementation

 ↓

Validation

 ↓

Evolution
```

Una Specification:

* nace antes del código;
* guía la implementación;
* valida el resultado;
* evoluciona con el sistema.

El objetivo final es mantener alineados:

```text id="2f9q8v"
Business Intent

        =

Specification

        =

Implementation
```

---

# Próximo capítulo

El siguiente archivo será:

```text id="z8r3px"
docs/module-02-openspec/

└── 05-requirements-and-acceptance-criteria.md
```

donde profundizaremos en cómo escribir Requirements de calidad y cómo transformar criterios de aceptación de Azure DevOps en especificaciones verificables.
