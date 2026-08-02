# Workflow de desarrollo con Specification-Driven Development

## Introducción

Una de las preguntas más frecuentes al adoptar Specification-Driven Development es:

> ¿En qué cambia realmente el trabajo diario del equipo?

La respuesta es:

No cambia el objetivo.

Cambia **el orden en que se toman las decisiones**.

En un proceso tradicional muchas decisiones aparecen durante la implementación.

En SDD intentamos que las decisiones importantes ocurran antes de escribir código.

---

# El workflow tradicional

Un flujo típico es:

```text
Product

↓

User Story

↓

Sprint

↓

Developer

↓

Código

↓

Testing

↓

Pull Request
```

Durante el desarrollo aparecen preguntas como:

* ¿Qué quiso decir el Product Owner?
* ¿Qué ocurre en casos límite?
* ¿Existe una API?
* ¿Qué componente reutilizamos?
* ¿Qué pruebas debemos crear?

Estas preguntas retrasan el desarrollo.

---

# El workflow con SDD

El flujo propuesto es:

```text
Business Need

↓

Azure DevOps User Story

↓

OpenSpec

↓

Refinement

↓

Specification Approved

↓

Implementation

↓

Testing

↓

Pull Request

↓

Release
```

La diferencia es que el desarrollo comienza con una Specification validada.

---

# Vista completa del flujo

```text
┌─────────────────────┐
│ Business Need       │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│ Azure DevOps        │
│ Epic / Feature / US │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│ OpenSpec            │
│ Specification       │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│ Refinement          │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│ Approved Tasks      │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│ AI + Developer      │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│ Tests               │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│ Pull Request        │
└─────────┬───────────┘
          │
          ▼
┌─────────────────────┐
│ Production          │
└─────────────────────┘
```

---

# Etapa 1 - Identificación de la necesidad

Todo comienza con una necesidad.

Ejemplo:

```text
Los clientes quieren descargar sus facturas.
```

Todavía no existe código.

Tampoco existe una solución.

Solo existe un problema.

---

# Etapa 2 - Gestión del trabajo

Azure DevOps continúa siendo el sistema de gestión.

Ejemplo:

```text
Epic

Customer Portal

↓

Feature

Invoices

↓

User Story

Download Invoice
```

Azure DevOps responde:

* ¿Qué vamos a construir?
* ¿Cuál es la prioridad?
* ¿Quién trabajará?
* ¿En qué sprint?

No responde:

* ¿Cómo construirlo?

---

# Etapa 3 - Crear la Specification

El equipo crea:

```text
specs/

invoice-download/

├── spec.md

├── requirements.md

├── design.md

├── tasks.md

└── test-plan.md
```

Ahora existe conocimiento compartido.

---

# Etapa 4 - Refinamiento

El equipo revisa la Specification.

Participan:

* Product Owner
* Tech Lead
* Developers
* QA
* Arquitectura (si aplica)

Objetivo:

Reducir incertidumbre.

No escribir código.

---

# Etapa 5 - Aprobación

La Specification pasa a estado:

```text
READY
```

A partir de este momento:

No deberían existir dudas críticas.

Las decisiones importantes ya fueron tomadas.

---

# Etapa 6 - Planificación de implementación

Las Tasks se distribuyen.

Ejemplo:

```text
TASK-001

Backend API


TASK-002

Frontend UI


TASK-003

Automated Tests
```

Cada Task mantiene una relación directa con uno o más Requirements.

---

# Etapa 7 - Implementación asistida por IA

Aquí cambia la forma de trabajar.

En lugar de pedir:

```text
Create invoice component.
```

El desarrollador utiliza la Specification.

Ejemplo:

```text
Implement TASK-002.

Specification:

invoice-download

Read:

requirements.md

design.md

Constraints:

Reuse existing InvoiceService.

Validation:

Add Jest tests.
```

La IA recibe contexto suficiente para producir una implementación alineada.

---

# Etapa 8 - Validación continua

Cada Task implementada debe validar:

* Requirements.
* Tests.
* Restricciones.

La pregunta deja de ser:

> ¿Compila?

Y pasa a ser:

> ¿Cumple la Specification?

---

# Etapa 9 - Pull Request

Una Pull Request ideal contiene:

```text
Code

+

Tests

+

Specification updates
```

El revisor analiza tres aspectos:

