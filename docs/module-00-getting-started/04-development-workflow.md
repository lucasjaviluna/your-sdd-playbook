# Flujo de desarrollo utilizando SDD

## Introducción

Specification-Driven Development define un cambio fundamental en la forma de construir software:

El desarrollo no comienza con código.

Comienza con comprensión.

Antes de implementar una funcionalidad, el equipo transforma una necesidad de negocio en una Specification completa que será utilizada como guía durante todo el ciclo de desarrollo.

Este capítulo describe el flujo completo:

```text
Azure DevOps
      │
      ▼
Specification
      │
      ▼
Design
      │
      ▼
Implementation
      │
      ▼
Testing
      │
      ▼
Pull Request
      │
      ▼
Production
```

---

# Etapa 1 - Creación de la User Story

El flujo comienza normalmente en Azure DevOps.

Ejemplo:

## User Story

```
Como cliente

quiero actualizar mi dirección

para recibir correctamente mis pedidos.
```

Esta historia representa una necesidad del negocio.

Sin embargo, todavía existen muchas preguntas:

* ¿Qué campos puede modificar?
* ¿Qué validaciones existen?
* ¿Qué sistemas deben actualizarse?
* ¿Se debe guardar historial?
* ¿Qué sucede si falla la actualización?
* ¿Qué permisos son necesarios?

La User Story es el inicio, no la especificación completa.

---

# Etapa 2 - Creación de la Specification

A partir de la User Story se crea una Specification.

Ejemplo:

```text
specs/

└── update-address/

    ├── spec.md
    ├── requirements.md
    ├── design.md
    ├── tasks.md
    └── test-plan.md
```

Aquí comienza el verdadero análisis.

---

# Etapa 3 - Definir el contexto

Primero se documenta el problema.

Ejemplo:

```markdown
## Context

Actualmente los clientes deben contactar
al centro de atención para modificar su dirección.

Esto genera:

- mayor volumen de llamadas;
- demora en actualizaciones;
- mala experiencia del usuario.
```

El objetivo es que cualquier persona o agente de IA comprenda por qué existe la funcionalidad.

---

# Etapa 4 - Definir Requirements

Luego se describen los comportamientos esperados.

Ejemplo:

```markdown
Requirement R001

Given a logged user

When the user updates the address

Then the system stores the new information.
```

Los requisitos deben ser:

* claros;
* verificables;
* independientes de la implementación.

---

# Etapa 5 - Diseño de la solución

Antes de escribir código se define la solución.

Ejemplo:

```text
Frontend

AddressComponent
      |
      |
AddressService


Backend

PUT /customers/{id}/address


Database

CustomerAddress
```

El diseño puede incluir:

* diagramas;
* contratos API;
* modelos;
* decisiones técnicas.

---

# Etapa 6 - Crear Tasks

El diseño se transforma en trabajo ejecutable.

Ejemplo:

```markdown
TASK-001

Crear endpoint actualizar dirección.


TASK-002

Crear formulario frontend.


TASK-003

Implementar validaciones.


TASK-004

Crear pruebas unitarias.
```

Estas tareas pueden sincronizarse con Azure DevOps.

---

# Etapa 7 - Implementación asistida por IA

Aquí entran Claude Code y GitHub Copilot.

La diferencia con un desarrollo tradicional es el contexto entregado.

En lugar de:

```
Implementa actualización de dirección
```

el agente recibe:

```
Implementa TASK-002.

Contexto:

Leer:
- spec.md
- requirements.md
- design.md

Reglas:

- respetar arquitectura existente;
- crear pruebas;
- no modificar archivos fuera del alcance.
```

La IA deja de trabajar por inferencia y trabaja siguiendo una especificación.

---

# Etapa 8 - Testing

Los tests se derivan de los requisitos.

Ejemplo:

Requirement:

```
El usuario puede actualizar una dirección válida.
```

Genera:

```
Test:

Given a valid address

When user submits the form

Then address is updated.
```

Existe una relación directa:

```text
Requirement

      │

      ▼

Test Case

      │

      ▼

Automated Test
```

---

# Etapa 9 - Pull Request

En SDD una Pull Request revisa dos cosas:

## Código

* calidad;
* arquitectura;
* pruebas;
* estándares.

## Specification

* ¿la solución implementada coincide con lo diseñado?
* ¿los requisitos están cubiertos?
* ¿la documentación necesita actualizarse?

La Specification forma parte del cambio.

---

# Etapa 10 - Actualización y mantenimiento

Después del release:

La Specification continúa siendo útil.

Puede utilizarse para:

* mantenimiento;
* nuevas funcionalidades;
* onboarding;
* soporte;
* nuevos agentes de IA.

El conocimiento no desaparece después de cerrar la User Story.

---

# Flujo completo con herramientas

```text
                 Azure DevOps

                      │

                      ▼

                User Story

                      │

                      ▼

                  OpenSpec

        ┌─────────────┼─────────────┐

        ▼             ▼             ▼

 Requirements      Design        Tasks


                      │

                      ▼

              Claude Code / Copilot


                      │

                      ▼

                   Código


                      │

                      ▼

                   Tests


                      │

                      ▼

              GitHub Pull Request


                      │

                      ▼

                Deployment
```

---

# Rol de cada participante

## Product Owner

Responsable de:

* objetivo de negocio;
* alcance;
* criterios de aceptación.

---

## Arquitecto / Tech Lead

Responsable de:

* diseño;
* decisiones técnicas;
* riesgos.

---

## Desarrollador

Responsable de:

* implementar;
* validar;
* mantener calidad.

---

## IA

Responsable de:

* asistir;
* acelerar;
* proponer soluciones.

No reemplaza la responsabilidad técnica del equipo.

---

# Beneficios del flujo SDD

Este flujo permite:

## Menos retrabajo

Los problemas se detectan antes de programar.

---

## Mejor colaboración

Todos trabajan sobre el mismo contexto.

---

## Mejor uso de IA

Los agentes reciben información estructurada.

---

## Mayor trazabilidad

Cada cambio tiene:

* origen;
* decisión;
* implementación;
* validación.

---

# Regla de oro

En SDD:

> Una funcionalidad no está terminada cuando existe código funcionando. Está terminada cuando la Specification, el código y las pruebas representan la misma realidad.

---

# Resumen

El flujo SDD transforma una User Story en un proceso completo:

1. Entender la necesidad.
2. Crear una Specification.
3. Diseñar la solución.
4. Crear tareas.
5. Implementar con ayuda de IA.
6. Validar mediante pruebas.
7. Revisar código y documentación.
8. Mantener el conocimiento actualizado.

Este flujo será la base práctica para todos los módulos siguientes.

---

# Próximo capítulo

En el siguiente capítulo crearemos el **glosario SDD**, definiendo términos como Specification, Requirement, Design, ADR, Task, Agent, Prompt Engineering y Human-in-the-Middle, que serán utilizados durante todo el playbook.
