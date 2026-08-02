# Ejercicios prácticos - OpenSpec

## Introducción

El objetivo de estos ejercicios es practicar la creación de Specifications completas.

La meta no es escribir documentación.

La meta es aprender a transformar una necesidad de negocio en un paquete de conocimiento ejecutable por humanos y agentes IA.

---

# Ejercicio 1 - Transformar una User Story en Specification

## Contexto

Azure DevOps contiene:

```text
Feature:

Customer Profile


User Story:

Como cliente quiero actualizar mi teléfono
para mantener mis datos actualizados.
```

---

## Paso 1

Crear la estructura:

```text
specs/

customer-phone-update/

├── spec.md

├── requirements.md

├── design.md

├── tasks.md

└── test-plan.md
```

---

## Paso 2

Crear spec.md.

Debe responder:

* ¿Cuál es el problema?
* ¿Cuál es el objetivo?
* ¿Qué incluye?
* ¿Qué queda fuera?

---

Ejemplo:

```markdown
# Customer Phone Update


## Context

Customers need to maintain
their contact information updated.


## Goal

Allow customers to modify
their phone number.


## Scope

Included:

- Edit phone number.
- Validate format.


Excluded:

- Contact preferences.
```

---

# Ejercicio 2 - Crear Requirements

A partir de la User Story anterior crear:

Mínimo:

* 3 requisitos funcionales.
* 2 reglas de negocio.
* 2 casos negativos.

---

Ejemplo:

```markdown
# Requirement R001


Given:

Authenticated customer.


When:

Customer submits a valid phone number.


Then:

Phone number is updated.
```

---

Crear también:

```markdown
BR001

Phone number must have
valid format.
```

---

Caso negativo:

```markdown
R004


Given:

Invalid phone number.


When:

Customer submits form.


Then:

System displays validation error.
```

---

# Ejercicio 3 - Crear Design

## Contexto técnico

La aplicación actual:

```text
Frontend:

Angular 20


Architecture:

Standalone Components


State:

NgRx


Testing:

Jest
```

---

Crear:

```text
design.md
```

Debe incluir:

## Componentes

Ejemplo:

```text
PhoneUpdateComponent
PhoneService
CustomerStore
```

---

## Flujo

Representar:

```text
Component

 ↓

Store

 ↓

Service

 ↓

API
```

---

## Restricciones

Ejemplo:

```text
Do not introduce new state management.
```

---

# Ejercicio 4 - Crear Tasks

Transformar Design en tareas.

Ejemplo:

```markdown
TASK-001

Create phone update component.


TASK-002

Implement validation rules.


TASK-003

Integrate API service.


TASK-004

Add automated tests.
```

---

Cada Task debe:

* tener objetivo;
* relacionarse con un Requirement;
* poder verificarse.

---

# Ejercicio 5 - Diseñar un flujo con IA

Supongamos que utilizamos Claude Code.

Crear el contexto:

```text
Implement TASK-003.


Specification:

customer-phone-update


Read:

requirements.md

design.md


Constraints:

- Use existing services.
- Follow Angular patterns.


Validation:

Add Jest tests.
```

---

Preguntas:

¿Por qué este contexto es mejor que?

```text
Create phone service.
```

---

# Ejercicio 6 - Detectar Specification Drift

Tenemos:

Specification:

```text
Customer can update phone number.
```

Código:

```typescript
updateEmail()
```

---

Responder:

1. ¿Existe drift?
2. ¿Qué está incorrecto?
3. ¿Debe cambiar el código o la Specification?

---

# Ejercicio 7 - Integración Azure DevOps

Tenemos:

```text
US-9001

Download Invoice
```

Crear:

## Azure DevOps

Debe contener:

```text
Feature:

Invoices


User Story:

Download invoice
```

---

## OpenSpec

Crear:

```text
specs/

invoice-download/
```

con:

```text
spec.md

requirements.md

design.md
```

---

Definir:

¿Qué queda en Azure DevOps?

¿Qué queda en OpenSpec?

---

# Ejercicio 8 - Caso completo empresarial

## Contexto

Una empresa necesita:

> Permitir que clientes descarguen sus facturas desde el portal.

---

Crear una Specification completa:

```text
invoice-download/

├── spec.md

├── requirements.md

├── business-rules.md

├── design.md

├── tasks.md

└── test-plan.md
```

---

Debe contemplar:

## Negocio

* clientes autorizados;
* facturas disponibles;
* historial.

---

## Seguridad

* autorización;
* protección de documentos.

---

## Frontend

* botón descargar;
* estados;
* errores.

---

## Backend

* endpoint;
* permisos;
* generación del archivo.

---

## Testing

* descarga exitosa;
* factura inexistente;
* usuario no autorizado.

---

# Ejercicio 9 - Preparar contexto para un agente

Crear un prompt profesional.

Debe contener:

```text
Context

Specification

Requirements

Design

Constraints

Validation
```

---

Ejemplo:

```text
You are implementing TASK-004.


Context:

Invoice download feature.


Architecture:

Angular + NgRx.


Requirements:

R001-R005.


Constraints:

Reuse existing document service.


Validation:

Create Jest tests.
```

---

# Ejercicio final del módulo

## Simulación completa de trabajo

Actúa como un equipo real.

Entrada:

Azure DevOps:

```text
Feature:

Customer Payments


User Story:

Como cliente quiero ver mis pagos
para controlar mis consumos.
```

---

Crear:

```text
1. Specification

2. Requirements

3. Design

4. Tasks

5. Test Plan

6. AI Context
```

---

La solución debe permitir que:

## Product Owner

entienda el valor.

---

## Developer

pueda implementar.

---

## QA

pueda validar.

---

## Arquitecto

pueda revisar impacto.

---

## IA

pueda colaborar.

---

# Criterios de evaluación

Una Specification está completa cuando:

## Contexto

✅ Explica por qué existe.

---

## Requirements

✅ Define comportamiento verificable.

---

## Design

✅ Respeta arquitectura.

---

## Tasks

✅ Son ejecutables.

---

## Tests

✅ Validan requisitos.

---

## IA

✅ Tiene contexto suficiente.

---

# Reflexión final del módulo

OpenSpec no busca agregar burocracia.

Busca reducir incertidumbre.

El costo mayor en desarrollo no es escribir código.

Es:

* interpretar mal una necesidad;
* tomar decisiones inconsistentes;
* rehacer trabajo;
* perder conocimiento.

---

El modelo mental final:

```text
Antes:

User Story

 ↓

Código


Después:

User Story

 ↓

Specification

 ↓

Knowledge

 ↓

Code

 ↓

Validation
```

---

# Estado al finalizar Módulo 2

Ahora deberías poder:

✅ Crear una Specification OpenSpec.
✅ Definir Requirements verificables.
✅ Crear Design técnico.
✅ Generar Tasks ejecutables.
✅ Versionar Specifications con Git.
✅ Integrar OpenSpec con Azure DevOps.
✅ Preparar contexto para Copilot y Claude Code.

---

# Próximo módulo

```text
Módulo 3

Specification Workflow

"Cómo aplicar SDD en un equipo real"
```

En el siguiente módulo veremos:

* cómo iniciar una funcionalidad desde cero;
* ceremonias del equipo;
* roles;
* refinamiento;
* aprobación;
* implementación;
* revisión;
* operación.
