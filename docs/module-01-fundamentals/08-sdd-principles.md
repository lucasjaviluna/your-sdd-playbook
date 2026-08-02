# Principios fundamentales de Specification-Driven Development

## Introducción

Specification-Driven Development no es solamente una estructura de archivos o una herramienta.

Es un modelo de trabajo basado en una serie de principios que cambian la forma en que los equipos entienden, diseñan y construyen software.

Estos principios definen cómo:

* capturamos conocimiento;
* tomamos decisiones;
* colaboramos;
* usamos Inteligencia Artificial;
* mantenemos sistemas a largo plazo.

---

# Principio 1 - Specification First

## La Specification precede a la implementación

El primer principio establece:

> Antes de escribir código debemos entender y documentar qué estamos construyendo.

Flujo incorrecto:

```text id="7y7g5d"
Idea

   ↓

Código

   ↓

Intentar explicar lo realizado
```

Problema:

La documentación se convierte en una descripción posterior y puede no representar la intención original.

---

Flujo SDD:

```text id="7pv3lo"
Idea

   ↓

Specification

   ↓

Design

   ↓

Code

   ↓

Tests
```

La implementación nace desde una comprensión compartida.

---

# Principio 2 - Context First

## El contexto es más importante que la instrucción

Una instrucción sin contexto genera resultados impredecibles.

Ejemplo:

```text id="plf1ol"
Crear componente de beneficios.
```

Falta información:

* arquitectura;
* reglas;
* usuarios;
* restricciones.

---

Un enfoque basado en contexto:

```text id="4y3w0q"
Context:

Los clientes necesitan consultar beneficios.

Requirements:

- Usuario autenticado.
- Mostrar beneficios activos.

Design:

- Utilizar BenefitsService.
- Mantener patrón existente.

Task:

Crear componente.
```

La calidad del resultado aumenta porque la intención está clara.

---

# Principio 3 - Single Source of Truth

## Debe existir una referencia oficial del conocimiento

En SDD:

```text id="3c8n2w"
Specification = Source of Truth
```

Esto significa:

* las reglas viven allí;
* las decisiones importantes quedan registradas;
* el equipo consulta la misma fuente.

Evita:

* información perdida;
* interpretaciones diferentes;
* dependencia de personas.

---

# Principio 4 - Traceability

## Todo cambio debe poder rastrearse

Un cambio de software debería responder:

¿Por qué existe?

¿Qué requisito cubre?

¿Cómo fue implementado?

¿Cómo fue validado?

Ejemplo:

```text id="2mt2cg"
Business Need

      ↓

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

La trazabilidad conecta negocio y tecnología.

---

# Principio 5 - Human-in-the-Middle

## La IA ayuda, pero la responsabilidad permanece en humanos

SDD no propone reemplazar ingenieros.

Propone aumentar sus capacidades.

Modelo:

```text id="70e5dg"
Human

  ↓

Specification

  ↓

AI Agent

  ↓

Implementation

  ↓

Human Review
```

El humano sigue siendo responsable de:

* decisiones;
* arquitectura;
* calidad;
* seguridad.

---

# Principio 6 - Design Before Implementation

## Las decisiones importantes deben ocurrir antes del código

Un error frecuente es descubrir la arquitectura mientras se programa.

Ejemplo:

```text id="0o6sdc"
Comenzar frontend

      ↓

Descubrir necesidad backend

      ↓

Cambiar diseño

      ↓

Retrabajo
```

SDD propone:

```text id="19ckmz"
Requirement

      ↓

Design

      ↓

Implementation
```

---

# Principio 7 - Evolution Over Documentation

## La Specification debe evolucionar con el sistema

Una Specification no es documentación histórica.

Debe cambiar cuando cambia el sistema.

Incorrecto:

```text id="x3v6yq"
Specification

(vieja)

        +

Código

(nuevo)
```

Correcto:

```text id="1xv1ji"
Specification

        +

Código

        +

Tests
```

Todos evolucionan juntos.

---

# Principio 8 - Small and Focused Specifications

## Una Specification debe representar una capacidad concreta

Un error común es crear Specifications demasiado grandes.

Ejemplo incorrecto:

```text id="v8j1a9"
Customer Platform
```

Demasiado amplio.

---

Ejemplo correcto:

```text id="g4i3lq"
Customer Benefits Feature
```

Una Specification debe ser:

* entendible;
* implementable;
* verificable.

---

# Principio 9 - Verification Driven

## Todo Requirement debe poder validarse

Un requisito que no puede probarse es ambiguo.

Ejemplo débil:

```text id="5az7t8"
La pantalla debe ser rápida.
```

---

Ejemplo verificable:

```text id="h0z8pl"
The page must load within 2 seconds
under normal conditions.
```

La Specification debe permitir validar el resultado.

---

# Principio 10 - AI Ready by Design

## El software debe construirse pensando también en agentes

En el futuro, humanos y agentes trabajarán sobre los mismos sistemas.

Por eso debemos crear artefactos que sean:

* claros;
* estructurados;
* versionados;
* consultables.

Una Specification bien diseñada es:

* documentación;
* contrato;
* contexto para IA.

---

# Relación entre principios

Los principios se conectan:

```text id="az3p8k"
Specification First

        +

Context First

        +

Traceability

        +

Human Approval

        +

Continuous Evolution


        =


SDD
```

---

# Cómo aplicar estos principios en el día a día

Antes de desarrollar una funcionalidad:

Preguntar:

## ¿Tenemos una Specification?

Si no:

Crear contexto.

---

## ¿Sabemos por qué hacemos este cambio?

Si no:

Revisar objetivo.

---

## ¿Está definido cómo validaremos?

Si no:

Crear Test Plan.

---

## ¿La IA tiene suficiente contexto?

Si no:

Mejorar Specification.

---

## ¿La implementación refleja la intención?

Si no:

Actualizar diseño o código.

---

# SDD como cambio cultural

El mayor cambio no es técnico.

Es cultural.

Antes:

> "Empieza a programar y resolvemos dudas después."

Después:

> "Construyamos entendimiento antes de acelerar la implementación."

---

# Resumen

Los principios fundamentales de SDD son:

1. Specification First.
2. Context First.
3. Single Source of Truth.
4. Traceability.
5. Human-in-the-Middle.
6. Design Before Implementation.
7. Evolution Over Documentation.
8. Small and Focused Specifications.
9. Verification Driven.
10. AI Ready by Design.

Estos principios forman la base para construir equipos capaces de trabajar con software complejo y con inteligencia artificial de manera controlada.

---

# Próximo capítulo

El siguiente archivo será:

```text id="n4z9v2"
docs/module-01-fundamentals/
└── 09-exercises.md
```

donde aplicaremos estos conceptos con ejercicios prácticos transformando User Stories reales en Specifications.
