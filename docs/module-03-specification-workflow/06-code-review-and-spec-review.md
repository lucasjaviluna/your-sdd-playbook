# Code Review y Specification Review

## Introducción

En la mayoría de los equipos modernos existe un proceso de Code Review antes de integrar cambios al repositorio principal.

Su objetivo es verificar:

* calidad del código;
* mantenibilidad;
* cumplimiento de estándares;
* ausencia de errores evidentes.

Sin embargo, cuando trabajamos con Specification-Driven Development aparece una nueva pregunta:

> ¿Qué ocurre si el código está bien escrito, pero implementa el comportamiento incorrecto?

En ese caso, el problema no está en el código.

Está en la comprensión de la necesidad.

Por eso SDD introduce un segundo nivel de revisión:

```text
Specification Review
```

El objetivo ya no es únicamente validar cómo fue implementada la solución.

También debemos validar **qué solución fue implementada**.

---

# Dos revisiones diferentes

En SDD existen dos revisiones complementarias.

```text
Specification

        ↓

Implementation

        ↓

Code Review
```

Pero además:

```text
Specification

        ↓

Specification Review
```

Ambas son necesarias.

---

# ¿Qué valida el Code Review?

El Code Review responde preguntas como:

* ¿El código es legible?
* ¿Respeta los estándares del equipo?
* ¿Existe duplicación?
* ¿La solución es mantenible?
* ¿Las pruebas tienen calidad?
* ¿Hay problemas de rendimiento?
* ¿Hay riesgos de seguridad?

En otras palabras:

```text
¿Cómo fue implementada la solución?
```

---

# ¿Qué valida el Specification Review?

La Specification Review responde preguntas diferentes.

* ¿El comportamiento implementado coincide con los Requirements?
* ¿El alcance cambió sin aprobación?
* ¿Se respetaron las restricciones?
* ¿La arquitectura sigue siendo válida?
* ¿Existen nuevos casos de uso no documentados?

En otras palabras:

```text
¿Implementamos lo que acordamos?
```

---

# Un ejemplo

Specification:

```text
Customer can download invoices.
```

El desarrollador implementa:

```text
Download CSV invoices.
```

El código puede ser excelente.

Incluso puede tener cobertura del 100%.

Pero la implementación es incorrecta.

No cumple la Specification.

---

# Otro ejemplo

Requirement:

```text
Only authenticated customers
can download invoices.
```

Código:

```typescript
downloadInvoice()
```

Sin verificar autenticación.

El Code Review podría enfocarse en la calidad del código y no detectar el problema.

La Specification Review sí lo detectaría.

---

# Trazabilidad

Cada cambio debería poder responder tres preguntas.

```text
¿Por qué existe?

↓

Specification

----------------

¿Qué implementa?

↓

Requirement

----------------

¿Dónde está implementado?

↓

Código
```

Esta trazabilidad facilita:

* mantenimiento;
* auditorías;
* incorporación de nuevos integrantes;
* uso de agentes IA.

---

# Checklist del Specification Review

Antes de aprobar una Pull Request verifica:

## Objetivo

□ El objetivo de negocio sigue siendo el mismo.

---

## Alcance

□ No aparecieron funcionalidades nuevas.

□ No desaparecieron funcionalidades acordadas.

---

## Requirements

□ Todos los Requirements afectados fueron implementados.

□ No existen comportamientos contradictorios.

---

## Restricciones

□ Se respetaron las decisiones arquitectónicas.

□ No se agregaron dependencias no aprobadas.

□ No se modificó la arquitectura sin justificación.

---

## Validación

□ Existen pruebas para los escenarios definidos.

□ Los casos negativos fueron considerados.

---

## Documentación

□ La Specification refleja el estado actual.

---

# Checklist del Code Review

El Code Review continúa siendo importante.

Ejemplo:

## Calidad

□ Código legible.

□ Nombres claros.

□ Responsabilidad única.

---

## Arquitectura

□ Sigue los patrones del proyecto.

□ Reutiliza componentes existentes.

□ Evita duplicación.

---

## Testing

□ Cobertura adecuada.

□ Casos límite.

□ Errores controlados.

