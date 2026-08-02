# Release y Operación

## Introducción

En un proceso tradicional, el ciclo de desarrollo suele terminar cuando el código llega a producción.

```text
Development

↓

Testing

↓

Release

↓

Done
```

Sin embargo, el software continúa evolucionando.

Aparecen:

* incidentes;
* mejoras;
* nuevas regulaciones;
* cambios de negocio;
* deuda técnica.

Por eso, en Specification-Driven Development el Release no representa el final del ciclo.

Representa el comienzo de una nueva etapa.

---

# El ciclo de vida real

Una capacidad del sistema evoluciona constantemente.

```text
Idea

↓

Specification

↓

Implementation

↓

Validation

↓

Release

↓

Operation

↓

Feedback

↓

Evolution

↓

Specification Update
```

La Specification permanece durante todo el ciclo.

---

# La Specification como memoria

Supongamos que seis meses después aparece un incidente.

```
Los clientes no pueden descargar facturas antiguas.
```

En un proceso tradicional el equipo debe investigar:

* ¿Quién desarrolló esto?
* ¿Qué debía hacer?
* ¿Por qué funciona así?

Con SDD podemos comenzar por la Specification.

```
specs/

invoice-download/
```

Allí encontramos:

* contexto;
* Requirements;
* reglas;
* decisiones;
* restricciones;
* historial.

La investigación comienza con conocimiento, no con suposiciones.

---

# El Release no congela la Specification

Una mala práctica es considerar la Specification como documentación histórica.

```
Feature terminada

↓

Nunca más se modifica
```

En SDD ocurre lo contrario.

```
Feature en producción

↓

La Specification continúa evolucionando
```

Cuando cambia el comportamiento esperado, la Specification también cambia.

---

# Feedback desde producción

La operación genera información valiosa.

Ejemplos:

* métricas de uso;
* errores frecuentes;
* consultas al soporte;
* comentarios de clientes;
* problemas de rendimiento.

Todo este conocimiento puede traducirse en nuevas Requirements.

Ejemplo:

```
Se detecta que muchos clientes descargan varias facturas consecutivas.
```

Nueva necesidad:

```
Permitir descarga múltiple.
```

La evolución comienza actualizando la Specification.

---

# Gestión de incidentes

Supongamos un incidente:

```
INC-1023

Invoice Download returns HTTP 500.
```

El flujo recomendado es:

```text
Incident

↓

Identify affected Specification

↓

Review Requirements

↓

Analyze implementation

↓

Implement fix

↓

Update tests

↓

Update Specification (si cambia el comportamiento)
```

No todos los incidentes modifican la Specification.

Solo aquellos que cambian el comportamiento esperado.

---

# Cambios de negocio

Un Product Owner decide:

```
Ahora los clientes pueden descargar facturas de los últimos diez años.
```

No debemos comenzar modificando el código.

El flujo correcto es:

```text
Business Decision

↓

Specification Update

↓

Requirements Update

↓

Implementation

↓

Validation

↓

Release
```

La Specification vuelve a ser la fuente de verdad.

---

# Cambios técnicos

También existen cambios puramente técnicos.

Ejemplo:

```
Migrar Angular 20 → Angular 21.
```

Si el comportamiento funcional no cambia:

* la Specification funcional probablemente permanezca igual;
* el Design puede actualizarse;
* puede crearse un ADR para registrar la decisión técnica.

No todo cambio requiere modificar Requirements.

---

# Observabilidad

La operación moderna produce métricas.

Ejemplos:

* tiempo de respuesta;
* tasa de errores;
* uso de funcionalidades;
* disponibilidad.

Estas métricas ayudan a responder preguntas como:

```
¿La solución cumple realmente el objetivo del negocio?
```

La observabilidad complementa la Specification.

---

# Caso de estudio

Feature:

```
Invoice Download
```

Después del Release se observa:

* el 80% de las descargas provienen de dispositivos móviles;
* el tiempo medio de descarga supera los cinco segundos.

