# OpenSpec con Azure DevOps

## Introducción

Muchas organizaciones ya tienen procesos establecidos:

* Azure DevOps para backlog;
* Scrum/Kanban;
* User Stories;
* Sprint Planning;
* seguimiento de trabajo.

Adoptar SDD no significa reemplazar estos procesos.

La idea es complementar el flujo existente agregando una capa de conocimiento estructurado.

---

# El problema actual

Un flujo tradicional suele verse así:

```text id="traditional01"
Azure DevOps

Epic

 ↓

Feature

 ↓

User Story

 ↓

Acceptance Criteria


 ↓


Developer interpreta


 ↓


Código
```

---

El problema:

La información necesaria para implementar queda distribuida entre:

* reuniones;
* comentarios;
* chats;
* conocimiento del equipo.

---

Ejemplo:

User Story:

```text id="story01"
Como cliente quiero descargar mi factura.
```

Acceptance Criteria:

```text id="story02"
El usuario puede descargar la factura.
```

Preguntas que quedan abiertas:

* ¿Qué formato?
* ¿Qué ocurre si no existe?
* ¿Qué permisos necesita?
* ¿Cómo se valida seguridad?
* ¿Qué API existe?
* ¿Qué componentes reutilizar?

---

# El nuevo modelo con OpenSpec

Con SDD agregamos una capa intermedia:

```text id="openspecflow01"
Azure DevOps

Epic

 ↓

Feature

 ↓

User Story


        ↓


OpenSpec

Specification


        ↓


Requirements

Design

Tasks

Tests


        ↓


Código
```

---

# Responsabilidad de cada herramienta

Una clave para evitar duplicación es definir responsabilidades.

---

# Azure DevOps

Debe continuar gestionando:

## Gestión de producto

* Epics;
* Features;
* User Stories;
* Prioridades.

---

## Gestión del trabajo

* Sprint;
* asignaciones;
* estados;
* métricas.

---

## Comunicación del equipo

* comentarios;
* discusiones;
* seguimiento.

---

# OpenSpec

Debe gestionar:

## Conocimiento técnico-funcional

* contexto;
* requisitos;
* reglas;
* diseño;
* decisiones.

---

## Preparación para desarrollo

* tareas técnicas;
* escenarios;
* validaciones.

---

# GitHub

Debe gestionar:

* código;
* historial;
* Pull Requests;
* revisiones.

---

# IA

Debe consumir:

* Specifications;
* código existente;
* arquitectura;
* convenciones.

---

# Flujo completo recomendado

Ejemplo:

## Paso 1 - Producto crea User Story

Azure DevOps:

```text id="step01"
US-5001

Customer downloads invoice
```

---

## Paso 2 - Equipo crea Specification

Repositorio:

```text id="step02"
specs/

invoice-download/

├── spec.md

├── requirements.md

├── design.md

└── test-plan.md
```

---

## Paso 3 - Refinamiento

Participan:

* Product Owner;
* Arquitecto;
* Developers;
* QA.

Se validan:

* alcance;
* reglas;
* diseño.

---

## Paso 4 - Desarrollo

Developer o IA recibe contexto:

```text id="step04"
Implement invoice-download.


Read:

/specs/invoice-download/


Follow:

design.md

requirements.md

test-plan.md
```

---

## Paso 5 - Pull Request

Incluye:

```text id="step05"
PR

├── Code

├── Tests

└── Specification
```

---

# Mapeo entre Azure DevOps y OpenSpec

Ejemplo:

| Azure DevOps        | OpenSpec              |
| ------------------- | --------------------- |
| Epic                | Domain / Capability   |
| Feature             | Specification group   |
| User Story          | Specification trigger |
| Acceptance Criteria | Requirements          |
| Task                | Implementation Task   |
| Test Case           | Test Plan             |

---

# Ejemplo práctico

## Azure DevOps

User Story:

```text id="example01"
US-8001

Como cliente quiero actualizar mi dirección.
```

---

## OpenSpec

spec.md:

```markdown
# Customer Address Update

## Goal

Allow customers to update their address.

## Scope

Included:

- Edit address.
- Validate fields.

Excluded:

- Address history management.
```

---

requirements.md:

```markdown
R001

Customer can update address.


R002

Invalid addresses are rejected.


R003

Changes are audited.
```

---

design.md:

```markdown
Frontend:

AddressFormComponent


State:

CustomerStore


API:

PUT /customers/{id}/address
```

---

# Evitar duplicación

Un error común al adoptar SDD es copiar todo:

Azure DevOps:

```text
User Story
Acceptance Criteria
Tasks
```

OpenSpec:

```text
User Story
Acceptance Criteria
Tasks
```

Esto genera dos fuentes de verdad.

---

La regla:

```text id="singletruth01"
Azure DevOps

=
Qué y cuándo


OpenSpec

=
Qué significa y cómo construirlo
```

---

# Integración con Pull Requests

Azure DevOps Work Item:

```text
US-8001
```

Pull Request:

```text
Related:

US-8001


Specification:

/specs/customer-address-update
```

---

La trazabilidad queda:

```text id="trace01"
Business Need

        ↓

Azure DevOps Story

        ↓

OpenSpec

        ↓

Commit

        ↓

Pull Request

        ↓

Release
```

---

# Uso con GitHub Copilot

Copilot funciona mejor con contexto cercano.

Ejemplo:

Menos efectivo:

```text
Create address form.
```

---

Más efectivo:

```text
Implement TASK-003.

Context:

/specs/customer-address-update/

Requirements:

R001-R003

Architecture:

Angular standalone components.

Tests:

Jest.
```

---

# Uso con Claude Code

Claude Code puede trabajar como agente orientado a Specification.

Ejemplo:

```text
Read:

/specs/customer-address-update/


Analyze:

- requirements
- design
- existing patterns


Implement:

TASK-002
```

---

# Modelo operativo recomendado para una empresa

```text id="operatingmodel01"
Product Team

        |

        ↓

Azure DevOps

        |

        ↓

Engineering Team

        |

        ↓

OpenSpec

        |

        ↓

GitHub + AI Agents

        |

        ↓

Production
```

---

# Madurez progresiva

No es necesario implementar todo desde el día uno.

## Nivel 1

Specifications básicas:

```text
spec.md
requirements.md
```

---

## Nivel 2

Agregar:

```text
design.md
test-plan.md
```

---

## Nivel 3

Integrar:

* validaciones CI;
* agentes IA;
* métricas.

---

## Nivel 4

Gobierno completo:

* catálogo de Specifications;
* búsqueda semántica;
* memoria organizacional.

---

# Checklist de adopción

Antes de comenzar:

✅ ¿Cada User Story importante tiene Specification?
✅ ¿La Specification vive cerca del código?
✅ ¿Los Requirements son verificables?
✅ ¿El Design respeta arquitectura existente?
✅ ¿La IA recibe contexto suficiente?

---

# Resumen

OpenSpec no reemplaza Azure DevOps.

Lo complementa.

El modelo recomendado:

```text id="summary01"
Azure DevOps

Gestiona trabajo


+

OpenSpec

Gestiona conocimiento


+

GitHub

Gestiona cambios


+

IA

Acelera ejecución
```

El resultado es un ciclo de desarrollo donde la intención, el diseño y la implementación permanecen alineados.

---

# Próximo capítulo

El siguiente archivo será:

```text id="next09"
docs/module-02-openspec/

└── 10-openspec-with-ai-agents.md
```

donde veremos cómo preparar Specifications para trabajar con agentes IA como GitHub Copilot y Claude Code, incluyendo patrones de contexto, instrucciones y ejecución controlada.
