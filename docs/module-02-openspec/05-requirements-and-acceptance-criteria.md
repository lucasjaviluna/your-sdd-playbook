# Requirements y Acceptance Criteria en OpenSpec

## Introducción

Los Requirements son uno de los elementos más importantes dentro de una Specification.

Representan la transformación de una necesidad de negocio en un comportamiento que el sistema debe cumplir.

En muchos equipos ágiles ya existe un concepto similar:

> Acceptance Criteria.

Sin embargo, SDD propone llevar este concepto un paso más allá.

La diferencia principal es:

* Acceptance Criteria valida una User Story.
* Requirements define el comportamiento del sistema.

---

# De User Story a Requirement

Ejemplo tradicional:

Azure DevOps User Story:

```text id="j8m2kq"
Como cliente quiero consultar mis beneficios
para conocer las promociones disponibles.
```

Acceptance Criteria:

```text id="n4v8cx"
Given usuario autenticado

When ingresa a beneficios

Then visualiza sus beneficios.
```

Esto es correcto, pero todavía falta contexto.

---

OpenSpec transforma esto en:

```text id="0h5v2x"
Specification

      ↓

Requirements

      ↓

Business Rules

      ↓

Tests
```

---

# ¿Qué es un Requirement?

Un Requirement describe:

* comportamiento esperado;
* condición inicial;
* acción;
* resultado esperado.

Debe ser:

* claro;
* específico;
* verificable.

---

Ejemplo:

```markdown id="5m7q3d"
# Requirement R001

## Customer Authentication


Given:

A user without authentication.


When:

The user accesses the benefits page.


Then:

The system redirects the user to login.
```

---

# Anatomía de un Requirement

Un Requirement bien definido contiene:

## Identificador

Permite trazabilidad.

Ejemplo:

```text
R001
R002
R003
```

---

## Nombre

Describe la capacidad.

Ejemplo:

```text
Display Available Benefits
```

---

## Contexto

Describe la situación inicial.

Ejemplo:

```text
The customer is authenticated.
```

---

## Acción

Qué ocurre.

Ejemplo:

```text
The customer opens the benefits page.
```

---

## Resultado esperado

Qué debe suceder.

Ejemplo:

```text
Available benefits are displayed.
```

---

# Formato Given / When / Then

El formato más utilizado es:

```text id="8c5k1n"
Given

Estado inicial


When

Acción realizada


Then

Resultado esperado
```

---

Ejemplo completo:

```markdown id="y5m8pz"
# Requirement R002

## Display Benefits


Given:

The customer has active benefits.


When:

The customer opens the benefits section.


Then:

The system displays the active benefits.
```

---

# Requirement versus Business Rule

Estos conceptos suelen confundirse.

## Requirement

Define comportamiento.

Ejemplo:

```text
The customer can view benefits.
```

---

## Business Rule

Define restricciones.

Ejemplo:

```text
Only active customers can view benefits.
```

---

Relación:

```text id="7c4m1w"
Requirement

"The customer can view benefits"


        +

Business Rule

"Only active customers"


        =


Expected Behavior
```

---

# Acceptance Criteria versus Requirements

No son exactamente iguales.

## Acceptance Criteria

Está asociado a una User Story.

Ejemplo:

```text
US-1234

Acceptance Criteria:

Customer sees benefits.
```

---

## Requirements

Pertenece a la Specification.

Ejemplo:

```text
R001:

Authenticated customers can view benefits.


R002:

Expired benefits are hidden.


R003:

Empty state is displayed when no benefits exist.
```

---

Los Requirements son más detallados.

---

# Requisitos funcionales y no funcionales

Una Specification madura incluye ambos.

---

# Functional Requirements

Definen qué hace el sistema.

Ejemplo:

```text
The user can download invoices.
```

---

# Non Functional Requirements

Definen características del sistema.

Ejemplos:

## Performance

```text
The page should load within 2 seconds.
```

---

## Security

```text
Only authorized users can access documents.
```

---

## Availability

```text
The service must be available 99.9%.
```

---

# Requisitos negativos

Un error común es documentar solamente casos positivos.

Ejemplo incompleto:

```text
The user can download invoices.
```

---

También necesitamos:

```text
The user cannot download another customer's invoice.
```

---

Ejemplos:

```text
R004

Given:

A customer without permissions.


When:

The customer requests another user's invoice.


Then:

The system returns unauthorized.
```

---

# Requirement Quality Checklist

Antes de aprobar un Requirement debemos preguntar:

## ¿Es claro?

¿Otra persona lo entiende?

---

## ¿Es verificable?

¿Podemos escribir un test?

---

## ¿Tiene contexto?

¿Sabemos cuándo aplica?

---

## ¿Evita ambigüedad?

Ejemplo incorrecto:

```text
The system should be fast.
```

---

Ejemplo correcto:

```text
The API should respond within 500ms.
```

---

# De Requirement a Test

Una ventaja fundamental de OpenSpec es la trazabilidad.

Ejemplo:

```text id="7y4v2m"
Requirement R001

        ↓

Test Case TC001

        ↓

Automated Test
```

---

Requirement:

```text
Customer sees active benefits.
```

Test:

```typescript
it('should display active benefits', () => {

});
```

---

# Requirements como contexto para IA

Los agentes necesitan saber comportamiento esperado.

Ejemplo pobre:

```text
Create benefits component.
```

---

Ejemplo basado en Requirements:

```text
Implement R002.

Requirement:

Authenticated customers must see
active benefits.

Rules:

- Hide expired benefits.
- Show empty state.

Validation:

Add component tests.
```

---

# Relación con Azure DevOps

Un flujo recomendado:

```text id="1m9c4v"
Azure DevOps

User Story

"Customer views benefits"


        ↓


OpenSpec

requirements.md


R001 Authentication

R002 Display benefits

R003 Empty state


        ↓


Tasks

        ↓


Development
```

---

# Ejemplo completo

User Story:

```text
Como usuario quiero cambiar mi contraseña.
```

Requirements:

```markdown
R001

Given:

An authenticated user.


When:

The user submits a valid new password.


Then:

The password is updated.
```

---

```markdown
R002

Given:

The password does not meet security rules.


When:

The user submits the form.


Then:

The system shows validation errors.
```

---

```markdown
R003

Given:

The user is not authenticated.


When:

The user accesses password change.


Then:

Access is denied.
```

---

# Errores comunes

## Escribir requisitos como tareas

Incorrecto:

```text
Create PasswordComponent.
```

Eso es una Task.

---

Correcto:

```text
The user can change password.
```

---

## Mezclar solución técnica

Incorrecto:

```text
Use Angular Signals.
```

Eso pertenece al Design.

---

Correcto:

```text
The user sees updated information immediately.
```

---

## Crear requisitos imposibles de probar

Incorrecto:

```text
The system should be intuitive.
```

---

# Resumen

Los Requirements son el puente entre:

```text
Necesidad de negocio

        ↓

User Story

        ↓

Specification

        ↓

Implementation
```

Un buen Requirement:

* define comportamiento;
* tiene contexto;
* puede validarse;
* genera tests;
* sirve como contexto para IA.

---

# Próximo capítulo

El siguiente archivo será:

```text
docs/module-02-openspec/

└── 06-design-and-architecture-context.md
```

donde veremos cómo pasar de Requirements a Design, definiendo cómo la solución encaja con una arquitectura existente.
