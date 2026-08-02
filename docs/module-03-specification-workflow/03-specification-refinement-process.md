# Proceso de refinamiento de Specifications

## Introducción

En metodologías tradicionales, gran parte de la discusión ocurre durante:

* Sprint Planning;
* desarrollo;
* code review;
* testing.

SDD propone mover las conversaciones importantes hacia una etapa anterior:

```text id="refinement01"
Antes de escribir código
```

El objetivo es reducir incertidumbre.

---

# ¿Qué es el refinamiento de una Specification?

El refinamiento es una actividad colaborativa donde el equipo revisa:

* contexto de negocio;
* requisitos;
* reglas;
* diseño;
* riesgos;
* validaciones.

No es una reunión para asignar tareas.

Es una reunión para construir entendimiento compartido.

---

# Estado inicial de una Specification

Una Specification normalmente comienza incompleta.

Ejemplo:

```markdown id="initialspec01"
# Invoice Download


Goal:

Allow customers to download invoices.
```

Todavía faltan respuestas:

* ¿Qué clientes?
* ¿Qué facturas?
* ¿Qué permisos?
* ¿Qué formato?
* ¿Qué errores?

---

El refinamiento transforma esto:

```text id="uncertain01"
Idea

"Descargar facturas"
```

en:

```text id="clear01"
Capability

Authenticated customers
can download PDF invoices
from the last 5 years.
```

---

# Participantes del refinamiento

No todos tienen el mismo rol.

---

# Product Owner

Responsabilidad:

Definir intención de negocio.

Preguntas:

* ¿Qué problema resolvemos?
* ¿Cuál es el valor?
* ¿Quién utiliza esta funcionalidad?

---

# Developer

Responsabilidad:

Aportar viabilidad técnica.

Preguntas:

* ¿Existe infraestructura?
* ¿Qué componentes reutilizamos?
* ¿Qué impacto tiene?

---

# QA

Responsabilidad:

Definir validabilidad.

Preguntas:

* ¿Cómo sabemos que funciona?
* ¿Qué casos negativos existen?
* ¿Qué escenarios debemos probar?

---

# Arquitecto

Responsabilidad:

Cuidar evolución del sistema.

Preguntas:

* ¿Afecta arquitectura?
* ¿Existen decisiones previas?
* ¿Necesitamos ADR?

---

# El rol de IA en refinamiento

La IA no debería reemplazar la conversación.

Puede ayudar como asistente.

Ejemplos:

## Analizar Specification

```text id="ai_review01"
Review this specification.

Identify:

- missing requirements
- ambiguous statements
- possible edge cases
```

---

## Generar preguntas

```text id="ai_questions01"
Analyze invoice-download specification.

Generate questions
that developers and QA should clarify.
```

---

# Agenda recomendada de refinamiento

Una sesión efectiva:

```text id="agenda01"
1. Contexto de negocio

2. Alcance

3. Requirements

4. Rules

5. Design impact

6. Testing strategy

7. Open questions

8. Approval
```

---

# Paso 1 - Revisar contexto

Pregunta principal:

> ¿Todos entendemos por qué existe esta funcionalidad?

Ejemplo:

Incorrecto:

```text id="badcontext01"
Need invoice download.
```

---

Correcto:

```text id="goodcontext01"
Customers currently request
historical invoices through support.

Goal:

Enable self-service access.
```

---

# Paso 2 - Revisar alcance

El equipo debe acordar límites.

Ejemplo:

Incluye:

```text id="scopeinclude01"
✓ Download PDF invoice

✓ View invoice history
```

---

No incluye:

```text id="scopeexclude01"
✗ Invoice correction

✗ Payment processing
```

---

# Paso 3 - Revisar Requirements

Cada Requirement debe ser:

* claro;
* verificable;
* completo.

---

Ejemplo incorrecto:

```text id="badreq01"
System should be user friendly.
```

Problema:

No puede probarse.

---

Ejemplo correcto:

```text id="goodreq01"
Given:

Authenticated customer.


When:

Customer opens invoices page.


Then:

Available invoices are displayed.
```

---

# Paso 4 - Identificar reglas de negocio

Muchas veces las reglas están implícitas.

El refinamiento debe descubrirlas.

Ejemplo:

Pregunta:

> ¿Puede un cliente descargar cualquier factura?

Respuesta:

No.

Regla:

```text id="businessrule01"
Customer can only access
own invoices.
```

---

# Paso 5 - Revisar impacto técnico

No se diseña toda la solución.

Se valida dirección.

Preguntas:

* ¿Existe un servicio?
* ¿Debemos crear una API?
* ¿Hay componentes reutilizables?
* ¿Existe deuda técnica?

---

Ejemplo:

```text id="techimpact01"
Existing:

InvoiceService


New:

Download capability
```

---

# Paso 6 - Definir estrategia de pruebas

QA debe participar temprano.

Ejemplo:

Requirements:

```text id="testingreq01"
Customer downloads invoice.
```

Casos:

```text id="testingcases01"
✓ Download successful

✓ Invoice not found

✓ Unauthorized access

✓ API unavailable
```

---

# Paso 7 - Resolver preguntas abiertas

Una Specification madura no tiene preguntas críticas pendientes.

Ejemplo:

Antes:

```text id="questions02"
How many invoices?
```

---

Después:

```text id="answers01"
Maximum:

Last 5 years.
```

---

# Definition of Ready para Specification

Antes de desarrollo:

```text id="dor01"
Specification Ready
```

Debe cumplir:

## Negocio

✅ Objetivo claro.

---

## Alcance

✅ Incluido y excluido definido.

---

## Requirements

✅ Verificables.

---

## Design

✅ Dirección técnica conocida.

---

## Testing

✅ Estrategia definida.

---

## Questions

✅ Sin bloqueantes.

---

# Ejemplo de flujo completo

```text id="fullflow03"
Azure DevOps User Story

        ↓

Create Specification

        ↓

Refinement Meeting

        ↓

Requirements Updated

        ↓

Design Validated

        ↓

Tasks Created

        ↓

Development Starts
```

---

# Refinamiento continuo

Una Specification no queda congelada.

Puede evolucionar.

Ejemplo:

Semana 1:

```text id="week01"
Customer downloads invoice.
```

---

Semana 2:

```text id="week02"
Added invoice sharing capability.
```

---

El cambio debe quedar registrado.

---

# Errores comunes

## Refinar demasiado tarde

Problema:

Las dudas aparecen cuando ya existe código.

---

## Solo participa desarrollo

Problema:

Se pierde contexto de negocio.

---

## Crear Specifications perfectas antes de empezar

Problema:

Genera burocracia.

---

El objetivo es:

```text id="balance01"
Suficiente claridad

+

Flexibilidad para evolucionar
```

---

# Aplicación en tu contexto

Con Azure DevOps:

```text id="companyflow01"
Product creates User Story

        ↓

Engineering creates OpenSpec

        ↓

Refinement session

        ↓

Approved Specification

        ↓

GitHub development

        ↓

Copilot / Claude Code execution
```

---

# Resumen

El refinamiento convierte una Specification inicial en un contrato compartido.

La idea central:

> El equipo no empieza programando. El equipo empieza entendiendo.

---

# Próximo capítulo

```text id="m3file04"

docs/module-03-specification-workflow/

└── 04-roles-and-responsibilities.md
```

En el siguiente capítulo definiremos claramente quién es responsable de cada parte del proceso SDD: Product Owner, Developers, QA, Arquitectura, DevOps y agentes IA.
