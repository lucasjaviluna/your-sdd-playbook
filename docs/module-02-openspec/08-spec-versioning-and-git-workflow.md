# Versionamiento de Specifications y Git Workflow

## Introducción

Una de las premisas fundamentales de Specification-Driven Development es:

> La Specification debe evolucionar al mismo ritmo que el software.

Si el código cambia y la Specification no cambia, perdemos la fuente de verdad.

Ese problema se conoce como:

```text id="drift01"
Specification Drift
```

Es decir:

```text id="drift02"
Specification

      ❌

Código actual
```

---

# La Specification como código

En SDD, una Specification debe tratarse como un artefacto versionado.

Tiene:

* historial;
* autores;
* revisiones;
* cambios;
* trazabilidad.

Exactamente igual que el código.

---

# Ubicación recomendada

Una práctica común es almacenar Specifications dentro del repositorio.

Ejemplo:

```text id="repo01"
customer-portal/

├── src/

├── tests/

├── infrastructure/

└── specs/

    ├── authentication/

    ├── customer-benefits/

    └── invoices/
```

---

Ventajas:

* mismo ciclo de vida que el código;
* revisión mediante Pull Request;
* historial Git;
* contexto disponible para IA.

---

# Alternativas de organización

Existen diferentes modelos.

---

# Modelo 1 - Specifications dentro del repositorio

Ejemplo:

```text id="model01"
repository/

├── src

└── specs
```

Ventajas:

* máxima trazabilidad;
* fácil acceso para agentes IA;
* relación directa con código.

Desventaja:

* puede crecer mucho en repositorios grandes.

---

# Modelo 2 - Repositorio separado

Ejemplo:

```text id="model02"
company-specifications/

├── customer-domain

├── payments-domain

└── identity-domain
```

Ventajas:

* repositorio central;
* gobierno corporativo.

Desventaja:

* más difícil mantener sincronización.

---

# Modelo recomendado para equipos de producto

Para la mayoría de equipos:

```text id="recommended01"
Application Repository


├── Code

├── Tests

└── Specifications
```

La Specification viaja con el cambio.

---

# Cambios sincronizados

Una regla importante:

Cuando cambia el comportamiento:

```text id="sync01"
Código cambia

        ↓

Specification revisada
```

---

Ejemplo:

Antes:

```markdown
Customer can see benefits.
```

Después:

```markdown
Customer can filter benefits
by category.
```

Debe existir:

```text id="sync02"
Code Change

+

Specification Change
```

---

# Pull Request basado en Specification

Una Pull Request debería incluir:

```text id="pr01"
PR

├── Source Code Changes

├── Tests

└── Specification Update
```

---

Ejemplo:

```text id="pr02"
PR #542

Feature:

Customer Benefits Filter


Modified:

src/features/benefits

specs/customer-benefits
```

---

# Code Review evolucionado

Tradicionalmente revisamos:

* calidad del código;
* tests;
* estándares.

Con SDD agregamos:

## Specification Review

Preguntas:

* ¿El cambio representa correctamente la necesidad?
* ¿Los requisitos están completos?
* ¿El diseño sigue vigente?

---

# Branching Strategy

La Specification debe acompañar la rama de desarrollo.

Ejemplo:

```text id="branch01"
feature/customer-benefits-filter

        |

        ├── src/

        ├── tests/

        └── specs/customer-benefits/
```

---

Cuando la rama se mergea:

```text id="merge01"
main

├── Código actualizado

└── Specification actualizada
```

---

# Commits recomendados

Los commits deberían reflejar cambios relacionados.

Ejemplo:

```bash
git commit -m "feat(benefits): add filtering specification"

git commit -m "feat(benefits): implement category filter"
```

---

O en un único cambio:

```bash
git commit -m "feat(benefits): add category filtering"
```

incluyendo:

* código;
* tests;
* specification.

---

# Versionamiento semántico de Specifications

No siempre es necesario, pero puede ser útil.

Ejemplo:

```text id="specversion01"
Customer Benefits Specification

v1.0

Initial capability


v1.1

Added filtering


v2.0

New benefits model
```

---

Regla:

## Minor change

Agrega capacidad compatible.

Ejemplo:

```text
Agregar filtro.
```

---

## Major change

Cambia comportamiento existente.

Ejemplo:

```text
Nueva lógica de beneficios.
```

---

# Tags de Git y Specifications

En productos críticos:

```bash
git tag release-2.5.0
```

representa:

```text id="tag01"
Código

+

Specifications

+

Tests
```

---

Esto permite responder:

> ¿Cuál era el comportamiento esperado en esta versión?

---

# Specification History

Git permite recuperar decisiones.

Ejemplo:

```bash
git log specs/customer-benefits/spec.md
```

Podemos conocer:

* quién cambió;
* cuándo;
* por qué.

---

# Integración con Azure DevOps

En un entorno empresarial como el tuyo:

Modelo recomendado:

```text id="azure01"
Azure DevOps

Epic

 |

Feature

 |

User Story


        ↓


OpenSpec

Specification


        ↓


Git Repository

Code + Specs


        ↓


Pull Request

Review
```

---

# Work Items y Specifications

Una User Story debería referenciar su Specification.

Ejemplo:

Azure DevOps:

```text
US-4521

Customer downloads invoice
```

Referencia:

```text
/specs/invoice-download/
```

---

# Automatización en CI/CD

Los pipelines pueden validar:

## Existencia de Specification

Ejemplo:

```text id="pipeline01"
Feature detected

        ↓

Check specs folder

        ↓

Specification exists?
```

---

## Validación de formato

Ejemplo:

```text id="pipeline02"
Validate:

- Required sections
- Metadata
- Links
```

---

## Calidad documental

Ejemplo:

Verificar:

* requirements tienen tests;
* tasks están completas.

---

# OpenSpec como artefacto de auditoría

En industrias reguladas esto agrega valor.

Permite responder:

¿Qué cambió?

```text
Specification diff
```

¿Por qué cambió?

```text
Requirement history
```

¿Cómo se validó?

```text
Test evidence
```

---

# Errores comunes

## Crear Specification en una wiki aislada

Problema:

Código cambia.

Wiki queda vieja.

---

## Actualizar Specification después del desarrollo

Problema:

Se convierte en documentación histórica.

---

## No revisar Specifications en PR

Problema:

Pierde calidad progresivamente.

---

# Flujo recomendado

```text id="flowfinal01"
Developer receives User Story

          ↓

Creates / updates Specification

          ↓

Review with team

          ↓

Implement

          ↓

Update tests

          ↓

PR Review

          ↓

Merge Code + Specification
```

---

# Resumen

Versionar Specifications permite:

* evitar Specification Drift;
* mantener conocimiento histórico;
* mejorar revisiones;
* dar contexto persistente a IA.

La regla principal:

> Un cambio de software incompleto es aquel donde cambia el código pero no cambia el conocimiento.

---

# Próximo capítulo

El siguiente archivo será:

```text id="next08"
docs/module-02-openspec/

└── 09-openspec-with-azure-devops.md
```

donde aterrizaremos OpenSpec específicamente a tu contexto actual: Azure DevOps como gestor de trabajo, GitHub como repositorio y Copilot/Claude Code como asistentes de desarrollo.
