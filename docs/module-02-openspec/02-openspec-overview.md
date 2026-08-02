# OpenSpec Overview

## Introducción

En el módulo anterior aprendimos que Specification-Driven Development propone colocar la Specification como elemento central del ciclo de desarrollo.

Ahora surge una pregunta:

> ¿Cómo creamos, organizamos y mantenemos esas Specifications en un entorno real?

OpenSpec es una forma estructurada de aplicar los principios de SDD mediante convenciones, artefactos y un flujo de trabajo definido.

Su objetivo es transformar una idea o necesidad de negocio en un conjunto de documentos que puedan ser utilizados por:

* personas;
* equipos;
* herramientas;
* agentes de Inteligencia Artificial.

---

# ¿Qué es OpenSpec?

OpenSpec puede entenderse como un marco de trabajo para definir Specifications de software.

No es solamente un formato de documentación.

Es un modelo operativo que define:

* qué información debe capturarse;
* cómo organizarla;
* cómo evolucionarla;
* cómo relacionarla con implementación y validación.

---

# OpenSpec dentro del ecosistema SDD

La relación es:

```text
Specification-Driven Development

                |

                ▼

             OpenSpec

                |

                ▼

     Estructura y proceso concreto

                |

                ▼

      Desarrollo del software
```

SDD es el enfoque.

OpenSpec es una manera de aplicarlo.

---

# El problema que OpenSpec intenta resolver

En muchos equipos existe documentación, pero no existe una estructura consistente.

Ejemplo:

Proyecto A:

```text
docs/

feature.md
notes.md
architecture.txt
```

Proyecto B:

```text
documentation/

requirements/
design/
decisions/
```

Proyecto C:

```text
wiki/

varios documentos sin relación
```

El problema no es la falta de información.

Es la falta de un modelo común.

---

# OpenSpec como contrato de conocimiento

Una Specification debe permitir que diferentes participantes entiendan el mismo cambio.

Participantes:

## Product Owner

Necesita entender:

* objetivo;
* alcance;
* valor de negocio.

---

## Arquitectos

Necesitan entender:

* restricciones;
* impacto;
* decisiones técnicas.

---

## Developers

Necesitan entender:

* comportamiento esperado;
* tareas;
* componentes involucrados.

---

## QA

Necesita entender:

* escenarios;
* criterios de aceptación.

---

## Agentes IA

Necesitan:

* contexto;
* reglas;
* estructura;
* restricciones.

---

# La unidad principal: Specification

En OpenSpec, la unidad central es una Specification.

Ejemplo:

```text
specs/

└── customer-benefits/

    ├── spec.md
    ├── requirements.md
    ├── design.md
    ├── tasks.md
    └── test-plan.md
```

Cada Specification representa una capacidad concreta del sistema.

---

# Características de una buena Specification

Una Specification debe ser:

## Clara

Debe poder ser entendida por personas que no participaron en la conversación original.

---

## Completa

Debe contener la información necesaria para implementar.

---

## Verificable

Debe permitir crear pruebas.

---

## Evolutiva

Debe cambiar junto con el sistema.

---

## Consumible por IA

Debe poder utilizarse como contexto para agentes.

---

# OpenSpec versus documentación tradicional

Existe una diferencia importante.

## Documentación tradicional

Normalmente responde:

> ¿Cómo funciona el sistema actualmente?

Ejemplo:

```text
CustomerService tiene estos métodos.
```

---

## Specification

Responde:

> ¿Qué comportamiento debe tener el sistema?

Ejemplo:

```text
Cuando un cliente actualiza su dirección,
el sistema debe validar los campos requeridos
y registrar la modificación.
```

---

# OpenSpec y el ciclo de desarrollo

Un flujo basado en OpenSpec:

```text
Business Idea

      ↓

User Story

      ↓

OpenSpec

      ↓

Requirements

      ↓

Design

      ↓

Tasks

      ↓

Implementation

      ↓

Tests

      ↓

Release
```

La Specification acompaña todo el ciclo.

---

# OpenSpec como memoria del sistema

En equipos grandes existe un problema:

Los equipos cambian.

Las personas cambian.

Los proyectos evolucionan.

OpenSpec ayuda a conservar conocimiento.

Ejemplo:

Un nuevo desarrollador llega al equipo.

Sin Specification:

```text
Pregunta:

¿Por qué esto funciona así?
```

Respuesta:

> "Porque alguien lo hizo hace dos años."

---

Con Specification:

```text
Decision:

Se utiliza este patrón
por estas restricciones.
```

---

# OpenSpec y Git

Una característica fundamental es que las Specifications deben vivir cerca del código.

Ejemplo:

```text
repository/

├── src/

├── tests/

└── specs/

    └── customer-benefits/

        ├── spec.md
        ├── requirements.md
        └── design.md
```

Esto permite:

* versionamiento;
* revisión por Pull Request;
* historial;
* trazabilidad.

---

# OpenSpec y Azure DevOps

OpenSpec no reemplaza Azure DevOps.

Cada herramienta tiene una responsabilidad diferente.

Modelo recomendado:

```text
Azure DevOps

Gestiona:

- Epic
- Feature
- User Story
- Sprint
- Estado


        +


OpenSpec

Gestiona:

- Contexto
- Requerimientos
- Diseño
- Decisiones
- Validación
```

---

# OpenSpec y agentes IA

Los agentes necesitan contexto estructurado.

Una Specification funciona como un paquete de contexto.

Ejemplo:

```text
Implement feature customer-benefits.

Read:

/specs/customer-benefits/

Understand:

- requirements.md
- design.md
- test-plan.md

Follow:

existing architecture patterns.
```

---

# Error común: usar OpenSpec como documentación final

OpenSpec no debe crearse después del desarrollo.

Incorrecto:

```text
Código

    ↓

Documentación
```

Correcto:

```text
Necesidad

    ↓

OpenSpec

    ↓

Código
```

---

# Principio clave

OpenSpec cambia la pregunta:

Antes:

> "¿Qué código tengo que escribir?"

Después:

> "¿Qué conocimiento necesito construir antes de escribir código?"

---

# Resumen

OpenSpec es una forma estructurada de aplicar SDD.

Su objetivo es:

* capturar intención;
* reducir ambigüedad;
* mantener trazabilidad;
* proporcionar contexto a humanos y agentes IA.

La Specification deja de ser un documento auxiliar y se convierte en un artefacto central del desarrollo.

---

# Próximo capítulo

El siguiente archivo será:

```text
module-02-openspec/

└── 03-specification-structure.md
```

donde definiremos la estructura interna de una Specification OpenSpec y el propósito de cada artefacto.
