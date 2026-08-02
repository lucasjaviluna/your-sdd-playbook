# Testing y Validation Workflow

## Introducción

En muchos equipos el testing comienza cuando el desarrollo ha terminado.

El flujo suele ser:

```text
Developer

↓

Code Complete

↓

QA

↓

Bug Report

↓

Developer

↓

Fix

↓

QA
```

Este modelo genera un ciclo de retroalimentación tardío.

Los problemas se descubren cuando la implementación ya existe.

Specification-Driven Development propone un enfoque diferente:

> **La estrategia de validación se define antes de escribir código.**

La validación deja de ser una actividad posterior y pasa a formar parte del diseño de la solución.

---

# El cambio de paradigma

En un flujo tradicional:

```text
Requirements

↓

Code

↓

Tests
```

En SDD:

```text
Requirements

↓

Validation Strategy

↓

Implementation

↓

Automated Tests

↓

Acceptance Validation
```

Los tests nacen de los Requirements, no del código.

---

# Principio fundamental

Cada Requirement verificable debe tener al menos una evidencia de validación.

Visualmente:

```text
Requirement

↓

Acceptance Criteria

↓

Test Scenario

↓

Automated Test

↓

Execution Result
```

Si un Requirement no puede validarse, probablemente no está suficientemente definido.

---

# Trazabilidad completa

Uno de los mayores beneficios de SDD es poder recorrer todo el ciclo.

```text
Business Need

↓

User Story

↓

Specification

↓

Requirement R-001

↓

Task T-003

↓

Pull Request #245

↓

InvoiceDownloadComponent.spec.ts

↓

Pipeline #1284
```

Ante un defecto en producción podemos responder rápidamente:

* ¿Qué Requirement implementaba?
* ¿Qué pruebas existían?
* ¿Qué Pull Request introdujo el cambio?
* ¿Qué Specification debemos revisar?

---

# Tipos de validación

Una funcionalidad moderna suele requerir distintos niveles de validación.

| Nivel               | Objetivo                          |
| ------------------- | --------------------------------- |
| Unit Testing        | Validar componentes individuales  |
| Integration Testing | Validar interacción entre módulos |
| API Testing         | Validar contratos entre servicios |
| End-to-End Testing  | Validar el flujo del usuario      |
| Acceptance Testing  | Validar el Requirement de negocio |

No todas las funcionalidades necesitan el mismo nivel de profundidad.

---

# Del Requirement al Test

Supongamos el siguiente Requirement:

```markdown
R-002

Given:
Authenticated customer

When:
Customer selects an invoice

Then:
The invoice PDF is downloaded.
```

De este Requirement podemos derivar varios escenarios.

```text
Caso 1
Descarga correcta.

Caso 2
Factura inexistente.

Caso 3
Sesión expirada.

Caso 4
Error del servicio.

Caso 5
Cliente intenta descargar una factura ajena.
```

Observa que todos los escenarios nacen del comportamiento esperado y no del código.

---

# Test Plan

Cada Specification debería incluir un plan de validación.

Ejemplo:

```text
specs/

invoice-download/

├── spec.md
├── requirements.md
├── design.md
├── tasks.md
└── test-plan.md
```

El archivo `test-plan.md` no contiene implementaciones.

Contiene la estrategia de validación.

Ejemplo:

```markdown
## Requirement

R-002

### Validation

- Unit Test
- Integration Test
- Negative Scenario
- Authorization Test
```

Esto permite que QA y desarrollo compartan la misma visión.

---

# Caso de estudio

## Feature

Invoice Download

Requirement:

```text
Cliente autenticado puede descargar sus facturas.
```

Antes de escribir código, el equipo identifica los escenarios.

### Escenarios positivos

* Descargar una factura existente.
* Descargar varias facturas consecutivas.
* Descargar desde distintos navegadores compatibles.

### Escenarios negativos

* Factura inexistente.
* Usuario no autenticado.
* Usuario autenticado sin permisos.
* Error de red.
* Error del backend.
* Archivo corrupto.

El resultado es una cobertura funcional mucho más completa.

---

# ¿Quién define los escenarios?

