# OpenSpec con agentes IA

## Introducción

La aparición de herramientas como:

* GitHub Copilot;
* Claude Code;
* agentes de desarrollo autónomos;

cambió la forma en que pensamos el desarrollo de software.

Sin embargo, existe un problema:

> Una IA puede escribir código rápidamente, pero no necesariamente entiende qué código debe escribir.

La diferencia entre una buena implementación y una implementación incorrecta normalmente no está en la capacidad de generar código.

Está en la calidad del contexto entregado.

---

# El problema del desarrollo asistido por IA

Un flujo básico suele ser:

```text id="aiold01"
Developer

"Create a customer benefits page"


        ↓


AI


        ↓


Generated Code
```

El resultado depende de muchas suposiciones:

* arquitectura;
* patrones existentes;
* reglas de negocio;
* restricciones;
* convenciones.

---

# El modelo SDD + IA

Con OpenSpec:

```text id="ainew01"
Business Need

        ↓

Specification

        ↓

Requirements

        ↓

Design

        ↓

Tasks

        ↓

AI Agent

        ↓

Implementation
```

La IA deja de improvisar.

Ejecuta una intención previamente definida.

---

# Specification como contexto para IA

Una Specification funciona como un paquete de contexto.

Ejemplo:

```text id="context01"
specs/

customer-benefits/

├── spec.md

├── requirements.md

├── design.md

├── tasks.md

└── test-plan.md
```

Un agente puede consumir todo este contexto.

---

# Contexto mínimo recomendado

Para una tarea simple:

```text id="context02"
Task:

Implement TASK-003.


Read:

requirements.md

design.md


Validate:

test-plan.md
```

---

Para una tarea compleja:

```text id="context03"
Project Context:

Architecture:

Angular 20


Patterns:

Standalone components

NgRx


Specification:

customer-benefits


Requirements:

R001-R005


Task:

TASK-003


Validation:

Jest tests
```

---

# El rol del desarrollador cambia

Antes:

```text id="developer-old01"
Developer

↓

Escribir código
```

---

Con agentes:

```text id="developer-new01"
Developer

↓

Definir intención

↓

Crear contexto

↓

Delegar ejecución

↓

Revisar resultado
```

---

El desarrollador se convierte en:

* diseñador de soluciones;
* creador de contexto;
* revisor técnico.

---

# OpenSpec como contrato con la IA

Una Specification establece límites.

Ejemplo:

```markdown id="contract01"
Constraints:

- Use existing state management.
- Do not create new dependencies.
- Follow current architecture patterns.
- Add automated tests.
```

---

La IA entiende:

No solamente qué hacer.

También qué NO hacer.

---

# Instrucciones para agentes

Una buena instrucción tiene:

```text id="promptstructure01"
Context

+

Goal

+

Constraints

+

Validation
```

---

Ejemplo:

```text id="prompt01"
Context:

Implement customer benefits feature.


Goal:

Create benefits filtering.


Requirements:

R001-R003.


Constraints:

Use existing BenefitsStore.


Validation:

Add Jest tests.
```

---

# OpenSpec y GitHub Copilot

Copilot funciona especialmente bien cuando tiene:

* archivos cercanos;
* convenciones claras;
* contexto arquitectónico.

Ejemplo:

Estructura:

```text id="copilot01"
src/

specs/

customer-benefits/
```

El desarrollador puede trabajar:

```text id="copilot02"
Implement TASK-002 based on:

/specs/customer-benefits/design.md
```

---

# OpenSpec y Claude Code

Claude Code puede utilizar una Specification como guía de ejecución.

Ejemplo:

```text id="claude01"
Analyze:

/specs/customer-benefits/


Understand:

- requirements
- design
- existing implementation


Execute:

TASK-004


Before changing code:

Explain approach.
```

---

Este patrón introduce un punto importante:

## Human-in-the-middle

El humano valida antes de cambios importantes.

