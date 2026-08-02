# Desde una idea hasta una Specification

## Introducción

Todo desarrollo de software comienza con una necesidad.

Puede surgir desde:

* un cliente;
* negocio;
* producto;
* soporte;
* análisis de datos;
* una mejora técnica.

El problema es que normalmente esa necesidad llega con información incompleta.

Ejemplo:

```text id="idea01"
"Necesitamos permitir que los clientes descarguen sus facturas."
```

Esta frase expresa intención.

Pero todavía no sabemos:

* quién puede descargar;
* qué facturas están disponibles;
* qué restricciones existen;
* cómo impacta la arquitectura;
* cómo validaremos el resultado.

---

# La transformación fundamental de SDD

SDD propone evolucionar:

```text id="flow02"
Idea

 ↓

User Story

 ↓

Specification

 ↓

Implementation
```

La Specification es el lugar donde la incertidumbre se reduce antes de escribir código.

---

# Paso 1 - Capturar la intención

El primer paso no es diseñar una solución.

Es entender el problema.

Ejemplo:

## Entrada inicial

Azure DevOps:

```text id="ado01"
Feature:

Invoice Management


User Story:

Como cliente quiero descargar
mis facturas para tener acceso
a mis comprobantes.
```

---

Todavía no tenemos una Specification.

Tenemos una intención.

---

# Paso 2 - Crear el contexto de negocio

La Specification comienza explicando:

## ¿Por qué existe esta funcionalidad?

Ejemplo:

```markdown id="context01"
# Invoice Download


## Business Context

Currently customers must contact
support to obtain historical invoices.

This feature allows customers
to self-service their invoices.
```

---

El objetivo es que cualquier persona pueda entender:

* el problema;
* el valor esperado;
* el motivo del cambio.

---

# Paso 3 - Definir alcance

Una de las mayores fuentes de problemas es el alcance ambiguo.

La Specification debe definir:

## Incluido

Ejemplo:

```text id="scope01"
Included:

- View available invoices.
- Download PDF invoices.
- Show download errors.
```

---

## Fuera de alcance

Ejemplo:

```text id="scope02"
Excluded:

- Invoice payment.
- Invoice correction.
- Tax document generation.
```

---

Esto evita que cada persona interprete algo diferente.

---

# Paso 4 - Identificar actores

Antes de definir requisitos debemos saber quién interactúa.

Ejemplo:

```markdown id="actors01"
## Actors


Customer

Can view and download own invoices.


Administrator

Can review customer invoices.
```

---

Los actores ayudan a descubrir reglas.

---

# Paso 5 - Crear preguntas abiertas

Un error común es comenzar desarrollo con preguntas sin resolver.

SDD propone hacer explícitas las dudas.

Ejemplo:

```markdown id="questions01"
## Open Questions


- How many years of invoices are available?
- What happens if PDF generation fails?
- Are administrators allowed to download?
```

---

Estas preguntas se resuelven durante refinamiento.

---

# Paso 6 - Crear la primera versión de Specification

Una estructura inicial podría ser:

```text id="specstructure01"
invoice-download/

├── spec.md

├── requirements.md

├── design.md

└── tasks.md
```

---

En esta etapa no necesariamente todo está completo.

La Specification evoluciona.

---

# Specification como documento vivo

Una mala práctica:

```text id="bad01"
Crear Specification después del desarrollo.
```

Eso solamente documenta historia.

---

La práctica correcta:

```text id="good01"
Crear Specification antes del desarrollo.

Evolucionarla durante el ciclo.
```

---

# Ejemplo completo

## Idea inicial

```text id="idea02"
"Los clientes necesitan consultar sus pagos."
```

---

## User Story

```text id="story03"
Como cliente quiero consultar
mis pagos realizados.
```

---

## Specification

```markdown id="spec03"
# Customer Payments


## Goal

Allow customers to review
their payment history.


## Scope

Included:

- Payment list.
- Payment details.


Excluded:

- Payment creation.
```

---

## Requirements iniciales

```markdown id="req03"
R001

Authenticated customers
can view payments.


R002

Customers only see
their own payments.
```

---

# ¿Quién crea la Specification?

Depende de la madurez del equipo.

No debería ser responsabilidad exclusiva de una persona.

---

Modelo recomendado:

```text id="roles01"
Product Owner

Define business intent.


        +

Developer

Defines technical context.


        +

QA

Defines validation.


        +

Architect

Reviews impact.
```

---

# Refinamiento de Specification

La creación inicial no busca perfección.

Busca generar conversación.

Ejemplo:

Primera versión:

```text id="version01"
Customer downloads invoice.
```

---

Después del refinamiento:

```text id="version02"
Authenticated customers
can download PDF invoices
from the last 5 years.
```

---

El conocimiento aumenta progresivamente.

---

# Relación con Azure DevOps

Un flujo práctico:

```text id="azureflow01"
Azure DevOps

Create User Story


        ↓


Engineering creates Specification


        ↓


Refinement meeting


        ↓


Approve Specification


        ↓


Development begins
```

---

# Criterio para saber cuándo crear una Specification

No todo cambio necesita una Specification completa.

Ejemplos:

## Sí necesita Specification

✅ Nueva funcionalidad
✅ Cambio de comportamiento
✅ Cambio arquitectónico
✅ Integración externa
✅ Migración importante

---

## Puede no necesitar Specification completa

❌ Cambio de texto menor
❌ Corrección visual simple
❌ Refactor interno sin impacto funcional

---

# La Specification como contrato previo

Antes:

```text id="before01"
"Creo que esto es lo que necesitan."
```

---

Después:

```text id="after01"
"Todos acordamos este comportamiento."
```

---

# Preparación para IA

La diferencia es importante.

Sin Specification:

```text id="ai01"
Create invoice feature.
```

---

Con Specification:

```text id="ai02"
Implement invoice-download.


Business Goal:

Self-service invoice access.


Requirements:

R001-R005.


Architecture:

Use existing invoice services.


Validation:

Add automated tests.
```

---

# Checklist antes de pasar a desarrollo

Una Specification está lista para implementación cuando:

✅ El objetivo está claro.
✅ El alcance está definido.
✅ Los actores están identificados.
✅ Los requisitos principales existen.
✅ Las dudas críticas fueron resueltas.
✅ El equipo entiende qué debe construirse.

---

# Resumen

El paso más importante de SDD es transformar:

```text id="summary02"
Necesidad ambigua

        ↓

Conocimiento estructurado

        ↓

Specification

        ↓

Desarrollo predecible
```

La Specification no es burocracia.

Es una herramienta para reducir incertidumbre antes de invertir esfuerzo.

---

# Próximo capítulo

```text id="m3file03"

docs/module-03-specification-workflow/

└── 03-specification-refinement-process.md
```

En el siguiente capítulo veremos cómo se realiza el refinamiento de una Specification con un equipo real: qué preguntas hacer, quién participa y cuándo una Specification está lista para desarrollo.
