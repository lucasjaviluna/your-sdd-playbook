# SDD y desarrollo asistido por Inteligencia Artificial

## Introducción

La llegada de herramientas como GitHub Copilot, Claude Code y agentes basados en modelos de lenguaje está cambiando la forma en que se desarrolla software.

La capacidad de generar código dejó de ser el principal limitante.

Hoy el desafío principal es:

> Proporcionar el contexto correcto para que la IA pueda producir soluciones alineadas con el sistema.

Specification-Driven Development encaja naturalmente con este nuevo escenario porque transforma conocimiento implícito en información estructurada que puede ser utilizada tanto por humanos como por agentes.

---

# La evolución del desarrollo con IA

Podemos observar tres etapas:

## Etapa 1 - Desarrollo tradicional

```text
Requirement

    ↓

Developer piensa la solución

    ↓

Código
```

El conocimiento estaba principalmente en la experiencia del desarrollador.

---

## Etapa 2 - Asistencia con IA

```text
Developer

    ↓

Prompt

    ↓

IA genera código
```

La IA acelera tareas, pero depende fuertemente del contexto entregado.

---

## Etapa 3 - Desarrollo basado en Specification

```text
Business Need

      ↓

Specification

      ↓

AI Agent

      ↓

Implementation

      ↓

Validation
```

La Specification se convierte en la memoria estructurada del cambio.

---

# El problema del prompt aislado

Un error común al utilizar IA es pensar:

> "Mientras mejor sea el prompt, mejor será el resultado."

El prompt es importante, pero no es suficiente.

Ejemplo:

```text
Implementa una pantalla de beneficios.
```

La IA no conoce:

* arquitectura;
* componentes existentes;
* reglas de negocio;
* decisiones anteriores;
* restricciones técnicas.

Puede generar código válido, pero incorrecto para el sistema.

---

# Contexto antes que prompt

En SDD cambiamos la prioridad:

Modelo tradicional:

```text
Prompt
  +
IA
  =
Resultado
```

Modelo SDD:

```text
Specification
      +
Context
      +
Prompt
      +
IA
      =
Resultado
```

La calidad del resultado depende principalmente de la calidad del contexto.

---

# Specification como contexto para agentes

Una Specification contiene información que una IA necesita:

## Contexto del problema

Ejemplo:

```markdown
Los clientes necesitan consultar sus beneficios
porque actualmente deben comunicarse con soporte.
```

Permite entender la intención.

---

## Requirements

Ejemplo:

```markdown
El usuario debe estar autenticado.

Los beneficios expirados no deben mostrarse.
```

Permite conocer reglas.

---

## Design

Ejemplo:

```markdown
Utilizar BenefitsService.

Mantener el patrón existente de state management.
```

Permite respetar arquitectura.

---

## Tests

Ejemplo:

```markdown
Validar estado vacío.

Validar error de API.
```

Permite conocer comportamiento esperado.

---

# Claude Code dentro de un flujo SDD

Claude Code puede trabajar como un agente que recibe una Specification.

Ejemplo:

```text
Implement TASK-003.

Context:

Read:

/specs/customer-benefits/

Files:

- spec.md
- requirements.md
- design.md
- test-plan.md


Constraints:

- Follow existing Angular architecture.
- Use Signals.
- Add Jest tests.
```

El agente no comienza desde cero.

Trabaja dentro de un marco definido.

---

# GitHub Copilot dentro de un flujo SDD

GitHub Copilot funciona especialmente bien cuando el proyecto tiene:

* buena estructura;
* nombres claros;
* patrones consistentes;
* tests existentes;
* documentación contextual.

Ejemplo:

Un desarrollador abre un componente:

```typescript
export class BenefitsComponent {

}
```

Copilot puede sugerir código.

Pero si además existe:

```text
specs/customer-benefits/

requirements.md

design.md
```

el desarrollador puede dirigir mejor la implementación.

---

# Prompt Engineering vs Context Engineering

Estos conceptos suelen confundirse.

## Prompt Engineering

Se enfoca en:

> Cómo pedir algo a una IA.

Ejemplo:

```text
Genera una función que valide emails.
```

---

## Context Engineering

Se enfoca en:

> Qué información necesita la IA para tomar buenas decisiones.

Incluye:

* arquitectura;
* restricciones;
* documentación;
* ejemplos;
* decisiones previas.

SDD es principalmente una práctica de Context Engineering.

---

# Human-in-the-Middle

Aunque usemos agentes avanzados, SDD mantiene una regla fundamental:

La IA propone e implementa.

El humano decide.

Flujo:

```text
Specification

      ↓

AI Agent

      ↓

Código generado

      ↓

Human Review

      ↓

Merge
```

---

# El rol del desarrollador cambia

Con IA, el desarrollador deja de ser solamente un generador de código.

Sus responsabilidades evolucionan hacia:

## Analizar

Entender problemas complejos.

---

## Diseñar

Definir soluciones.

---

## Guiar IA

Proporcionar contexto correcto.

---

## Validar

Revisar resultados.

---

# Nuevos tipos de errores con IA

La IA introduce nuevos riesgos.

## Código correcto pero incorrecto para el negocio

Ejemplo:

La IA crea un formulario perfecto.

Pero permite modificar datos que deberían estar bloqueados.

---

## Código correcto pero incompatible con arquitectura

Ejemplo:

El agente crea un nuevo patrón cuando el proyecto usa otro.

---

## Código correcto pero sin contexto

Ejemplo:

Funciona hoy, pero ignora decisiones existentes.

---

SDD ayuda a reducir estos problemas.

---

# Arquitectura de trabajo recomendada

Un flujo profesional:

```text
                Azure DevOps

                     |

                     ▼

                User Story

                     |

                     ▼

              OpenSpec

                     |

                     ▼

        Requirements + Design

                     |

                     ▼

          Claude Code / Copilot

                     |

                     ▼

              Pull Request

                     |

                     ▼

            Human Approval
```

---

# Reglas para usar IA con SDD

## Regla 1

No pedir implementación sin contexto.

---

## Regla 2

La Specification debe preceder al código.

---

## Regla 3

La IA no decide arquitectura sin supervisión.

---

## Regla 4

Todo cambio importante debe actualizar la Specification.

---

## Regla 5

El resultado generado debe ser validado mediante pruebas.

---

# Beneficios de combinar SDD + IA

## Mayor velocidad

La IA reduce trabajo repetitivo.

---

## Mayor consistencia

La Specification define patrones.

---

## Mejor onboarding

El conocimiento queda disponible.

---

## Mejor escalabilidad

Los agentes pueden trabajar sobre contexto compartido.

---

# Resumen

La Inteligencia Artificial no elimina la necesidad de ingeniería de software.

Aumenta la importancia de:

* contexto;
* diseño;
* especificaciones;
* validación.

Specification-Driven Development proporciona la estructura necesaria para que humanos y agentes trabajen sobre la misma comprensión del sistema.

La idea central es:

> La IA puede generar código rápidamente. SDD asegura que ese código tenga sentido dentro del sistema.

---

# Próximo capítulo

El siguiente archivo será:

```text
docs/module-01-fundamentals/
└── 08-sdd-principles.md
```

donde formalizaremos los principios que guían todo el enfoque SDD y que luego utilizaremos para diseñar procesos, gobernanza y automatización.
