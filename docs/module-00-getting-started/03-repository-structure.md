# Estructura de un repositorio SDD

## Introducción

En un enfoque tradicional, un repositorio suele estar organizado alrededor del código fuente.

Una estructura común es:

```text
project/

├── src/
├── tests/
├── package.json
├── README.md
└── configuration files
```

Esta organización funciona cuando los principales consumidores del repositorio son desarrolladores.

Sin embargo, en un entorno donde participan agentes de Inteligencia Artificial, el repositorio necesita contener mucho más contexto.

En SDD, el repositorio se convierte en la fuente de conocimiento del sistema.

---

# Principio fundamental

La estructura recomendada sigue esta idea:

> Todo conocimiento necesario para modificar el sistema debe estar versionado junto al sistema.

Esto incluye:

* especificaciones;
* decisiones arquitectónicas;
* contratos;
* reglas de negocio;
* planes de pruebas;
* instrucciones para agentes.

---

# Estructura general recomendada

Una estructura inicial puede ser:

```text
project/

├── src/
│
├── tests/
│
├── specs/
│
├── architecture/
│
├── adr/
│
├── prompts/
│
├── docs/
│
├── scripts/
│
├── README.md
│
└── configuration files
```

Cada carpeta tiene una responsabilidad específica.

---

# src/

Contiene el código fuente de la aplicación.

Ejemplo:

```text
src/

├── frontend/
│
├── backend/
│
└── shared/
```

El código implementa la Specification.

No debería contener decisiones de negocio que solamente existan dentro del código.

---

# tests/

Contiene las pruebas automatizadas.

Ejemplo:

```text
tests/

├── unit/
├── integration/
└── e2e/
```

En SDD los tests están relacionados con los requisitos definidos previamente.

Una prueba no debería existir solamente porque un desarrollador decidió crearla, sino porque verifica un comportamiento esperado.

---

# specs/

Esta es la carpeta principal de SDD.

Contiene las Specifications del sistema.

Ejemplo:

```text
specs/

├── update-address/
│
│   ├── spec.md
│   ├── requirements.md
│   ├── design.md
│   ├── tasks.md
│   └── test-plan.md
│
└── login/
    ├── spec.md
    ├── requirements.md
    ├── design.md
    ├── tasks.md
    └── test-plan.md
```

Cada funcionalidad importante tiene su propia Specification.

---

# spec.md

Es el documento principal.

Contiene:

* objetivo;
* contexto;
* alcance;
* referencias;
* estado actual.

Ejemplo:

```markdown
# Update Address

## Goal

Allow authenticated users to update their delivery address.

## Context

Customers currently need support assistance.

## Scope

Included:
- Update address.
- Validate information.

Excluded:
- Address history.
```

---

# requirements.md

Describe qué debe hacer el sistema.

Ejemplo:

```markdown
## Requirement R001

Given an authenticated user

When the user submits a valid address

Then the system stores the new information.
```

Los requisitos deben ser claros y verificables.

---

# design.md

Describe la solución técnica.

Puede incluir:

* arquitectura;
* componentes;
* APIs;
* diagramas;
* modelos.

Ejemplo:

```markdown
Frontend:

- AddressComponent
- AddressService

Backend:

- PUT /customers/{id}/address

Database:

- CustomerAddress table
```

---

# tasks.md

Divide la implementación.

Ejemplo:

```markdown
- [ ] Create backend endpoint
- [ ] Add validation rules
- [ ] Create frontend form
- [ ] Add unit tests
- [ ] Add integration tests
```

Estas tareas pueden sincronizarse con Azure DevOps.

---

# test-plan.md

Define cómo comprobar la funcionalidad.

Ejemplo:

```markdown
Scenario:

User updates address successfully.

Expected:

Address is persisted and confirmation is displayed.
```

---

# architecture/

Contiene documentación transversal.

Ejemplos:

```text
architecture/

├── system-context.md
├── frontend.md
├── backend.md
├── integrations.md
└── diagrams/
```

Aquí viven decisiones que afectan a todo el sistema.

---

# adr/

ADR significa Architecture Decision Record.

Esta carpeta conserva decisiones importantes.

Ejemplo:

```text
adr/

├── ADR-001-use-ngrx.md
├── ADR-002-api-gateway.md
└── ADR-003-authentication.md
```

Un ADR responde:

* qué decisión tomamos;
* por qué la tomamos;
* qué alternativas evaluamos.

---

# prompts/

En proyectos con IA es recomendable versionar prompts importantes.

Ejemplo:

```text
prompts/

├── claude-code/
│
├── github-copilot/
│
└── agents/
```

Esto permite reutilizar patrones exitosos.

Ejemplo:

```markdown
You are implementing a feature based on this specification.

Rules:

- Follow existing architecture.
- Do not modify unrelated files.
- Create tests.
```

---

# docs/

Documentación general del proyecto.

Ejemplo:

```text
docs/

├── onboarding.md
├── development-guide.md
└── contribution-guide.md
```

---

# Relación entre elementos

La visión completa sería:

```text
                    Azure DevOps

                         │

                         ▼

                   Specification

                         │

        ┌────────────────┼────────────────┐

        ▼                ▼                ▼

     Design          Tasks           Tests

        │                │                │

        └────────────────┼────────────────┘

                         ▼

                       Code

                         │

                         ▼

                    Pull Request
```

---

# Repositorio como memoria del sistema

En SDD el repositorio deja de ser únicamente un lugar donde almacenar código.

Se convierte en la memoria colectiva del proyecto.

Cuando un nuevo desarrollador llega, o cuando un agente de IA comienza a trabajar, el conocimiento necesario está disponible.

---

# Reglas recomendadas

## Mantener Specifications pequeñas

Una Specification debe representar una capacidad concreta.

Evitar documentos gigantes imposibles de mantener.

---

## Versionar junto al código

Un cambio de código importante debería tener un cambio correspondiente en la Specification.

---

## Revisar Specifications en Pull Requests

La revisión no debe enfocarse solamente en código.

También debe validar si la Specification sigue siendo correcta.

---

## Diseñar pensando en humanos e IA

La documentación debe ser:

* clara;
* estructurada;
* explícita;
* sin información implícita.

---

# Resumen

Un repositorio SDD agrega una capa de conocimiento encima del código.

La estructura recomendada permite que:

* los desarrolladores comprendan el sistema;
* los arquitectos documenten decisiones;
* los testers conozcan los escenarios esperados;
* los agentes de IA tengan contexto suficiente.

El repositorio deja de ser solamente un almacén de código y se transforma en la fuente de verdad del sistema.

---

# Próximo capítulo

En el siguiente capítulo definiremos el flujo completo de desarrollo utilizando SDD:

Azure DevOps → OpenSpec → Desarrollo asistido por IA → Pull Request → Producción.