## Código

Calidad de implementación.

---

## Specification

¿El comportamiento sigue siendo correcto?

---

## Trazabilidad

¿El código implementa realmente los Requirements?

---

# Etapa 10 - Merge

Cuando la Pull Request se aprueba:

```text
main

↓

Code

↓

Specification

↓

Tests
```

Todo evoluciona junto.

---

# Etapa 11 - Release

El pipeline despliega:

* código;
* configuración;
* documentación versionada.

En una auditoría futura podremos responder:

* ¿Qué cambió?
* ¿Por qué cambió?
* ¿Qué Requirements implementaba?
* ¿Qué pruebas existían?

---

# Integración con GitHub Copilot

GitHub Copilot funciona como un asistente de implementación.

Responsabilidades:

* generar código;
* completar funciones;
* crear pruebas;
* proponer refactorizaciones.

No debería:

* decidir requisitos;
* cambiar arquitectura;
* ampliar el alcance de una Task.

---

# Integración con Claude Code

Claude Code puede trabajar con una visión más amplia.

Ejemplo:

```text
Read Specification.

Review Requirements.

Compare with current implementation.

Implement TASK-003.

Explain decisions.

Generate tests.
```

Es especialmente útil para cambios de mayor complejidad.

---

# Flujo del desarrollador

```text
Asignación de Task

↓

Leer Specification

↓

Entender Requirements

↓

Revisar Design

↓

Planificar cambio

↓

Implementar

↓

Ejecutar pruebas

↓

Actualizar Specification (si corresponde)

↓

Crear Pull Request
```

---

# Flujo del revisor

Antes de aprobar una PR debe verificar:

```text
□ El código cumple los Requirements.

□ Los tests cubren los escenarios.

□ No se rompió la arquitectura.

□ La Specification sigue vigente.

□ La trazabilidad se mantiene.
```

---

# Definition of Done

Una funcionalidad está terminada cuando:

✅ Código implementado.

✅ Tests aprobados.

✅ Specification actualizada.

✅ Pull Request aprobada.

✅ Pipeline exitoso.

✅ Lista para producción.

No antes.

---

# Aplicación en tu empresa

Con el stack que describiste, un flujo recomendado sería:

```text
Azure DevOps

↓

User Story

↓

OpenSpec

↓

Refinement

↓

GitHub Branch

↓

Claude Code

↓

GitHub Copilot

↓

Developer Review

↓

Pull Request

↓

CI/CD

↓

Production
```

Cada herramienta tiene un propósito claro:

| Herramienta  | Responsabilidad                          |
| ------------ | ---------------------------------------- |
| Azure DevOps | Gestión del trabajo                      |
| OpenSpec     | Gestión del conocimiento                 |
| GitHub       | Código y versionado                      |
| Copilot      | Asistencia durante la implementación     |
| Claude Code  | Implementación y análisis de mayor nivel |
| CI/CD        | Validación y despliegue                  |

---

# Un paso más: el workflow orientado a agentes

A medida que un equipo madura, el desarrollador deja de pedir "escribe este código" y empieza a orquestar trabajo.

El flujo evoluciona hacia:

```text
Specification

↓

Seleccionar Task

↓

Asignar contexto

↓

Agente propone plan

↓

Humano aprueba

↓

Agente implementa

↓

Pruebas automáticas

↓

Revisión humana

↓

Merge
```

Aquí el desarrollador actúa como **orquestador**, no simplemente como autor del código.

Este cambio es uno de los principios más importantes de SDD aplicado a la ingeniería asistida por IA.

---

# Resumen

Specification-Driven Development no reemplaza el ciclo de desarrollo existente.

Lo reorganiza para que:

* las decisiones importantes se tomen antes del código;
* el conocimiento permanezca versionado;
* la IA trabaje con contexto estructurado;
* la trazabilidad llegue desde la necesidad de negocio hasta la implementación.

El resultado es un proceso más predecible, auditable y escalable.

---

# Próximo capítulo

```text
docs/module-03-specification-workflow/

└── 06-code-review-and-spec-review.md
```

En el siguiente capítulo veremos cómo cambia el proceso de revisión cuando, además del código, también revisamos la **Specification**. Analizaremos checklists, criterios de aceptación y un modelo de revisión específico para equipos que utilizan SDD con agentes de IA.
