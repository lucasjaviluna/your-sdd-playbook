# Módulo 3 - Specification Workflow

## Introducción

Specification-Driven Development no es solamente una forma de escribir documentos.

Es una forma diferente de organizar el ciclo de vida del desarrollo de software.

El objetivo principal es que todas las personas involucradas compartan el mismo modelo mental antes de comenzar la implementación.

---

# El problema que intenta resolver SDD

En muchos equipos el flujo tradicional es:

```text
Idea

 ↓

User Story

 ↓

Sprint Planning

 ↓

Developer interpreta

 ↓

Código

 ↓

Testing

 ↓

Release
```

Aunque este modelo funciona, presenta algunos problemas:

* diferentes interpretaciones de una misma historia;
* decisiones técnicas tomadas durante la implementación;
* falta de contexto para nuevos integrantes;
* dificultad para utilizar IA eficientemente;
* conocimiento perdido después del desarrollo.

---

# El cambio de paradigma

SDD introduce una etapa explícita:

```text
Idea

 ↓

Specification

 ↓

Implementation

 ↓

Validation
```

La Specification se convierte en el punto donde el equipo alinea:

* negocio;
* producto;
* arquitectura;
* desarrollo;
* QA;
* operaciones.

---

# Specification como contrato del equipo

Una Specification representa un acuerdo.

Antes del código, el equipo define:

## Qué problema resolvemos

Ejemplo:

```text
Los clientes necesitan consultar sus facturas
sin contactar al soporte.
```

---

## Qué comportamiento esperamos

Ejemplo:

```text
El cliente autenticado puede descargar
sus facturas disponibles.
```

---

## Qué solución proponemos

Ejemplo:

```text
Nuevo módulo de facturas integrado
con Invoice API.
```

---

## Cómo validamos

Ejemplo:

```text
Pruebas funcionales y automatizadas.
```

---

# Nuevo ciclo de desarrollo

El ciclo tradicional:

```text
Requirement

 ↓

Code

 ↓

Test
```

---

Con SDD:

```text
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

Code

 ↓

Tests

 ↓

Release
```

---

# SDD dentro de un equipo Agile

SDD no reemplaza Agile.

Lo complementa.

Un equipo puede continuar utilizando:

* Scrum;
* Kanban;
* Azure DevOps;
* Jira;
* GitHub Projects.

La diferencia está en agregar una capa de conocimiento estructurado.

---

Ejemplo:

## Antes

Azure DevOps:

```text
User Story

Como usuario quiero descargar mi factura.
```

Developer:

"Voy a revisar cómo hacerlo."

---

## Después

Azure DevOps:

```text
User Story

Como usuario quiero descargar mi factura.
```

↓

OpenSpec:

```text
Invoice Download Specification

- Requirements
- Design
- Tasks
- Validation
```

↓

Developer:

Implementa una solución conocida.

---

# Beneficios del workflow SDD

## 1. Menos incertidumbre

Las preguntas aparecen antes del código.

Ejemplo:

Antes:

"¿Qué hacemos si la factura no existe?"

Durante desarrollo.

---

Después:

Definido en Requirement:

```text
When invoice does not exist:

Show empty state.
```

---

## 2. Mejor colaboración

Producto, arquitectura y desarrollo trabajan sobre el mismo artefacto.

---

## 3. Mejor uso de IA

Un agente IA necesita contexto.

Comparación:

Sin SDD:

```text
Create invoice component.
```

Con SDD:

```text
Implement TASK-003.

Read:

/specs/invoice-download/

Requirements:

R001-R005

Design:

Angular + NgRx pattern

Validation:

Jest tests
```

---

## 4. Mayor mantenibilidad

La Specification explica por qué existe el código.

El código explica cómo funciona.

---

# Principio fundamental

SDD separa tres preguntas:

## ¿Por qué?

Business Context

---

## ¿Qué?

Requirements

---

## ¿Cómo?

Design e Implementation

---

Muchos problemas de software aparecen porque estas preguntas se mezclan.

---

# Workflow general del módulo

Durante este módulo construiremos este flujo:

```text
1. Idea nace

        ↓

2. Product crea User Story

        ↓

3. Equipo crea Specification

        ↓

4. Refinamiento colaborativo

        ↓

5. Aprobación

        ↓

6. Desarrollo

        ↓

7. Validación

        ↓

8. Release

        ↓

9. Evolución
```

---

# Aplicación en tu contexto

Considerando un entorno con:

* Azure DevOps;
* GitHub;
* GitHub Copilot;
* Claude Code;
* equipos frontend/backend;

un workflow recomendado será:

```text
Azure DevOps

Gestiona intención y prioridad


        ↓


OpenSpec

Gestiona conocimiento


        ↓


GitHub

Gestiona implementación


        ↓


IA Agents

Aceleran ejecución


        ↓


CI/CD

Entrega software
```

---

# Objetivos del módulo

Al finalizar este módulo deberías poder:

✅ Diseñar un flujo SDD dentro de una empresa.
✅ Definir cuándo crear una Specification.
✅ Saber quién participa en cada etapa.
✅ Integrar desarrollo humano + agentes IA.
✅ Mantener trazabilidad desde negocio hasta código.

---

# Próximo capítulo

El siguiente archivo será:

```text
docs/module-03-specification-workflow/

└── 02-from-idea-to-specification.md
```

En ese capítulo veremos el primer paso práctico:

> Cómo transformar una idea de negocio o una User Story de Azure DevOps en una Specification lista para refinamiento.