---

## Seguridad

□ Validación de permisos.

□ Manejo de datos sensibles.

---

## Performance

□ Sin consultas innecesarias.

□ Sin renderizados redundantes.

---

# Pull Request orientada a Specification

Una Pull Request debería incluir referencias explícitas.

Ejemplo:

```text
Implements:

TASK-003

Requirements:

R001
R002

Specification:

invoice-download

Tests:

InvoiceDownloadComponent.spec.ts
```

Esto facilita comprender el impacto del cambio sin necesidad de leer todo el código.

---

# El rol de los agentes IA

Los agentes también pueden participar en las revisiones.

Ejemplo:

```text
Review current Pull Request.

Compare implementation with:

requirements.md

design.md

Identify:

- missing requirements
- unexpected behavior
- architecture violations
```

La IA no aprueba la Pull Request.

Entrega un análisis para que el revisor humano tome la decisión.

---

# Human-in-the-loop

Toda recomendación del agente debe ser revisada.

El flujo recomendado es:

```text
Developer

↓

AI Review

↓

Human Review

↓

Merge
```

Nunca:

```text
Developer

↓

AI

↓

Merge
```

---

# ¿Qué ocurre cuando cambia la Specification?

Durante una revisión puede descubrirse que el comportamiento acordado ya no es suficiente.

En ese caso existen dos opciones.

## Cambia el código

Si la Specification es correcta.

---

## Cambia la Specification

Si el negocio decidió modificar el comportamiento.

Lo importante es que ambos artefactos evolucionen juntos.

---

# Errores comunes

## Aprobar únicamente el código

Consecuencia:

La implementación puede ser técnicamente correcta pero funcionalmente incorrecta.

---

## Actualizar el código y olvidar la Specification

Consecuencia:

La documentación deja de representar el sistema real.

---

## Modificar Requirements durante el desarrollo sin registrarlo

Consecuencia:

Se pierde la trazabilidad de las decisiones.

---

# Integración con Azure DevOps

Una User Story puede permanecer abierta hasta que:

```text
User Story

↓

Specification

↓

Requirements

↓

Tasks

↓

Code

↓

Tests

↓

Reviews

↓

Done
```

La definición de "Done" deja de depender solo del código.

---

# Integración con GitHub

Una Pull Request puede incorporar una plantilla similar a esta:

```text
Specification

□ Referenciada

Requirements

□ Implementados

Tests

□ Agregados

Architecture

□ Sin cambios

Documentation

□ Actualizada
```

Este checklist ayuda a estandarizar las revisiones del equipo.

---

# Aplicación práctica

En un equipo que utiliza Azure DevOps, GitHub, Copilot y Claude Code el flujo recomendado sería:

```text
Developer

↓

Implement Task

↓

Copilot / Claude Code

↓

Tests

↓

AI Review

↓

Specification Review

↓

Code Review

↓

Pull Request

↓

Merge
```

Las revisiones ya no se limitan al código.

También verifican que el conocimiento del sistema siga siendo consistente.

---

# Beneficios

Implementar Specification Review aporta:

* mayor trazabilidad;
* menos retrabajo;
* menor riesgo de cambios de alcance;
* mejor documentación;
* mejor colaboración entre negocio y desarrollo;
* mejor contexto para agentes IA.

---

# Resumen

Code Review y Specification Review responden preguntas diferentes.

| Revisión             | Pregunta principal              |
| -------------------- | ------------------------------- |
| Code Review          | ¿Está bien implementado?        |
| Specification Review | ¿Está implementado lo correcto? |

La combinación de ambas revisiones reduce tanto los errores técnicos como los errores de interpretación.

En SDD, una Pull Request no representa únicamente un cambio de código.

Representa la evolución coordinada de:

* conocimiento;
* implementación;
* validación.

---

# Próximo capítulo

```text
docs/module-03-specification-workflow/

└── 07-testing-and-validation-workflow.md
```

En el siguiente capítulo construiremos el flujo completo de validación: cómo derivar casos de prueba directamente desde los Requirements, cómo mantener la trazabilidad entre Specification y tests, y cómo integrar QA y agentes IA en el proceso de validación.
