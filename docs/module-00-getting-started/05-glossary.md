# Glosario SDD

## Introducción

Specification-Driven Development introduce un conjunto de conceptos que permiten organizar el ciclo de vida del software alrededor de especificaciones.

Este glosario define los términos principales que serán utilizados durante todo el playbook.

El objetivo es establecer un lenguaje común entre:

* Product Owners.
* Arquitectos.
* Desarrolladores.
* QA.
* Agentes de Inteligencia Artificial.

---

# SDD (Specification-Driven Development)

## Definición

Es un enfoque de desarrollo donde la Specification se convierte en la fuente principal de información para construir una funcionalidad.

La implementación, las pruebas y las decisiones técnicas se derivan de esa Specification.

## Idea principal

```text
Specification
      │
      ▼
Design
      │
      ▼
Code
      │
      ▼
Tests
```

---

# Specification

## Definición

Una Specification es un conjunto estructurado de documentos que describe una funcionalidad o cambio del sistema.

Incluye:

* contexto;
* objetivos;
* requerimientos;
* diseño;
* tareas;
* pruebas;
* decisiones.

## Propósito

Eliminar ambigüedad antes de implementar.

---

# Spec

Abreviatura utilizada para referirse a una Specification.

Ejemplo:

```text
specs/

└── update-address/
```

Una Spec representa una capacidad concreta del sistema.

---

# Context

## Definición

Describe el problema que se intenta resolver.

Responde:

> ¿Por qué estamos haciendo este cambio?

Ejemplo:

"Los clientes necesitan llamar al soporte para modificar su dirección."

El contexto evita implementar soluciones correctas para problemas equivocados.

---

# Requirement

## Definición

Un Requirement describe un comportamiento esperado del sistema.

Responde:

> ¿Qué debe hacer el sistema?

Ejemplo:

"El usuario autenticado puede actualizar su dirección."

---

# Functional Requirement

Describe una acción que el sistema debe realizar.

Ejemplos:

* Crear un usuario.
* Procesar un pago.
* Actualizar una dirección.

---

# Non-Functional Requirement

Describe atributos de calidad o restricciones.

Ejemplos:

* Tiempo de respuesta menor a 2 segundos.
* Disponibilidad del 99.9%.
* Cumplimiento de seguridad.

---

# Acceptance Criteria

## Definición

Condiciones que determinan cuándo una funcionalidad está correctamente implementada.

Ejemplo:

```text
Given a valid user

When the user updates the address

Then the address is stored successfully.
```

Los criterios de aceptación conectan negocio, desarrollo y pruebas.

---

# Design

## Definición

Describe la solución técnica que implementará los Requirements.

Puede incluir:

* arquitectura;
* componentes;
* APIs;
* modelos;
* diagramas;
* integraciones.

El Design explica el "cómo".

---

# Architecture Decision Record (ADR)

## Definición

Documento que registra decisiones importantes de arquitectura.

Formato típico:

```text
Context

Decision

Alternatives

Consequences
```

Ejemplo:

"Se utilizará Redis como cache porque necesitamos reducir latencia."

---

# Task

## Definición

Unidad de trabajo necesaria para implementar una Specification.

Ejemplo:

```text
TASK-001

Create customer address endpoint.
```

Una Task debe ser:

* concreta;
* ejecutable;
* verificable.

---

# Test Plan

## Definición

Documento que describe cómo validar una Specification.

Incluye:

* escenarios;
* casos positivos;
* casos negativos;
* pruebas automatizadas.

---

# Traceability

## Definición

Capacidad de relacionar todos los elementos del ciclo de desarrollo.

Ejemplo:

```text
User Story

    ↓

Specification

    ↓

Requirement

    ↓

Task

    ↓

Code

    ↓

Test

    ↓

Release
```

La trazabilidad permite saber por qué existe cada cambio.

---

# Agent

## Definición

Un agente de IA es un sistema capaz de ejecutar tareas utilizando modelos de inteligencia artificial y herramientas externas.

Ejemplos:

* Claude Code.
* Agentes personalizados.
* Sistemas internos basados en LLM.

Un agente puede:

* analizar código;
* modificar archivos;
* ejecutar comandos;
* crear pruebas.

---

# Prompt

## Definición

Una instrucción entregada a un modelo de IA.

Un buen prompt define:

* objetivo;
* contexto;
* restricciones;
* resultado esperado.

Ejemplo:

```text
Implement TASK-002.

Read:
- spec.md
- design.md

Rules:
- Follow existing architecture.
- Add tests.
```

---

# Context Engineering

## Definición

Disciplina enfocada en proporcionar el contexto correcto a una IA para obtener mejores resultados.

Incluye:

* seleccionar información relevante;
* estructurar instrucciones;
* limitar ambigüedad.

En SDD, las Specifications son una forma avanzada de Context Engineering.

---

# Human-in-the-Middle (HITM)

## Definición

Modelo donde la IA participa activamente, pero una persona mantiene la supervisión y toma las decisiones finales.

El flujo es:

```text
Humano

  │

  ▼

Specification

  │

  ▼

IA

  │

  ▼

Resultado

  │

  ▼

Validación humana
```

La IA acelera el trabajo, pero la responsabilidad continúa siendo humana.

---

# AI Governance

## Definición

Conjunto de reglas y controles para utilizar Inteligencia Artificial dentro de una organización.

Incluye:

* qué herramientas están permitidas;
* qué datos pueden utilizarse;
* cómo revisar resultados;
* quién es responsable.

---

# Source of Truth

## Definición

Elemento considerado como referencia oficial.

En SDD:

```text
Specification = Source of Truth
```

El código implementa esa fuente.

---

# Drift

## Definición

Situación donde la documentación y el sistema real evolucionan de manera diferente.

Ejemplo:

```text
Specification:

Endpoint GET /customers


Código:

Endpoint GET /clients
```

SDD busca reducir este problema.

---

# Pull Request Review

## Definición

Proceso de revisión donde se valida:

* código;
* pruebas;
* arquitectura;
* Specification.

En SDD la pregunta no es solamente:

> "¿El código funciona?"

También:

> "¿El código implementa correctamente la Specification?"

---

# Release Pack

## Definición

Conjunto de artefactos asociados a una entrega.

Puede incluir:

* Specifications;
* ADRs;
* cambios principales;
* riesgos;
* evidencias de pruebas.

---

# Resumen

Los conceptos fundamentales de SDD giran alrededor de una idea:

> El software debe construirse a partir de conocimiento estructurado, no solamente a partir de código.

Specification, Requirements, Design, Tasks y Tests forman una cadena de conocimiento que puede ser utilizada tanto por personas como por agentes de Inteligencia Artificial.

Dominar este lenguaje es el primer paso para aplicar SDD correctamente en equipos reales.

---

# Próximo capítulo

El siguiente archivo será:

```text
06-cheat-sheet.md
```

Será una referencia rápida con:

* flujo SDD completo;
* estructura de una Spec;
* checklist antes de desarrollar;
* checklist antes de aprobar un Pull Request;
* reglas para trabajar con IA.
