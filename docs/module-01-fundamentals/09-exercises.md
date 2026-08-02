# Ejercicios prácticos - Fundamentos de SDD

## Introducción

El objetivo de estos ejercicios es entrenar una nueva forma de pensar.

En un desarrollo tradicional, normalmente recibimos una User Story y comenzamos a implementar.

En SDD el proceso cambia:

```text
Necesidad

   ↓

Entendimiento

   ↓

Specification

   ↓

Diseño

   ↓

Implementación
```

Los ejercicios buscan desarrollar la capacidad de transformar información incompleta en conocimiento estructurado.

---

# Ejercicio 1 - Detectar ambigüedad en una User Story

## Objetivo

Aprender a identificar información faltante antes de comenzar a programar.

---

## User Story

```text
US-1001

Como cliente quiero actualizar mis datos personales
para mantener mi información actualizada.
```

---

## Preguntas de análisis

Antes de crear código, responder:

### Contexto

* ¿Por qué el cliente necesita actualizar sus datos?
* ¿Qué problema actual estamos resolviendo?

---

### Alcance

¿Qué datos puede modificar?

Ejemplos:

* Nombre.
* Teléfono.
* Email.
* Dirección.

---

### Seguridad

* ¿Todos los clientes pueden hacerlo?
* ¿Necesita validación adicional?
* ¿Existe auditoría?

---

### Reglas

* ¿Qué ocurre con datos inválidos?
* ¿Hay campos obligatorios?

---

### Testing

* ¿Qué escenarios deben probarse?

---

## Resultado esperado

Crear una lista de preguntas que deben resolverse antes de implementar.

---

# Ejercicio 2 - Transformar User Story en Specification

## Objetivo

Crear la primera Specification básica.

---

## User Story

```text
US-2001

Como cliente quiero consultar mis beneficios
para conocer las promociones disponibles.
```

---

Crear:

```text
specs/

└── customer-benefits/

    ├── spec.md

    ├── requirements.md

    ├── business-rules.md

    └── test-plan.md
```

---

# spec.md

Debe responder:

## Context

¿Por qué existe esta funcionalidad?

---

## Goal

¿Qué queremos conseguir?

---

## Scope

¿Qué incluye?

---

## Out of Scope

¿Qué queda fuera?

---

Ejemplo:

```markdown
# Customer Benefits

## Context

Customers need visibility of available benefits
without contacting support.

## Goal

Allow authenticated customers to view active benefits.

## Scope

- Display available benefits.
- Show expiration date.

## Out of Scope

- Benefit activation.
- Benefit purchase.
```

---

# requirements.md

Crear requisitos verificables.

Ejemplo:

```markdown
# Requirement R001

The customer must be authenticated.

Given:
A user without authentication.

When:
The user accesses benefits.

Then:
The system redirects to login.
```

Crear al menos:

* R001 autenticación.
* R002 visualización.
* R003 estado vacío.
* R004 error de servicio.

---

# business-rules.md

Definir reglas:

Ejemplo:

```markdown
BR001

Only active benefits are displayed.


BR002

Expired benefits are hidden.
```

Crear al menos tres reglas.

---

# test-plan.md

Crear escenarios:

Ejemplo:

```markdown
Scenario:

Customer has active benefits.

Expected:

Benefits are displayed.
```

Crear:

* Caso exitoso.
* Sin beneficios.
* Error backend.
* Usuario no autenticado.

---

# Ejercicio 3 - Identificar información necesaria para IA

## Objetivo

Comprender por qué una IA necesita contexto.

---

## Prompt inicial

```text
Implement a benefits page.
```

---

Analizar:

¿Qué información falta?

---

Crear una segunda versión:

```text
Implement the customer benefits feature.

Context:

...

Requirements:

...

Architecture:

...

Tests:

...
```

---

Comparar ambos resultados.

---

# Ejercicio 4 - Detectar Specification Drift

## Objetivo

Aprender a mantener alineados conocimiento y código.

---

Tenemos:

Specification:

```text
The customer can update phone number and email.
```

Código actual:

```typescript
updateCustomer(data){

    savePhone(data.phone);

}
```

---

Preguntas:

1. ¿Existe diferencia entre Specification y código?
2. ¿Qué debería actualizarse?
3. ¿La Specification estaba incorrecta?
4. ¿El código está incompleto?

---

Resultado esperado:

Identificar el drift y proponer una acción.

---

# Ejercicio 5 - Relacionar Azure DevOps con OpenSpec

## Objetivo

Aplicar SDD en un entorno empresarial real.

---

Entrada:

Azure DevOps User Story:

```text
Feature:

Customer Profile


User Story:

As a customer
I want to change my address
so that my information is correct.
```

---

Crear:

```text
Azure DevOps

Feature
 |
 User Story


OpenSpec

Specification
 |
 Requirements
 |
 Design
 |
 Tasks
 |
 Tests
```

---

Definir:

¿Qué información queda en Azure DevOps?

¿Qué información queda en OpenSpec?

---

# Ejercicio 6 - Preparación para agentes IA

## Objetivo

Crear un contexto ejecutable para un agente.

---

Dado:

```text
TASK:

Create address update component.
```

Crear un contexto para Claude Code:

Debe incluir:

```text
Context:

Requirements:

Architecture:

Files involved:

Constraints:

Validation:
```

---

Ejemplo:

```text
Context:

The application uses Angular Signals.

Requirements:

User must edit address fields.

Constraints:

Do not introduce new state management libraries.

Validation:

Add Jest tests.
```

---

# Ejercicio final del módulo

## Caso completo

Crear una Specification para:

```text
Como cliente quiero descargar mi factura
para guardar una copia de mis consumos.
```

Debe contener:

```text
spec.md

requirements.md

design.md

tasks.md

test-plan.md
```

---

Debe considerar:

## Negocio

* ¿Quién puede descargar?
* ¿Qué facturas existen?

---

## Seguridad

* ¿Cómo protegemos documentos?

---

## Frontend

* Estados de carga.
* Errores.
* Descarga.

---

## Backend

* Endpoint.
* Autorización.

---

## Testing

* Casos positivos.
* Casos negativos.

---

# Criterios de evaluación

Una buena Specification debe ser:

## Clara

Otra persona puede entender el objetivo.

---

## Completa

Incluye información necesaria para implementar.

---

## Verificable

Tiene criterios que pueden probarse.

---

## Útil para IA

Un agente puede utilizarla como contexto.

---

# Reflexión final

El objetivo de SDD no es escribir más documentación.

Es eliminar incertidumbre antes de invertir esfuerzo.

Una buena Specification reduce:

* preguntas repetidas;
* decisiones improvisadas;
* errores de interpretación;
* retrabajo.

La habilidad fundamental es:

> Convertir intención humana en conocimiento estructurado.

---

# Próximo capítulo

El siguiente archivo será:

```text
docs/module-01-fundamentals/
└── 10-summary.md
```

donde cerraremos el módulo y conectaremos todos los conceptos antes de comenzar con OpenSpec.