El equipo decide:

* optimizar la generación del PDF;
* mejorar la experiencia móvil.

Antes de implementar estos cambios:

1. Se actualiza la Specification.
2. Se crean nuevos Requirements.
3. Se planifican nuevas Tasks.

La evolución queda documentada.

---

# Versionado

Una Specification debe evolucionar junto al código.

Ejemplo:

```text
v1.0

Descarga individual.

↓

v1.1

Nuevos mensajes de error.

↓

v1.2

Descarga múltiple.

↓

v2.0

Nuevo servicio de documentos.
```

Cada versión representa un cambio explícito del conocimiento del sistema.

---

# Operación asistida por IA

Los agentes IA también pueden ayudar durante la operación.

Ejemplos:

* analizar incidentes;
* comparar código con la Specification;
* identificar Requirements afectados;
* proponer escenarios de regresión;
* generar borradores de actualización de la Specification.

Ejemplo de contexto:

```text
Read:

specs/invoice-download/

Analyze:

Incident INC-1023

Identify:

- impacted requirements
- possible root causes
- missing test scenarios

Do not modify code.
```

La IA acelera el análisis, pero la decisión continúa siendo humana.

---

# Integración con Azure DevOps

Un flujo completo podría ser:

```text
Incident

↓

Azure DevOps Bug

↓

Related User Story

↓

Related Specification

↓

Implementation

↓

Pull Request

↓

Release
```

La trazabilidad permanece incluso durante el mantenimiento.

---

# Integración con GitHub

Una corrección importante debería incluir:

* cambios en el código;
* pruebas adicionales;
* actualización de la Specification (si aplica).

Así evitamos que el conocimiento y la implementación diverjan.

---

# Checklist antes de cerrar un cambio

Antes de marcar una funcionalidad como completada verifica:

□ La Specification refleja el comportamiento actual.

□ Los Requirements siguen siendo válidos.

□ Las pruebas cubren el cambio realizado.

□ La documentación técnica está actualizada.

□ La trazabilidad con Azure DevOps permanece.

□ La Pull Request referencia las Tasks correspondientes.

---

# Errores comunes

## Considerar la Specification como documentación inicial

Consecuencia:

Queda obsoleta rápidamente.

---

## Corregir incidentes sin revisar Requirements

Consecuencia:

El código puede alejarse del comportamiento esperado.

---

## Modificar el comportamiento directamente en el código

Consecuencia:

La Specification deja de ser la fuente de verdad.

---

# Buenas prácticas

* Toda evolución funcional comienza en la Specification.
* Los cambios técnicos relevantes se documentan mediante ADRs cuando corresponda.
* Los incidentes importantes generan aprendizaje y fortalecen la Specification.
* La operación alimenta continuamente el refinamiento del producto.

---

# Resumen

En SDD el Release no marca el final de una funcionalidad.

Marca el inicio de su vida operativa.

La Specification acompaña a esa funcionalidad desde la primera idea hasta su retiro del sistema.

El conocimiento evoluciona junto con el software.

Ese es el verdadero valor de trabajar con Specifications versionadas.

---

# Cierre del módulo

Con este módulo aprendiste a:

* transformar una idea en una Specification;
* refinarla colaborativamente;
* definir responsabilidades;
* integrar Azure DevOps, GitHub y agentes IA;
* revisar código y Specifications;
* diseñar la estrategia de validación;
* mantener la Specification durante la operación.

Ya no vemos la Specification como un documento.

La entendemos como el artefacto central del ciclo de vida del software.

---

# Próximo capítulo

```text
docs/module-03-specification-workflow/

└── 09-exercises.md
```

En el siguiente capítulo pondremos en práctica todo el workflow mediante un caso de estudio completo: desde una User Story en Azure DevOps hasta una funcionalidad desplegada, incluyendo OpenSpec, Pull Requests, prompts para agentes IA y validación de extremo a extremo.
