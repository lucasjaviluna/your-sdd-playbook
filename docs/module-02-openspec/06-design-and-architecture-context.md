# Design y contexto arquitectónico en OpenSpec

## Introducción

Una Specification no debe detenerse en describir qué debe hacer el sistema.

Para poder implementar una funcionalidad necesitamos responder otra pregunta:

> ¿Cómo construiremos esta capacidad dentro del sistema existente?

El archivo `design.md` representa la transición entre:

```text id="k5f7s9"
Qué debe hacer el sistema

        ↓

Cómo será construido
```

---

# El propósito del Design

El objetivo del Design no es escribir código anticipadamente.

Su objetivo es definir:

* la estrategia de solución;
* los componentes involucrados;
* los puntos de integración;
* las restricciones técnicas;
* las decisiones relevantes.

---

# Design no es implementación

Es importante diferenciar:

## Requirement

Define comportamiento:

```text id="m4x7pa"
El cliente puede consultar sus beneficios.
```

---

## Design

Define solución:

```text id="8r3jkt"
Crear BenefitsComponent.

Consumir Benefits API.

Utilizar el patrón de estado existente.
```

---

## Implementation

Define código:

```typescript id="p0x8fd"
export class BenefitsComponent {

}
```

---

La relación correcta es:

```text id="f5r9nx"
Requirement

      ↓

Design

      ↓

Code
```

---

# Por qué el Design es importante en SDD

Sin Design, una IA o un desarrollador puede implementar una solución válida pero incorrecta.

Ejemplo:

Requirement:

```text id="x8m2qv"
El usuario debe ver sus beneficios.
```

Una IA podría crear:

```text id="c9p4ay"
NewBenefitsService

NewBenefitsStore

NewBenefitsComponent
```

Pero el sistema ya tiene:

```text id="k6m1zw"
BenefitsFacade

CustomerStore

SharedComponents
```

El código funciona.

Pero rompe la arquitectura existente.

---

# El Design como contexto arquitectónico

Una aplicación empresarial tiene reglas no escritas:

* patrones utilizados;
* librerías aprobadas;
* convenciones;
* restricciones.

Muchas veces ese conocimiento está en la cabeza del equipo.

OpenSpec busca hacerlo explícito.

---

Ejemplo:

```markdown id="v2m8ks"
## Architecture Context


Application:

Angular 20


State Management:

NgRx


Component Pattern:

Standalone components


Testing:

Jest
```

---

Esto permite que nuevos miembros y agentes IA entiendan el entorno.

---

# Estructura recomendada de design.md

Un Design puede contener:

```text id="p8z5qd"
design.md

├── Architecture Context
├── Components
├── Data Flow
├── API Integration
├── State Management
├── Security Considerations
├── Error Handling
└── Decisions
```

---

# 1. Architecture Context

Describe dónde vive la funcionalidad.

Ejemplo:

```markdown id="r2f8mw"
## Architecture Context


Frontend:

Angular application


Pattern:

Feature-based architecture


State:

NgRx Store


API Communication:

HTTP Services
```

---

# 2. Components

Define piezas principales.

Ejemplo:

```markdown id="g3z8xn"
## Components


BenefitsPageComponent

Responsible for displaying benefits.


BenefitsCardComponent

Responsible for benefit visualization.
```

---

No incluye código.

Solo responsabilidades.

---

# 3. Data Flow

Describe cómo circula la información.

Ejemplo:

```text id="w6q3vn"
User

 ↓

BenefitsPageComponent

 ↓

BenefitsFacade

 ↓

BenefitsService

 ↓

Benefits API
```

---

Esto es muy valioso para agentes IA.

---

# 4. API Integration

Define dependencias externas.

Ejemplo:

```markdown id="8v0q3m"
## API


GET

/api/customers/{id}/benefits


Response:

Benefit[]
```

---

También puede documentar:

* autenticación;
* errores;
* contratos.

---

# 5. State Management

Especialmente importante en aplicaciones frontend.