---

# Flujo recomendado con agentes

```text id="agentflow01"
1. Developer selects Task


          ↓


2. Agent reads Specification


          ↓


3. Agent proposes plan


          ↓


4. Human approves


          ↓


5. Agent implements


          ↓


6. Tests execute


          ↓


7. Human reviews
```

---

# Por qué evitar prompts gigantes

Un error frecuente:

```text id="badprompt01"
Build the entire customer portal.
```

Problemas:

* demasiado contexto;
* demasiadas decisiones;
* difícil validar resultado.

---

Mejor:

```text id="goodprompt01"
Implement TASK-003.

Specification:

customer-benefits

Scope:

Only filtering capability.

Do not modify:

authentication module.
```

---

# División de responsabilidades

Una arquitectura madura distribuye responsabilidades:

```text id="responsibility01"
Human

Define intention

        ↓

OpenSpec

Stores knowledge

        ↓

AI Agent

Executes tasks

        ↓

Tests

Validate behavior
```

---

# Agentes especializados

En una evolución avanzada pueden existir agentes diferentes.

Ejemplo:

```text id="agents01"
Requirements Agent

↓

Creates specifications


Design Agent

↓

Proposes architecture


Coding Agent

↓

Implements tasks


Testing Agent

↓

Creates validation
```

---

Pero todos deben consumir la misma fuente:

```text id="agentsource01"
/specs
```

---

# OpenSpec como memoria para agentes

Uno de los mayores problemas de IA es la pérdida de contexto.

Cada conversación empieza prácticamente desde cero.

OpenSpec permite:

```text id="memory01"
Conversation Context

        +

Repository Knowledge

        +

Specification History
```

---

El repositorio se convierte en memoria persistente.

---

# Guardrails para agentes

Una empresa necesita límites.

Ejemplos:

## No modificar arquitectura sin aprobación

```text id="guardrail01"
Architecture changes require ADR.
```

---

## No agregar dependencias sin justificar

```text id="guardrail02"
New libraries require approval.
```

---

## No modificar fuera del scope

```text id="guardrail03"
Only implement current specification.
```

---

# Métricas de calidad

La adopción de IA debe medirse.

Ejemplos:

## Specification completeness

¿Las tareas tienen contexto suficiente?

---

## AI success rate

¿Cuántas implementaciones requieren retrabajo?

---

## Review efficiency

¿Las PR generadas son más fáciles de revisar?

---

# Ejemplo completo

Specification:

```text id="examplefull01"
Customer Invoice Download
```

Task:

```text id="examplefull02"
TASK-003

Create invoice download button.
```

Contexto al agente:

```text id="examplefull03"
Read:

/specs/invoice-download/


Implement:

TASK-003


Requirements:

R001

Authenticated users only.


Design:

Use existing InvoiceService.


Validation:

Add component tests.
```

Resultado esperado:

* código alineado;
* tests incluidos;
* sin decisiones improvisadas.

---

# Errores comunes

## Usar IA sin Specification

Resultado:

Código rápido pero inconsistente.

---

## Crear Specification después

Resultado:

Documentación histórica.

---

## Permitir decisiones arquitectónicas autónomas

Resultado:

Divergencia técnica.

---

# Resumen

OpenSpec convierte la IA en un acelerador controlado.

El modelo correcto:

```text id="finalmodel01"
Human

Define intent


↓

OpenSpec

Captures knowledge


↓

AI Agent

Executes


↓

Tests

Validate


↓

Human

Approves
```

La IA no reemplaza la ingeniería.

La amplifica cuando existe una base de conocimiento estructurada.

---

# Próximo capítulo

El siguiente archivo será:

```text id="next10"
docs/module-02-openspec/

└── 11-exercises.md
```

donde cerraremos el módulo con ejercicios prácticos construyendo Specifications completas y simulando un flujo real con Azure DevOps + GitHub + IA.