Una práctica habitual es pensar que los tests son responsabilidad exclusiva de QA.

En SDD los escenarios se construyen de manera colaborativa.

| Rol           | Aporte                              |
| ------------- | ----------------------------------- |
| Product Owner | Criterios de aceptación             |
| Developer     | Casos técnicos                      |
| QA            | Casos límite y negativos            |
| Arquitecto    | Restricciones técnicas              |
| AI            | Propuesta de escenarios adicionales |

Cada perspectiva descubre riesgos diferentes.

---

# El papel de los agentes IA

Los agentes pueden ayudar a generar propuestas de validación.

Ejemplo de contexto:

```text
Read:

requirements.md

design.md

Generate:

- Unit test scenarios
- Integration test scenarios
- Edge cases
- Negative scenarios

Do not generate code yet.
```

El resultado esperado no es una suite de pruebas completa.

Es una revisión de cobertura.

Posteriormente el desarrollador o QA decide qué automatizar.

---

# Automatización

Cuando una Task se implementa, la automatización debe responder directamente a los Requirements.

Ejemplo:

```text
Requirement

R-002

↓

Test

InvoiceDownloadComponent.spec.ts

↓

Scenario

Authenticated customer downloads invoice successfully.
```

No es recomendable escribir pruebas que validen comportamientos no documentados, salvo que se descubra un defecto y la Specification se actualice.

---

# Definition of Done orientada a validación

Una Task puede considerarse terminada cuando:

* El Requirement fue implementado.
* Existe evidencia de validación.
* Las pruebas automatizadas pasan correctamente.
* Los escenarios negativos relevantes fueron considerados.
* La Specification refleja el comportamiento final.

---

# Pipeline de validación

Un pipeline típico podría ser:

```text
Developer Push

↓

Static Analysis

↓

Unit Tests

↓

Integration Tests

↓

Build

↓

End-to-End Tests

↓

Package

↓

Deploy
```

Cada etapa valida una parte distinta de la Specification.

---

# Aplicación en un equipo real

Supongamos el siguiente flujo:

1. El Product Owner crea la User Story en Azure DevOps.
2. El equipo genera la Specification en OpenSpec.
3. Durante el refinamiento se definen los escenarios de prueba.
4. El desarrollador implementa una Task utilizando la Specification como contexto.
5. Copilot y Claude Code ayudan a generar código y pruebas.
6. La Pull Request incluye referencias a los Requirements implementados.
7. El pipeline ejecuta las pruebas automatizadas.
8. QA valida los criterios de aceptación definidos originalmente.
9. La funcionalidad se libera a producción.

En ningún momento los tests aparecen "al final". Forman parte del proceso desde el inicio.

---

# Errores comunes

## Escribir pruebas solo después del desarrollo

Consecuencia:

Los escenarios negativos suelen olvidarse.

---

## Crear tests basados únicamente en la implementación

Consecuencia:

Si la implementación es incorrecta, los tests también lo serán.

---

## No mantener el Test Plan

Consecuencia:

La Specification y las pruebas dejan de representar el mismo comportamiento.

---

# Buenas prácticas

* Cada Requirement debe ser verificable.
* Cada Requirement importante debe tener al menos un escenario automatizado.
* Los escenarios negativos deben documentarse explícitamente.
* La estrategia de validación debe revisarse durante el refinamiento.
* La IA puede proponer escenarios, pero la aprobación corresponde al equipo.

---

# Resumen

En Specification-Driven Development el testing deja de ser la última etapa del proceso.

Se convierte en un elemento central que conecta:

```text
Requirement

↓

Validation Strategy

↓

Implementation

↓

Evidence
```

Esto mejora la calidad del software y fortalece la trazabilidad entre negocio, implementación y operación.

---

# Próximo capítulo

```text
docs/module-03-specification-workflow/

└── 08-release-and-operation.md
```

En el siguiente capítulo veremos cómo una Specification continúa siendo útil después del desarrollo: durante el despliegue, la operación, la resolución de incidentes y la evolución del producto. La idea es cerrar el ciclo completo de vida de una funcionalidad.
