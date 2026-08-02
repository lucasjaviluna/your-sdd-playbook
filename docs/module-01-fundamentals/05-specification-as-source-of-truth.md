# La Specification como Source of Truth

## Introducción

Uno de los cambios más importantes que propone Specification-Driven Development es cambiar dónde vive el conocimiento principal del sistema.

En muchos equipos tradicionales, el código termina siendo la única fuente confiable.

La lógica es:

> "Si quieres saber cómo funciona el sistema, revisa el código."

El problema es que el código explica **qué hace el sistema**, pero no siempre explica:

* por qué existe;
* qué problema resuelve;
* qué alternativas fueron evaluadas;
* qué restricciones de negocio existen;
* qué decisiones llevaron a esa implementación.

SDD propone que la Specification sea la fuente de verdad que conecta intención, diseño e implementación.

---

# ¿Qué significa Source of Truth?

Source of Truth significa:

> El lugar donde existe la información considerada oficial y confiable.

Ejemplos fuera del software:

## Finanzas

Un sistema contable es la fuente de verdad de una transacción.

---

## Identidad

Un sistema IAM es la fuente de verdad de permisos y usuarios.

---

## Software

La Specification es la fuente de verdad del comportamiento esperado del sistema.

---

# El modelo tradicional

En muchos equipos encontramos esta relación:

```text
                 Código

                   ▲

                   |

        Documentación parcial

                   ▲

                   |

            Conversaciones

                   ▲

                   |

              User Story
```

El conocimiento está distribuido.

Cada capa puede tener una interpretación diferente.

---

# El modelo SDD

SDD reorganiza la relación:

```text
             Business Need

                  |

                  ▼

            Specification

                  |

       ┌──────────┼──────────┐

       ▼          ▼          ▼

    Design      Tasks      Tests

                  |

                  ▼

               Código
```

El código deja de ser el origen del conocimiento.

Pasa a ser la implementación de una intención documentada.

---

# Specification versus código

Una pregunta común:

> "¿Entonces el código deja de ser importante?"

No.

El código sigue siendo fundamental.

La diferencia es la relación entre ambos.

Modelo tradicional:

```text
Código
  |
  |
Documentación opcional
```

Modelo SDD:

```text
Specification

      ↓

Código
```

La Specification define lo que debe existir.

El código demuestra cómo fue implementado.

---

# La Specification responde preguntas que el código no responde

## ¿Por qué existe esta funcionalidad?

Ejemplo:

Código:

```typescript
updateAddress(customerId, address)
```

Nos dice qué hace.

Pero no responde:

¿Por qué los clientes necesitan actualizar dirección?

La Specification sí.

---

## ¿Por qué elegimos esta arquitectura?

Código:

```typescript
AddressService
```

No explica:

* qué alternativas fueron consideradas;
* qué restricciones existían.

Un ADR asociado sí lo explica.

---

## ¿Qué comportamiento es esperado?

Código:

```typescript
if(validAddress){
   save();
}
```

Pero:

¿Qué significa una dirección válida?

Eso pertenece al Requirement.

---

# Specification y trazabilidad

Una de las mayores ventajas es poder seguir el camino completo.

Ejemplo:

```text
Azure DevOps

US-1234

     ↓

Specification

update-address

     ↓

Requirement

R001 - User can update address

     ↓

Task

TASK-002 Create form

     ↓

Code

AddressComponent

     ↓

Test

should update address
```

Esto permite responder preguntas importantes:

* ¿Por qué existe este código?
* ¿Qué requisito cubre?
* ¿Qué prueba valida este comportamiento?

---

# El problema del Specification Drift

Uno de los mayores enemigos de SDD es el drift.

Drift significa que la Specification y el sistema evolucionan de manera diferente.

Ejemplo:

Specification:

```text
The customer can update phone number.
```

Código:

```text
Only email can be updated.
```

Existe una contradicción.

---

# Cómo evitar el drift

## Versionamiento

Specification y código deben evolucionar juntos.

Ejemplo:

```text
Pull Request

+
├── source code
├── tests
└── specification update
```

---

## Revisión conjunta

Una Pull Request no debería revisar solamente código.

También debe responder:

* ¿La implementación coincide con la Specification?
* ¿Cambió algún requerimiento?
* ¿La Specification necesita actualización?

---

## Automatización

En equipos maduros se pueden agregar validaciones:

Ejemplo:

```text
PR opened

      ↓

Check

      ↓

Does feature have specification?

      ↓

Yes / No
```

---

# Specification como contrato

Una forma útil de pensar la Specification es como un contrato.

Entre:

* negocio;
* arquitectura;
* desarrollo;
* QA;
* IA.

Ejemplo:

Product Owner dice:

"Necesitamos actualizar dirección."

Specification traduce:

"El sistema debe permitir a usuarios autenticados modificar estos campos bajo estas reglas."

El desarrollador implementa:

"Crearé estos componentes y servicios."

QA valida:

"Probaré estos escenarios."

La IA ejecuta:

"Implementaré siguiendo estas restricciones."

---

# Specification e Inteligencia Artificial

Este concepto es especialmente importante en la era de agentes.

Una IA no tiene:

* conversaciones pasadas;
* conocimiento tribal;
* contexto informal.

Necesita información explícita.

Una Specification funciona como memoria operacional del proyecto.

Ejemplo:

Sin Specification:

```text
Implementa beneficios.
```

Con Specification:

```text
Implementa BENEFITS-001.

Context:
Customers need to view available benefits.

Requirements:
- User must be authenticated.
- Benefits are filtered by customer category.

Design:
- Use BenefitsService.
- Follow existing state management.

Tests:
- Validate loading state.
- Validate empty results.
```

El segundo escenario permite resultados mucho más confiables.

---

# La Specification no es documentación tradicional

Existe una diferencia importante.

Documentación tradicional:

> Describe el sistema.

Specification:

> Define el sistema esperado.

La documentación normalmente explica algo existente.

La Specification guía una evolución.

---

# Regla fundamental

En SDD:

> Si una decisión cambia el comportamiento del sistema, la Specification debe reflejar ese cambio.

---

# Ejemplo completo

Una funcionalidad:

"Permitir cambiar dirección."

Evolución:

```text
Idea de negocio

      ↓

User Story

      ↓

Specification

      ↓

Design

      ↓

Implementation

      ↓

Tests

      ↓

Release
```

La Specification acompaña todo el ciclo.

---

# Resumen

Convertir la Specification en Source of Truth significa:

* centralizar conocimiento;
* reducir ambigüedad;
* mantener trazabilidad;
* facilitar colaboración;
* mejorar el trabajo con IA.

El código sigue siendo importante, pero deja de ser el único lugar donde vive la verdad del sistema.

En SDD:

> El código implementa la intención. La Specification conserva la intención.

---

# Próximo capítulo

El siguiente archivo será:

```text
06-from-user-story-to-specification.md
```

donde veremos el proceso práctico de transformar una User Story de Azure DevOps en una Specification completa utilizando el enfoque OpenSpec.
