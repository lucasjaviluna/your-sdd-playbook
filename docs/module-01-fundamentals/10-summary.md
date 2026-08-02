# Resumen - Fundamentos de Specification-Driven Development

## Introducción

Durante este módulo construimos el modelo mental necesario para comprender Specification-Driven Development.

El objetivo no era aprender una herramienta específica, sino entender el cambio de paradigma:

> Pasar de construir software desde conversaciones y supuestos a construir software desde conocimiento estructurado.

---

# El problema que queremos resolver

El desarrollo moderno logró grandes avances:

* metodologías ágiles;
* integración continua;
* DevOps;
* automatización;
* inteligencia artificial.

Sin embargo, muchos equipos todavía enfrentan un problema común:

## Falta de contexto compartido.

Ejemplos:

* historias ambiguas;
* decisiones técnicas no documentadas;
* conocimiento almacenado en personas;
* documentación desactualizada;
* IA trabajando sin suficiente información.

---

# La idea central de SDD

Specification-Driven Development propone:

```text id="5t1b0q"
Intención

    ↓

Specification

    ↓

Diseño

    ↓

Implementación

    ↓

Validación
```

La Specification se convierte en el elemento central que conecta:

* negocio;
* arquitectura;
* desarrollo;
* testing;
* inteligencia artificial.

---

# Conceptos fundamentales aprendidos

## 1. Specification First

Antes de escribir código debemos comprender qué estamos construyendo.

La implementación es consecuencia de una intención previamente definida.

---

## 2. Context First

La calidad del resultado depende de la calidad del contexto.

Esto es especialmente importante al trabajar con IA.

Una buena instrucción sin contexto produce resultados limitados.

---

## 3. Source of Truth

La Specification representa la fuente oficial del comportamiento esperado.

El código implementa esa definición.

---

## 4. Traceability

Cada cambio debe poder seguirse desde su origen:

```text id="0z7hbc"
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
```

---

## 5. Human-in-the-Middle

La IA aumenta la capacidad del equipo, pero no reemplaza la responsabilidad humana.

El humano:

* define intención;
* valida decisiones;
* aprueba cambios.

---

# Diferencia entre User Story y Specification

Una User Story responde:

> ¿Qué necesidad tiene el usuario?

Ejemplo:

```text id="p1q5j7"
Como cliente quiero ver mis beneficios.
```

---

Una Specification responde:

> ¿Qué significa exactamente construir esa capacidad?

Incluye:

* contexto;
* objetivos;
* alcance;
* requisitos;
* reglas;
* diseño;
* validación.

---

# El nuevo rol del desarrollador

En un entorno SDD + IA, el desarrollador evoluciona.

Antes:

```text id="6cv8n4"
Recibir tarea

      ↓

Escribir código
```

Después:

```text id="9v8m6s"
Entender problema

      ↓

Diseñar solución

      ↓

Crear contexto

      ↓

Guiar IA

      ↓

Validar resultado
```

---

# SDD y herramientas actuales

SDD no reemplaza las herramientas existentes.

Se integra con ellas.

Modelo empresarial:

```text id="8w7p1v"
Azure DevOps

- Epics
- Features
- User Stories
- Tracking


        +

OpenSpec

- Specifications
- Requirements
- Design
- Tests


        +

GitHub

- Código
- Versionamiento
- Pull Requests


        +

AI Tools

- GitHub Copilot
- Claude Code
```

---

# Lecciones principales

## Lección 1

El principal cuello de botella del desarrollo moderno no es escribir código.

Es entender correctamente qué debemos construir.

---

## Lección 2

La IA aumenta la importancia del contexto.

Cuanto más poderosa es la herramienta, más importante es darle información correcta.

---

## Lección 3

La documentación tradicional no es suficiente.

Necesitamos artefactos vivos que evolucionen junto con el software.

---

## Lección 4

Una Specification bien diseñada es útil para:

* humanos;
* equipos;
* herramientas;
* agentes IA.

---

# Checklist antes de desarrollar una funcionalidad

Antes de comenzar una implementación deberíamos poder responder:

## Problema

¿Entendemos por qué existe esta funcionalidad?

---

## Alcance

¿Sabemos qué incluye y qué no incluye?

---

## Reglas

¿Conocemos las restricciones del negocio?

---

## Diseño

¿Sabemos cómo encaja en la arquitectura existente?

---

## Validación

¿Sabemos cómo comprobar que funciona?

---

## Contexto IA

¿Un agente podría implementar esta tarea con la información disponible?

---

# Preparación para el siguiente módulo

En este módulo aprendimos el "por qué".

El siguiente módulo responderá:

> ¿Cómo se implementa esto utilizando OpenSpec?

Entraremos en:

* estructura de Specifications;
* convenciones;
* archivos;
* versionamiento;
* ciclo de vida;
* integración con Git;
* flujo de trabajo real.

---

# Estado del aprendizaje

Al finalizar el Módulo 1 deberías poder:

✅ Explicar qué es SDD.
✅ Identificar problemas que resuelve.
✅ Diferenciar User Story de Specification.
✅ Entender la Specification como Source of Truth.
✅ Preparar contexto para IA.
✅ Evaluar si una funcionalidad está lista para implementarse.

---

# Próximo módulo

```text id="x4k7nm"
Módulo 2

OpenSpec

"De conceptos a estructura real"
```

Aquí comenzaremos a construir Specifications reales siguiendo un flujo profesional.
