# Módulo 4 — Customer Portal: Caso de estudio completo

## Introducción

Hasta este punto del curso aprendimos los principios de Specification-Driven Development (SDD), cómo estructurar una Specification con OpenSpec y cómo integrar herramientas como Azure DevOps, GitHub y asistentes de IA en el flujo de desarrollo.

A partir de este módulo cambiaremos el enfoque.

En lugar de estudiar conceptos de forma aislada, construiremos un **caso de estudio completo** que evolucionará durante el resto del curso.

Este proyecto será el hilo conductor para aplicar todos los conceptos aprendidos.

---

# Objetivo del caso de estudio

El objetivo es simular el trabajo de un equipo de ingeniería que desarrolla un producto empresarial desde cero utilizando Specification-Driven Development como metodología principal.

Durante los siguientes módulos construiremos:

* el backlog del producto;
* las User Stories;
* las Specifications;
* los ADRs (Architecture Decision Records);
* la arquitectura;
* los prompts para agentes IA;
* las Pull Requests;
* los planes de prueba;
* los workflows de desarrollo;
* los procesos de revisión.

Todo el conocimiento del proyecto quedará versionado junto al código.

---

# ¿Por qué un Customer Portal?

Necesitamos un dominio suficientemente amplio para cubrir situaciones reales que aparecen en proyectos empresariales.

Un portal de clientes reúne la mayoría de estos escenarios:

* autenticación;
* autorización;
* perfiles de usuario;
* consultas de información;
* carga y descarga de documentos;
* formularios;
* integraciones con APIs;
* notificaciones;
* administración.

Además, es un dominio conocido por la mayoría de los equipos de desarrollo, lo que permite concentrarse en la metodología sin depender de conocimientos específicos del negocio.

---

# Visión del producto

Imaginemos una empresa que ofrece distintos servicios a sus clientes.

Actualmente, muchas gestiones requieren contactar al soporte.

El objetivo del Customer Portal es ofrecer una plataforma de autoservicio donde los clientes puedan realizar esas operaciones de forma segura y eficiente.

Algunas de las capacidades que tendrá el portal serán:

* iniciar sesión;
* consultar información personal;
* administrar su perfil;
* visualizar beneficios;
* gestionar reclamos;
* descargar facturas y documentos;
* recibir notificaciones;
* configurar preferencias.

Cada una de estas capacidades será desarrollada siguiendo el flujo completo de Specification-Driven Development.

---

# Objetivos del módulo

Al finalizar este módulo comprenderás:

* cómo transformar una visión de producto en un backlog inicial;
* cómo organizar un proyecto utilizando OpenSpec;
* cómo estructurar Specifications por funcionalidad;
* cómo relacionar Azure DevOps con OpenSpec;
* cómo preparar el contexto que utilizarán los agentes de IA.

---

# El proyecto que construiremos

Durante el curso el repositorio irá creciendo progresivamente.

La estructura inicial será la siguiente:

```text
customer-portal/

├── azure-devops/
├── specs/
├── adrs/
├── architecture/
├── prompts/
├── workflows/
├── testing/
├── agents/
└── README.md
```

Cada directorio representará una parte del conocimiento del proyecto.

Por ejemplo:

* **azure-devops/** contendrá ejemplos del backlog y User Stories.
* **specs/** almacenará las Specifications de cada funcionalidad.
* **adrs/** documentará las decisiones arquitectónicas.
* **prompts/** incluirá el contexto y prompts utilizados por los agentes IA.
* **workflows/** describirá los procesos operativos del equipo.
* **testing/** contendrá planes de prueba y estrategias de validación.

---

# Nuestro flujo de trabajo

Durante todo el caso de estudio seguiremos el mismo proceso:

```text
Idea de negocio

↓

Azure DevOps

↓

User Story

↓

Specification

↓

Refinement

↓

Design

↓

Tasks

↓

Implementación

↓

Testing

↓

Pull Request

↓

Release

↓

Operación
```

Cada capítulo del curso desarrollará una parte de este flujo.

---

# El papel de la IA

La inteligencia artificial tendrá un rol importante, pero claramente delimitado.

Los agentes podrán ayudar a:

* analizar Specifications;
* generar propuestas de implementación;
* redactar pruebas;
* revisar código;
* detectar inconsistencias.

Sin embargo, las decisiones de negocio y arquitectura continuarán siendo responsabilidad del equipo.

Este principio de **Human-in-the-Loop** acompañará todo el curso.

---

# Un proyecto vivo

El Customer Portal no será un ejemplo estático.

Cada nuevo módulo añadirá capacidades al producto.

Por ejemplo:

* nuevos Requirements;
* nuevas Specifications;
* nuevas decisiones arquitectónicas;
* nuevos workflows;
* nuevos agentes.

Esto permitirá observar cómo evoluciona un proyecto real a lo largo del tiempo.

---

# Relación con Azure DevOps

En este curso mantendremos una separación clara entre planificación y conocimiento.

**Azure DevOps** será la herramienta para gestionar el trabajo:

* Epics;
* Features;
* User Stories;
* Bugs;
* Sprint Planning.

**OpenSpec** será la fuente de verdad del conocimiento funcional y técnico.

Ambos mundos estarán conectados mediante referencias, pero cada uno mantendrá una responsabilidad bien definida.

---

# Relación con GitHub

GitHub almacenará:

* código fuente;
* Specifications;
* ADRs;
* documentación técnica;
* prompts;
* workflows.

Todo evolucionará mediante Pull Requests.

La documentación dejará de ser un elemento externo al desarrollo y pasará a formar parte del mismo ciclo de vida.

---

# Lo que construiremos al finalizar el curso

Cuando completemos todos los módulos, el repositorio contendrá:

* un producto empresarial completamente documentado;
* un conjunto de Specifications enlazadas con un backlog;
* decisiones arquitectónicas registradas;
* ejemplos de prompts para agentes IA;
* estrategias de testing;
* playbooks operativos;
* workflows de desarrollo;
* ejemplos de revisión y despliegue.

Más que un ejercicio académico, será un repositorio de referencia para equipos que quieran adoptar Specification-Driven Development.

---

# Resumen

El Customer Portal será el escenario donde aplicaremos todos los conceptos aprendidos hasta ahora.

A partir de este momento cada nuevo tema se desarrollará sobre un proyecto real, siguiendo el mismo flujo que utilizaría un equipo profesional de ingeniería.

La Specification dejará de ser un ejemplo aislado y pasará a convertirse en el centro de un producto completo.

---

# Próximo capítulo

```
docs/module-04-customer-portal-case-study/

02-business-domain.md
```

En el siguiente capítulo definiremos el dominio del negocio: quién es la empresa, quiénes son los usuarios, qué problemas intenta resolver el Customer Portal y cómo esa visión se transformará en el backlog inicial del producto.
