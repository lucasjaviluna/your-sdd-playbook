# Roles y responsabilidades en Specification-Driven Development

## Introducción

Specification-Driven Development no introduce nuevos roles dentro de una organización.

Lo que hace es redefinir las responsabilidades de los roles existentes respecto al conocimiento del sistema.

Cada participante aporta una parte diferente de la Specification.

El objetivo es que el conocimiento no dependa de una única persona.

---

# El principio fundamental

En un proyecto tradicional solemos pensar:

```text
Product Owner

↓

Developer

↓

QA
```

En SDD pensamos en la construcción colaborativa del conocimiento.

```text
Business

        ↓

Product

        ↓

Architecture

        ↓

Development

        ↓

QA

        ↓

Operations
```

Todos colaboran sobre la misma Specification.

---

# Mapa general de responsabilidades

| Rol              | Principal responsabilidad       |
| ---------------- | ------------------------------- |
| Product Owner    | Problema de negocio             |
| Business Analyst | Reglas del negocio              |
| Arquitecto       | Diseño de alto nivel            |
| Developer        | Diseño técnico e implementación |
| QA               | Estrategia de validación        |
| DevOps           | Pipeline y despliegue           |
| AI Agent         | Ejecución asistida              |
| Tech Lead        | Aprobación técnica              |

---

# Product Owner

El Product Owner es responsable del **por qué**.

Debe responder preguntas como:

* ¿Qué problema queremos resolver?
* ¿Qué valor genera?
* ¿Quién utilizará esta funcionalidad?
* ¿Cuál es la prioridad?

No debería definir detalles técnicos.

---

## Artefactos donde participa

Principalmente:

```text
spec.md
```

Especialmente:

* Business Context
* Goal
* Scope
* Success Criteria

---

## Ejemplo

Incorrecto:

```text
Crear un componente Angular.
```

Eso es una decisión técnica.

---

Correcto:

```text
Permitir que el cliente descargue sus facturas
sin contactar al soporte.
```

---

# Business Analyst

En organizaciones donde existe este rol:

Su foco está en transformar necesidades en reglas.

Ejemplos:

* reglas del negocio;
* excepciones;
* actores;
* restricciones funcionales.

---

Participa principalmente en:

```text
requirements.md

business-rules.md
```

---

# Arquitecto

El arquitecto responde:

> ¿Cuál es la mejor dirección técnica?

No implementa cada tarea.

Define:

* patrones;
* integración;
* impacto;
* decisiones arquitectónicas.

---

Participa principalmente en:

```text
design.md
```

---

Ejemplo:

```text
Frontend

↓

NgRx Store

↓

Invoice Service

↓

Invoice API
```

---

También identifica cuándo es necesario crear un ADR.

---

# Tech Lead

Muchas organizaciones tienen un Tech Lead además del arquitecto.

Su responsabilidad es:

* revisar consistencia;
* asegurar estándares;
* coordinar implementación.

Durante el refinamiento responde preguntas como:

* ¿Es implementable?
* ¿Existe deuda técnica?
* ¿Qué riesgos vemos?

---

# Developer

El desarrollador deja de ser únicamente quien escribe código.

Ahora también participa en:

* refinamiento;
* diseño técnico;
* definición de tareas;
* mejora continua de la Specification.

---

Responsabilidades principales:

```text
requirements.md

design.md

tasks.md
```

---

El desarrollador también valida que:

* la Specification sea implementable;
* los Requirements sean consistentes;
* las Tasks tengan el nivel adecuado.

---

# QA

QA participa mucho antes.

No espera a que exista código.

Su trabajo comienza durante el refinamiento.

---

Responsabilidades:

* definir escenarios;
* identificar casos límite;
* descubrir ambigüedades;
* diseñar estrategia de pruebas.

---

Participa principalmente en:

```text
test-plan.md
```

---

Ejemplo:

Requirement:

```text
Customer downloads invoice.
```

QA pregunta:

```text
¿Y si la factura ya no existe?

¿Y si el PDF falla?

¿Y si la sesión expiró?
```

---

Estas preguntas mejoran la Specification.

---

# DevOps

DevOps normalmente participa menos en funcionalidades pequeñas.

Pero sí en cambios que afectan:

* infraestructura;
* despliegues;
* observabilidad;
* pipelines;
* ambientes.

---

Puede agregar restricciones como:

```text
Deployment requires feature flag.

Rollback supported.

Metrics required.
```

---

# Security

En empresas grandes suele existir un equipo de seguridad.

Su responsabilidad es revisar:

* autenticación;
* autorización;
* manejo de datos;
* auditoría.