Ejemplo:

```markdown id="d7m1qx"
## State


Use existing CustomerBenefitsStore.


State:

- benefits
- loading
- error
```

---

Evita que cada implementación invente su propio estado.

---

# 6. Security Considerations

Debe incluir riesgos relevantes.

Ejemplo:

```markdown id="n5c8mv"
## Security


Only authenticated customers
can access benefits.


Customer can only access
own benefits.
```

---

# 7. Error Handling

Define comportamiento ante fallos.

Ejemplo:

```markdown id="m8k4tz"
## Error Handling


API unavailable:

Display retry option.


Empty result:

Show empty state.
```

---

# Design y arquitectura empresarial

En sistemas grandes, una funcionalidad puede impactar:

* frontend;
* backend;
* bases de datos;
* APIs;
* infraestructura.

El Design permite visualizar ese impacto.

Ejemplo:

```text id="b6z2pa"
Customer Benefits


Frontend

Benefits Module


        ↓


BFF

Benefits Endpoint


        ↓


Backend

Benefits Service


        ↓


Database

Benefits Table
```

---

# Design y ADRs

No todas las decisiones necesitan un ADR.

Una regla práctica:

Crear ADR cuando:

* afecta arquitectura;
* tiene impacto de largo plazo;
* existen alternativas relevantes.

Ejemplo:

```text id="r9q4mf"
Decision:

Use BFF instead of direct frontend API calls.


Reason:

Security and aggregation.
```

---

# Design como contexto para IA

Una IA sin Design puede hacer suposiciones.

Ejemplo:

Prompt:

```text id="x7c1mz"
Create benefits page.
```

---

Con Design:

```text id="s4w8pk"
Implement BenefitsPageComponent.


Architecture:

Angular standalone components.


State:

Use existing BenefitsStore.


API:

Use BenefitsService.


Testing:

Jest + Angular Testing Library.
```

---

La diferencia es enorme.

---

# Design y evolución del sistema

Un error común:

Crear Design solamente para funcionalidades nuevas.

También es útil para:

* migraciones;
* refactors;
* cambios arquitectónicos.

Ejemplo:

```text id="q2k7wm"
Migration:

NgModules → Standalone Components
```

La Specification puede documentar:

* estado actual;
* estado objetivo;
* estrategia.

---

# Relación completa

Al finalizar una Specification tenemos:

```text id="x4m8qs"
spec.md

¿Por qué?


        ↓


requirements.md

¿Qué?


        ↓


design.md

¿Cómo?


        ↓


tasks.md

Qué hacer


        ↓


test-plan.md

Cómo validar
```

---

# Errores comunes

## Escribir demasiado detalle técnico

Incorrecto:

```text id="g8n2vr"
Create file benefits.component.ts
```

Eso es implementación.

---

## No documentar restricciones

Incorrecto:

```text id="y5v8na"
Create component.
```

Falta contexto.

---

## Ignorar arquitectura existente

El Design debe responder:

> ¿Cómo encaja esto con lo que ya existe?

---

# Checklist de Design

Antes de aprobar:

✅ ¿Sabemos qué componentes participan?
✅ ¿Sabemos cómo fluye la información?
✅ ¿Conocemos integraciones externas?
✅ ¿Respetamos arquitectura existente?
✅ ¿Un nuevo desarrollador podría implementarlo?
✅ ¿Un agente IA tendría suficiente contexto?

---

# Resumen

El Design dentro de OpenSpec:

* conecta requisitos con implementación;
* protege la arquitectura;
* reduce decisiones improvisadas;
* mejora el trabajo con IA.

La idea central:

> Requirements definen el comportamiento. Design define la solución.

---

# Próximo capítulo

El siguiente archivo será:

```text id="n2v6rx"
docs/module-02-openspec/

└── 07-tasks-and-execution-plan.md
```

donde veremos cómo transformar una Specification aprobada en un plan de ejecución accionable para desarrolladores y agentes IA.
