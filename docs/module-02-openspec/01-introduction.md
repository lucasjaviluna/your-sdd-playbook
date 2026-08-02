# Módulo 2 – OpenSpec

# 1. Introducción a OpenSpec

## Objetivos

Al finalizar este capítulo podrás:

* Comprender qué es OpenSpec.
* Entender por qué fue creado.
* Diferenciar OpenSpec de una wiki o un gestor de tareas.
* Comprender el rol que cumple dentro de Specification-Driven Development.
* Conocer cómo OpenSpec se integra con herramientas como Azure DevOps, GitHub, Claude Code y GitHub Copilot.

---

# ¿Qué es OpenSpec?

OpenSpec es una forma de organizar y mantener especificaciones técnicas como artefactos versionados dentro del repositorio del proyecto.

En lugar de almacenar el conocimiento únicamente en herramientas externas, las especificaciones viven junto al código y evolucionan con él.

Esto permite que desarrolladores, arquitectos, testers y agentes de Inteligencia Artificial trabajen siempre sobre la misma fuente de información.

---

# ¿Qué problema resuelve?

En muchos equipos la información se encuentra distribuida en diferentes lugares:

* Azure DevOps contiene las User Stories.
* Confluence almacena documentación funcional.
* Diagramas en herramientas externas.
* Pull Requests con decisiones técnicas.
* Comentarios en chats o reuniones.

El conocimiento termina fragmentado.

Como consecuencia:

* es difícil encontrar información;
* aparecen inconsistencias;
* la documentación queda desactualizada;
* la IA dispone de poco contexto para generar código de calidad.

OpenSpec propone centralizar toda la información técnica necesaria para desarrollar una funcionalidad.

---

# OpenSpec no reemplaza Azure DevOps

Una duda frecuente es pensar que OpenSpec sustituye al gestor de trabajo del equipo.

No es así.

Cada herramienta cumple un propósito diferente.

| Herramienta    | Responsabilidad                                            |
| -------------- | ---------------------------------------------------------- |
| Azure DevOps   | Gestión del trabajo, backlog, sprints, User Stories y Bugs |
| OpenSpec       | Especificación técnica y documentación viva                |
| GitHub         | Versionado del código y de las especificaciones            |
| Claude Code    | Implementación guiada por la Specification                 |
| GitHub Copilot | Asistencia durante el desarrollo                           |

---

# OpenSpec como fuente de contexto para la IA

Los agentes de IA generan mejores resultados cuando conocen:

* el problema de negocio;
* las restricciones;
* la arquitectura existente;
* los contratos entre componentes;
* los criterios de aceptación;
* las decisiones técnicas.

OpenSpec reúne toda esta información en una estructura consistente.

En lugar de enviar un prompt extenso cada vez que se solicita una implementación, el agente puede consultar directamente la Specification correspondiente.

---

# Principios de OpenSpec

Una Specification debe cumplir los siguientes principios:

## Versionable

Forma parte del repositorio Git.

Cada cambio queda registrado.

---

## Revisable

Las modificaciones pasan por Pull Requests igual que el código.

---

## Trazable

Cada Specification puede relacionarse con:

* User Stories;
* Bugs;
* Features;
* ADRs;
* Pull Requests;
* Releases.

---

## Evolutiva

La documentación evoluciona junto con el software.

Nunca debería quedar desactualizada.

---

## Consumible por IA

La estructura debe ser clara y consistente para facilitar el trabajo de herramientas como Claude Code y GitHub Copilot.

---

# El flujo de trabajo

```text
Azure DevOps
      │
      ▼
User Story
      │
      ▼
OpenSpec
      │
 ├── Context
 ├── Requirements
 ├── Design
 ├── Tasks
 ├── ADR
 └── Test Plan
      │
      ▼
Claude Code
      │
      ▼
GitHub Copilot
      │
      ▼
Código
      │
      ▼
Tests
      │
      ▼
Pull Request
```

---

# ¿Por qué es importante en la era de la IA?

Antes, la documentación era consumida principalmente por personas.

Hoy también debe ser consumida por agentes inteligentes.

Una Specification bien estructurada reduce la ambigüedad, mejora la calidad del código generado y permite automatizar una parte importante del ciclo de desarrollo sin perder control sobre el resultado.

---

# Resumen

OpenSpec no es simplemente una colección de documentos.

Es una manera de convertir las especificaciones en artefactos versionados, revisables y preparados para ser utilizados tanto por desarrolladores como por herramientas de Inteligencia Artificial.

En el próximo capítulo construiremos la estructura completa de un proyecto OpenSpec y analizaremos el propósito de cada carpeta y archivo.
