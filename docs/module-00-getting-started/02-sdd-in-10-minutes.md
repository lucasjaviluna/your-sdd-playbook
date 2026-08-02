# SDD en 10 minutos

## ¿Qué es Specification-Driven Development?

Specification-Driven Development (SDD) es un enfoque de desarrollo donde la especificación de una funcionalidad se convierte en el elemento central del ciclo de vida del software.

En lugar de comenzar directamente con la implementación, primero se define claramente:

* qué problema se quiere resolver;
* qué comportamiento debe tener el sistema;
* qué restricciones existen;
* cómo será la solución;
* cómo se comprobará que funciona correctamente.

El código deja de ser el punto inicial y pasa a ser la implementación de una especificación previamente definida.

---

# El cambio de paradigma

El desarrollo tradicional suele seguir este flujo:

```text
User Story
    │
    ▼
Análisis
    │
    ▼
Código
    │
    ▼
Pruebas
    │
    ▼
Entrega
```

En este modelo gran parte del conocimiento queda en la experiencia del equipo y en conversaciones.

SDD propone:

```text
User Story
    │
    ▼
Specification
    │
    ├── Contexto
    ├── Requirements
    ├── Design
    ├── Tasks
    ├── ADR
    └── Test Plan
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

La diferencia principal es que existe una etapa explícita donde el equipo entiende y documenta el problema antes de construir la solución.

---

# ¿Por qué surge SDD?

Durante años los equipos han tenido problemas recurrentes:

## Falta de contexto

Un desarrollador recibe una tarea como:

> "Agregar una nueva opción en el perfil del usuario"

Pero necesita descubrir:

* ¿qué usuarios?
* ¿qué reglas aplican?
* ¿qué sistemas intervienen?
* ¿qué impacto tiene?
* ¿qué restricciones existen?

La información está repartida en diferentes lugares.

---

## Documentación desactualizada

Muchas organizaciones tienen documentación que queda abandonada porque está separada del código.

Ejemplo:

```
Código actual
      │
      ├── cambios realizados
      │
      └── documentación antigua
```

En SDD, la especificación vive junto al código y evoluciona con él.

---

## Desarrollo asistido por IA

La llegada de agentes como Claude Code cambia la forma de desarrollar software.

Una IA puede escribir código rápidamente, pero necesita comprender correctamente el problema.

Una buena Specification proporciona:

* contexto;
* restricciones;
* decisiones;
* criterios de aceptación;
* estrategia de pruebas.

La calidad del resultado depende directamente de la calidad del contexto entregado.

---

# Los elementos básicos de SDD

Una Specification normalmente contiene:

## Context

Explica el problema.

Responde:

> ¿Por qué estamos construyendo esto?

Ejemplo:

"Los clientes actualmente deben contactar al soporte para actualizar su dirección. Queremos permitir que puedan hacerlo desde el portal."

---

## Requirements

Define qué debe hacer el sistema.

Ejemplo:

* El usuario autenticado puede modificar su dirección.
* La dirección debe validarse antes de guardarse.
* El cambio debe quedar registrado.

---

## Design

Describe cómo será la solución.

Ejemplo:

* Nuevo endpoint REST.
* Nuevo componente frontend.
* Validaciones compartidas.
* Actualización de estado.

---

## Tasks

Divide el trabajo.

Ejemplo:

```
TASK-001 Crear endpoint actualizar dirección

TASK-002 Crear formulario frontend

TASK-003 Agregar validaciones

TASK-004 Crear pruebas
```

---

## Test Plan

Define cómo verificar el resultado.

Ejemplo:

* Usuario puede actualizar dirección válida.
* Usuario recibe error con dirección incorrecta.
* Usuario no autenticado no puede acceder.

---

## ADR

Documenta decisiones importantes.

Ejemplo:

"Se utilizará un servicio compartido de validación porque la regla de negocio debe mantenerse igual en frontend y backend."

---

# SDD y herramientas actuales

SDD no reemplaza las herramientas existentes.

Se integra con ellas.

## Azure DevOps

Continúa siendo responsable de:

* Backlog.
* User Stories.
* Bugs.
* Sprint Planning.
* Seguimiento.

---

## GitHub

Gestiona:

* Código.
* Branches.
* Pull Requests.
* Versionado de Specifications.

---

## Claude Code

Utiliza las Specifications como contexto para:

* analizar cambios;
* generar código;
* proponer soluciones;
* ejecutar tareas.

---

## GitHub Copilot

Ayuda durante la implementación:

* completando código;
* generando pruebas;
* explicando código existente;
* refactorizando.

---

# El nuevo rol del desarrollador

Con SDD el desarrollador no solamente escribe código.

Su responsabilidad aumenta.

Debe ser capaz de:

* entender problemas de negocio;
* diseñar soluciones;
* cuestionar requerimientos ambiguos;
* guiar herramientas de IA;
* validar resultados generados.

La IA aumenta la capacidad del desarrollador, pero no reemplaza el pensamiento crítico.

---

# Regla principal de SDD

Una buena regla para recordar:

> Primero entender.
> Después especificar.
> Luego diseñar.
> Finalmente implementar.

La velocidad de la IA hace tentador comenzar directamente escribiendo código, pero SDD busca evitar que la velocidad genere errores más rápidamente.

---

# Resumen rápido

SDD consiste en:

1. Tomar una necesidad de negocio.
2. Transformarla en una Specification.
3. Diseñar la solución.
4. Dividir el trabajo.
5. Implementar utilizando la Specification como guía.
6. Validar mediante pruebas.
7. Mantener la Specification actualizada.

El resultado es un proceso más predecible, trazable y preparado para equipos que trabajan con Inteligencia Artificial.

---

# Próximo capítulo

En el siguiente capítulo veremos la estructura del repositorio SDD y cómo organizar Specifications, ADRs, prompts y documentación para que puedan ser utilizadas tanto por personas como por agentes de IA.