---

Ejemplo:

```text
Only authenticated users
can download invoices.
```

---

# UX/UI

Los diseñadores también participan.

No escriben código.

Aportan:

* experiencia;
* accesibilidad;
* comportamiento esperado.

---

Ejemplo:

```text
Loading state.

Empty state.

Error state.

Responsive behavior.
```

---

# AI Agents

Los agentes IA no son responsables del diseño del producto.

Su responsabilidad es ejecutar tareas definidas.

Un agente recibe:

```text
Task

+

Requirements

+

Design

+

Constraints
```

Y devuelve:

* código;
* pruebas;
* documentación;
* propuestas.

---

Nunca debería definir objetivos de negocio.

---

# Human-in-the-loop

Uno de los principios fundamentales del curso.

La IA propone.

El humano decide.

Modelo:

```text
Specification

↓

AI

↓

Proposal

↓

Human Review

↓

Approval

↓

Merge
```

---

# Matriz RACI

Una forma útil de definir responsabilidades es una matriz RACI.

| Actividad              | PO | BA | Arq | TL | Dev | QA | DevOps | IA |
| ---------------------- | -- | -- | --- | -- | --- | -- | ------ | -- |
| Definir problema       | R  | A  | C   | C  | I   | I  | I      | I  |
| Escribir Specification | A  | R  | C   | C  | C   | C  | I      | I  |
| Definir Requirements   | C  | R  | C   | C  | C   | C  | I      | I  |
| Diseñar solución       | I  | C  | A   | R  | C   | I  | I      | I  |
| Crear Tasks            | I  | I  | C   | A  | R   | C  | I      | C  |
| Implementar            | I  | I  | I   | C  | A   | I  | I      | R  |
| Crear pruebas          | I  | I  | I   | C  | C   | A  | I      | C  |
| Aprobar PR             | I  | I  | C   | A  | R   | C  | I      | I  |

Leyenda:

* **R** → Responsible
* **A** → Accountable
* **C** → Consulted
* **I** → Informed

---

# Responsabilidades durante el workflow

```text
Idea

↓

Product Owner

↓

Specification

↓

Business + Architecture

↓

Requirements

↓

Developers + QA

↓

Tasks

↓

AI / Developers

↓

Code Review

↓

Release
```

---

# Un error frecuente

Pensar que la Specification pertenece únicamente al Product Owner.

Eso produce documentos funcionales sin valor para el desarrollo.

---

Otro error frecuente

Pensar que la Specification pertenece únicamente a desarrollo.

Eso produce documentos técnicamente correctos pero desconectados del negocio.

---

El modelo correcto

La Specification es propiedad del equipo.

Cada sección tiene un responsable principal, pero todos colaboran en su evolución.

---

# Aplicación práctica en tu empresa

Con el stack que describiste:

```text
Azure DevOps

↓

Product Owner

↓

User Story

↓

OpenSpec

↓

Tech Lead + Developers

↓

Claude Code / GitHub Copilot

↓

Pull Request

↓

QA

↓

Merge

↓

Release
```

En este modelo:

* Azure DevOps sigue siendo la fuente de planificación.
* OpenSpec se convierte en la fuente de conocimiento.
* GitHub es la fuente de implementación.
* Los agentes IA aceleran la ejecución, pero siempre bajo supervisión humana.

---

# Checklist de responsabilidades

Antes de comenzar el desarrollo verifica:

✅ El Product Owner definió el objetivo de negocio.

✅ Los Requirements fueron revisados.

✅ Arquitectura validó el diseño.

✅ QA participó en la estrategia de pruebas.

✅ Las Tasks están listas para ejecutarse.

✅ Los agentes IA tienen contexto suficiente.

---

# Resumen

Uno de los mayores beneficios de SDD es que hace explícita la responsabilidad sobre el conocimiento.

No existe una única persona dueña de la Specification.

Cada rol aporta su experiencia para construir un entendimiento compartido.

Cuando esto ocurre, el desarrollo deja de depender de conversaciones informales y pasa a estar guiado por conocimiento versionado, revisable y reutilizable.

---

# Próximo capítulo

```text
docs/module-03-specification-workflow/

└── 05-development-workflow.md
```

En el siguiente capítulo construiremos el **workflow completo de desarrollo**, desde que una Specification es aprobada hasta que el código llega a producción. Será el primer capítulo donde integraremos de forma detallada **Azure DevOps + GitHub + GitHub Copilot + Claude Code + OpenSpec**, definiendo un proceso que podrías aplicar casi directamente en tu empresa.
