# Módulo 1 – Fundamentos de Specification-Driven Development (SDD)

# 1. Introducción a Specification-Driven Development

## Objetivos del capítulo

Al finalizar este capítulo serás capaz de:

* Comprender qué es Specification-Driven Development (SDD).
* Entender por qué surge este enfoque.
* Identificar las limitaciones del desarrollo tradicional basado únicamente en User Stories.
* Comprender el papel que desempeñan las especificaciones como fuente de verdad.
* Entender por qué la IA obtiene mejores resultados cuando trabaja sobre especificaciones completas.

---

# ¿Qué es Specification-Driven Development?

Specification-Driven Development (SDD) es una metodología de desarrollo de software en la que **las especificaciones son el elemento central del proceso de desarrollo**.

En lugar de comenzar escribiendo código después de leer una User Story, el equipo comienza construyendo una especificación técnica completa que describe con precisión qué debe construirse, por qué debe construirse y cómo debería comportarse el sistema.

En SDD el código deja de ser el punto de partida.

La especificación pasa a ser la fuente oficial de conocimiento del proyecto.

Todo el ciclo de desarrollo gira alrededor de ella.

---

# El problema del desarrollo tradicional

En muchas organizaciones el flujo de trabajo es similar al siguiente:

```
Product Owner
      │
      ▼
User Story
      │
      ▼
Desarrollador
      │
      ▼
Código
      │
      ▼
Tests
```

Aunque este proceso funciona, presenta varios problemas:

* Las User Stories suelen ser demasiado breves.
* Muchas reglas de negocio permanecen únicamente en conversaciones.
* Las decisiones técnicas quedan dispersas entre Pull Requests, comentarios o documentación aislada.
* La documentación pierde vigencia rápidamente.
* Los nuevos integrantes del equipo tardan en comprender el contexto.
* Las herramientas de IA deben inferir información que nunca fue documentada.

Con el tiempo, el conocimiento del proyecto deja de estar centralizado.

---

# La aparición de la Inteligencia Artificial

La llegada de herramientas como GitHub Copilot, Claude Code y otros agentes de IA cambió la forma de desarrollar software.

Sin embargo, estas herramientas solo pueden producir buenos resultados cuando reciben contexto suficiente.

Una IA que únicamente conoce una User Story deberá inferir:

* reglas de negocio;
* restricciones técnicas;
* arquitectura existente;
* convenciones del proyecto;
* criterios de aceptación.

Cada inferencia aumenta el riesgo de implementar una solución incorrecta.

La IA no reemplaza la necesidad de especificar correctamente el problema; por el contrario, hace que una buena especificación sea aún más importante.

---

# La filosofía de SDD

Specification-Driven Development propone invertir el esfuerzo.

En lugar de dedicar la mayor parte del tiempo a corregir implementaciones, se dedica más tiempo a construir una especificación precisa.

Una vez que la especificación es clara:

* el desarrollo resulta más predecible;
* los agentes de IA generan mejores resultados;
* las pruebas pueden definirse desde el inicio;
* la documentación se mantiene sincronizada con el código.

El código pasa a ser una consecuencia natural de una buena especificación.

---

# La especificación como fuente de verdad

En SDD toda la información relevante vive dentro de la especificación.

Una especificación puede incluir:

* objetivos del negocio;
* alcance;
* requisitos funcionales;
* requisitos no funcionales;
* reglas de negocio;
* restricciones técnicas;
* decisiones arquitectónicas;
* tareas de implementación;
* estrategia de pruebas;
* criterios de aceptación.

De esta manera, cualquier integrante del equipo consulta una única fuente de información consistente.

---

# Beneficios de SDD

Adoptar Specification-Driven Development aporta beneficios como:

* mejor comunicación entre negocio y desarrollo;
* mayor trazabilidad;
* reducción de ambigüedades;
* documentación siempre actualizada;
* incorporación más rápida de nuevos desarrolladores;
* mejor aprovechamiento de herramientas de IA;
* menor cantidad de retrabajo;
* mayor calidad del software.

---

# ¿SDD reemplaza Scrum o Azure DevOps?

No.

SDD no reemplaza las metodologías ágiles ni las herramientas de gestión.

Por el contrario, las complementa.

Una User Story continúa representando una necesidad del negocio.

La diferencia es que, antes de escribir código, esa necesidad se transforma en una especificación técnica completa que servirá como guía para el desarrollo.

Por este motivo, SDD puede integrarse perfectamente con herramientas como Azure DevOps, GitHub, GitHub Copilot, Claude Code y OpenSpec.

---

# Lo que aprenderás en este curso

Durante los siguientes módulos aprenderás a:

* convertir User Stories en especificaciones completas;
* estructurar proyectos utilizando OpenSpec;
* diseñar soluciones antes de implementarlas;
* trabajar con Claude Code utilizando especificaciones;
* utilizar GitHub Copilot como asistente durante la implementación;
* generar pruebas a partir de las especificaciones;
* integrar SDD con Azure DevOps;
* construir un flujo de desarrollo moderno, repetible y preparado para trabajar con Inteligencia Artificial.

---

# Resumen

Specification-Driven Development cambia el foco del desarrollo de software.

En lugar de considerar el código como el principal activo del proyecto, sitúa a la especificación como la fuente de verdad que guía todas las etapas del ciclo de vida del software.

Este enfoque resulta especialmente valioso en la era de la Inteligencia Artificial, donde la calidad del contexto determina en gran medida la calidad del resultado generado por los agentes de desarrollo.

En el siguiente capítulo profundizaremos en los conceptos fundamentales que forman parte de una especificación y comprenderemos cómo se relacionan entre sí.
