# Problemas del desarrollo tradicional que SDD intenta resolver

## Introducción

Specification-Driven Development no aparece porque los enfoques anteriores sean incorrectos.

Metodologías como Waterfall, Agile, Scrum y DevOps han aportado mejoras importantes a la industria del software.

El problema es que, incluso en equipos maduros, continúan existiendo desafíos relacionados con:

* comprensión del problema;
* comunicación;
* documentación;
* toma de decisiones;
* transferencia de conocimiento.

SDD surge como una evolución para resolver estos problemas mediante un elemento central: una Specification compartida y versionada.

---

# Evolución de los enfoques de desarrollo

## Waterfall

Los modelos tradicionales intentaban reducir la incertidumbre mediante planificación exhaustiva al inicio.

Flujo:

```text
Requirements
      |
      ▼
Design
      |
      ▼
Development
      |
      ▼
Testing
      |
      ▼
Release
```

Ventajas:

* mucha documentación inicial;
* planificación detallada;
* trazabilidad formal.

Problemas:

* dificultad para adaptarse a cambios;
* feedback demasiado tardío;
* alto costo de modificar decisiones iniciales.

---

# Agile

Agile cambió el enfoque:

```text
Plan
 |
 ▼
Develop
 |
 ▼
Review
 |
 ▼
Improve
```

Sus principios ayudaron a:

* entregar valor más rápido;
* obtener feedback frecuente;
* trabajar colaborativamente.

Sin embargo, en muchos equipos apareció un nuevo problema:

> La velocidad de entrega aumentó, pero la claridad del conocimiento no siempre aumentó al mismo ritmo.

---

# El problema de las User Stories

Las User Stories son excelentes herramientas de comunicación de negocio.

Ejemplo:

```text
Como cliente

quiero actualizar mi dirección

para recibir correctamente mis pedidos.
```

Pero una User Story normalmente no responde todas las preguntas necesarias para implementar.

Faltan detalles como:

## Reglas de negocio

* ¿Qué campos son obligatorios?
* ¿Qué formatos son válidos?
* ¿Existen restricciones?

---

## Arquitectura

* ¿Qué servicios participan?
* ¿Qué componentes se modifican?
* ¿Qué sistemas externos intervienen?

---

## Seguridad

* ¿Qué permisos necesita?
* ¿Existe auditoría?
* ¿Cómo protegemos la información?

---

## Testing

* ¿Qué escenarios deben validarse?
* ¿Qué comportamiento es esperado?

---

La User Story expresa intención.

La Specification expresa conocimiento.

---

# El problema de la interpretación

Cuando una historia no tiene suficiente contexto, cada persona completa los espacios vacíos con sus propios supuestos.

Ejemplo:

## Product Owner

Piensa:

> "El cliente podrá cambiar sus datos fácilmente."

---

## Frontend Developer

Interpreta:

> "Necesitamos un formulario editable."

---

## Backend Developer

Interpreta:

> "Necesitamos un nuevo endpoint."

---

## QA

Pregunta:

> "¿Qué pasa si el dato es inválido?"

---

Todos están trabajando sobre la misma historia, pero con modelos mentales diferentes.

---

# El problema del conocimiento tribal

Muchas organizaciones tienen conocimiento crítico almacenado en personas.

Ejemplo:

> "Ese servicio no se puede llamar directamente porque tiene un límite de concurrencia."

Pero esa información puede estar:

* en un chat antiguo;
* en una conversación;
* en la memoria de un desarrollador senior.

El problema aparece cuando esa persona:

* cambia de equipo;
* deja la organización;
* no está disponible.

El conocimiento desaparece.

---

# El problema de la documentación desconectada

Un patrón común:

```text
Código

   │

   │

Documentación
```

Ambos evolucionan por caminos diferentes.

Ejemplo:

Documento:

```text
Customer API

POST /customer/address
```

Código actual:

```text
PUT /customers/{id}/address
```

La documentación deja de ser confiable.

---

# El problema del contexto perdido

Durante un proyecto existen muchas decisiones.

Ejemplo:

¿Por qué elegimos una determinada librería?

¿Por qué una API tiene esa estructura?

¿Por qué una validación está en frontend y backend?

Si esas decisiones no quedan registradas, los equipos futuros deben redescubrirlas.

---

# El problema del desarrollo asistido por IA

La llegada de herramientas como:

* GitHub Copilot;
* Claude Code;
* agentes personalizados;

hizo más evidente este problema.

Un desarrollador humano puede compensar falta de documentación con experiencia previa.

Un agente de IA necesita contexto explícito.

Ejemplo:

Solicitud:

```text
Implementa la gestión de clientes.
```

Para una IA faltan:

* arquitectura;
* restricciones;
* patrones existentes;
* reglas de negocio;
* decisiones previas.

El resultado puede ser técnicamente correcto pero arquitectónicamente incorrecto.

---

# El nuevo cuello de botella

Antes:

```text
Problema principal:

Escribir código rápido
```

Ahora:

```text
Problema principal:

Proporcionar contexto correcto
```

La generación de código es cada vez más rápida.

La comprensión del problema se vuelve el factor limitante.

---

# El concepto de "Context Debt"

Así como existe deuda técnica, existe deuda de contexto.

## Deuda técnica

Código difícil de mantener.

---

## Deuda de contexto

Información necesaria para tomar decisiones que no está disponible.

Ejemplos:

* reglas no documentadas;
* decisiones sin registrar;
* arquitectura implícita;
* conocimiento en personas.

La deuda de contexto aumenta el costo de cualquier cambio.

---

# Cómo SDD aborda estos problemas

SDD introduce una capa explícita de conocimiento:

```text
Business Need

      |

      ▼

Specification

      |

      ▼

Design

      |

      ▼

Implementation

      |

      ▼

Tests
```

La Specification permite:

* alinear personas;
* reducir supuestos;
* preservar conocimiento;
* entregar contexto a la IA.

---

# Comparación rápida

| Problema              | Sin SDD                   | Con SDD                  |
| --------------------- | ------------------------- | ------------------------ |
| User Stories ambiguas | Interpretación individual | Specification compartida |
| Decisiones técnicas   | Implícitas                | ADRs                     |
| Conocimiento tribal   | Dependencia de personas   | Documentación versionada |
| IA sin contexto       | Resultados inconsistentes | Contexto estructurado    |
| Documentación vieja   | Separada del código       | Evoluciona con el cambio |

---

# Idea principal

El problema que SDD intenta resolver no es escribir código.

El problema es transformar conocimiento humano en una forma:

* clara;
* reutilizable;
* verificable;
* consumible por personas y máquinas.

---

# Resumen

Los enfoques modernos de desarrollo han mejorado la velocidad de entrega, pero todavía enfrentan desafíos relacionados con contexto y conocimiento.

SDD propone una evolución:

Antes de implementar una solución, construir una comprensión compartida mediante una Specification.

Esa Specification reduce ambigüedad, conserva conocimiento y permite aprovechar mejor las capacidades de la Inteligencia Artificial.

---

# Próximo capítulo

El siguiente archivo será:

```text
05-specification-as-source-of-truth.md
```

En ese capítulo profundizaremos en uno de los conceptos más importantes de SDD:

**La Specification como fuente de verdad del sistema.**
