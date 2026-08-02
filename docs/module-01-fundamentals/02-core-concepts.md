# Módulo 1 – Fundamentos de Specification-Driven Development

# 2. Conceptos fundamentales

## Objetivos

Al finalizar este capítulo podrás:

* Comprender los componentes principales de SDD.
* Entender cómo se relacionan entre sí.
* Identificar el propósito de cada documento dentro de una Specification.
* Reconocer el flujo de información desde el requerimiento hasta el código.

---

# La anatomía de una Specification

En Specification-Driven Development, una funcionalidad no se representa únicamente mediante una User Story.

Se representa mediante un conjunto de documentos relacionados que describen distintos aspectos del problema y de la solución.

Una Specification puede visualizarse de la siguiente manera:

```text
Specification
│
├── Contexto
├── Objetivos
├── Requerimientos
├── Diseño
├── Arquitectura
├── Tareas
├── Plan de pruebas
├── Riesgos
└── Decisiones (ADR)
```

Cada uno de estos elementos cumple una función específica y juntos conforman la fuente de verdad del proyecto.

---

# 1. Contexto

El contexto responde a la pregunta:

**¿Por qué existe esta funcionalidad?**

Describe:

* el problema de negocio;
* quiénes son los usuarios afectados;
* las limitaciones conocidas;
* las dependencias con otros sistemas.

Sin contexto, una IA o un desarrollador pueden implementar correctamente una funcionalidad desde el punto de vista técnico, pero equivocarse respecto al objetivo de negocio.

---

# 2. Objetivos

Los objetivos describen qué se espera lograr.

Ejemplos:

* Reducir el tiempo de carga.
* Permitir la actualización de datos personales.
* Automatizar un proceso manual.
* Mejorar la experiencia del usuario.

Los objetivos deben expresar el resultado esperado, no la implementación.

---

# 3. Requerimientos (Requirements)

Los requerimientos definen el comportamiento esperado del sistema.

Se clasifican normalmente en:

## Funcionales

Describen qué debe hacer el sistema.

Ejemplos:

* Registrar un usuario.
* Validar credenciales.
* Enviar una notificación.

## No funcionales

Describen restricciones o atributos de calidad.

Ejemplos:

* Tiempo máximo de respuesta.
* Seguridad.
* Escalabilidad.
* Accesibilidad.
* Disponibilidad.

---

# 4. Diseño (Design)

El diseño explica cómo se resolverá el problema.

Puede incluir:

* arquitectura;
* componentes;
* APIs;
* modelos de datos;
* diagramas de secuencia;
* decisiones de integración.

El diseño no contiene código, sino la estructura que servirá de guía para implementarlo.

---

# 5. Tareas (Tasks)

Una vez aprobado el diseño, el trabajo se divide en tareas concretas.

Ejemplos:

* Crear endpoint REST.
* Implementar componente Angular.
* Agregar validaciones.
* Actualizar base de datos.
* Escribir pruebas unitarias.

Estas tareas pueden sincronizarse con Azure DevOps o GitHub Projects.

---

# 6. Plan de pruebas (Test Plan)

El Test Plan define cómo se verificará que la implementación cumple con la Specification.

Puede incluir:

* pruebas unitarias;
* pruebas de integración;
* pruebas end-to-end;
* pruebas manuales;
* criterios de aceptación.

En SDD, las pruebas se diseñan antes de escribir el código.

---

# 7. ADR (Architecture Decision Record)

Un ADR registra decisiones importantes de arquitectura.

Por ejemplo:

* ¿Por qué se eligió Angular Signals?
* ¿Por qué se utiliza Redis?
* ¿Por qué se decidió implementar un BFF?
* ¿Por qué se eligió OpenSpec como herramienta de especificación?

El objetivo es conservar el razonamiento detrás de las decisiones, evitando que se pierda con el tiempo.

---

# Relación entre los componentes

Cada elemento depende del anterior.

```text
Contexto
      │
      ▼
Objetivos
      │
      ▼
Requerimientos
      │
      ▼
Diseño
      │
      ▼
Tareas
      │
      ▼
Implementación
      │
      ▼
Pruebas
      │
      ▼
Entrega
```

Este orden evita comenzar la implementación sin comprender completamente el problema.

---

# ¿Qué documentos consume la IA?

Un agente como Claude Code puede utilizar:

* Specification.
* Requirements.
* Design.
* Tasks.
* ADR.
* Test Plan.

Cuanto mayor sea la calidad de estos documentos, más preciso será el código generado.

---

# Diferencia con una User Story

Una User Story responde principalmente a:

> ¿Qué necesita el usuario?

Una Specification responde además a:

* ¿Por qué?
* ¿Qué restricciones existen?
* ¿Qué riesgos hay?
* ¿Cómo se diseñará?
* ¿Cómo se probará?
* ¿Qué decisiones arquitectónicas deben respetarse?

Por eso una Specification ofrece mucho más contexto que una User Story aislada.

---

# Resumen

Una Specification está formada por varios documentos especializados, cada uno con un propósito claro.

Trabajando en conjunto, estos documentos permiten que desarrolladores, arquitectos, testers y agentes de IA compartan una única fuente de verdad, reduciendo ambigüedades y mejorando la calidad del desarrollo.

En el próximo capítulo veremos cómo estos conceptos se integran en un flujo de trabajo completo utilizando Azure DevOps, OpenSpec, GitHub, GitHub Copilot y Claude Code.
