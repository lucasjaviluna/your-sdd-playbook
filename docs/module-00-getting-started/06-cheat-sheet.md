# SDD Cheat Sheet

## Guía rápida de Specification-Driven Development

Este documento resume las reglas, estructuras y verificaciones principales para aplicar SDD en el día a día.

Utilízalo como referencia antes, durante y después del desarrollo de una funcionalidad.

---

# Flujo SDD completo

```text
┌─────────────────┐
│ Azure DevOps    │
│ User Story      │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Specification   │
│ OpenSpec        │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Requirements    │
│ Design          │
│ ADR             │
│ Tasks           │
│ Tests           │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ AI Assisted     │
│ Development     │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Pull Request    │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Production      │
└─────────────────┘
```

---

# Antes de comenzar una funcionalidad

## Checklist de Specification

Antes de escribir código verificar:

### Contexto

* [ ] ¿Está claro el problema de negocio?
* [ ] ¿Está explicado por qué existe esta funcionalidad?
* [ ] ¿Está definido el alcance?

---

### Requirements

* [ ] ¿Los requerimientos están escritos?
* [ ] ¿Son verificables?
* [ ] ¿Existen casos positivos y negativos?
* [ ] ¿Se conocen las reglas de negocio?

---

### Design

* [ ] ¿Está definida la solución técnica?
* [ ] ¿Se conocen los componentes afectados?
* [ ] ¿Se identificaron integraciones?
* [ ] ¿Existen decisiones arquitectónicas importantes?

---

### Tasks

* [ ] ¿El trabajo está dividido en tareas pequeñas?
* [ ] ¿Cada tarea tiene un objetivo claro?
* [ ] ¿Las tareas pueden ejecutarse de forma independiente?

---

### Testing

* [ ] ¿Existe un plan de pruebas?
* [ ] ¿Cada requirement tiene validación?
* [ ] ¿Se conocen los escenarios límite?

---

# Estructura mínima de una Specification

```text
specs/

└── feature-name/

    ├── spec.md
    │
    ├── requirements.md
    │
    ├── design.md
    │
    ├── tasks.md
    │
    └── test-plan.md
```

---

# Template mental de una Specification

Antes de desarrollar responder:

## ¿Por qué?

Context.

```text
¿Cuál es el problema que resolvemos?
```

---

## ¿Qué?

Requirements.

```text
¿Qué debe hacer el sistema?
```

---

## ¿Cómo?

Design.

```text
¿Cómo implementaremos la solución?
```

---

## ¿Qué pasos?

Tasks.

```text
¿Qué trabajo debemos realizar?
```

---

## ¿Cómo sabemos que funciona?

Tests.

```text
¿Cómo validamos el resultado?
```

---

# Uso con agentes de IA

## Mal ejemplo

Prompt:

```text
Implementa esta historia.
```

Problema:

La IA debe adivinar:

* arquitectura;
* reglas;
* restricciones;
* estilo del proyecto.

---

## Buen ejemplo

Prompt:

```text
Implementa TASK-003.

Lee previamente:

- spec.md
- requirements.md
- design.md

Reglas:

- Respeta arquitectura existente.
- No modifiques archivos fuera del alcance.
- Agrega pruebas.
- Explica decisiones importantes.
```

---

# Regla para trabajar con IA

Nunca entregar solamente una tarea.

Entregar:

```
Objetivo
+
Contexto
+
Restricciones
+
Resultado esperado
```

---

# Checklist para Claude Code

Antes de solicitar implementación:

* [ ] La Specification está completa.
* [ ] El Design está aprobado.
* [ ] Las Tasks están claras.
* [ ] Las restricciones técnicas están documentadas.
* [ ] La IA conoce la arquitectura existente.

---

# Checklist para GitHub Copilot

Copilot funciona mejor cuando:

* [ ] El código existente es claro.
* [ ] Los nombres son descriptivos.
* [ ] Existen interfaces bien definidas.
* [ ] Los tests muestran ejemplos.
* [ ] La arquitectura es consistente.

Copilot complementa al desarrollador; no reemplaza la Specification.

---

# Checklist de Pull Request

Antes de aprobar:

## Código

* [ ] Cumple estándares del proyecto.
* [ ] Tiene pruebas.
* [ ] No introduce deuda innecesaria.

---

## Specification

* [ ] Está actualizada.
* [ ] Representa la implementación real.
* [ ] Incluye nuevas decisiones.

---

## Arquitectura

* [ ] No rompe patrones existentes.
* [ ] Las decisiones importantes tienen ADR.

---

# Anti-patrones comunes

## Empezar por el código

Incorrecto:

```text
Idea
 ↓
Código
 ↓
Intentar documentar
```

Correcto:

```text
Idea
 ↓
Specification
 ↓
Código
```

---

## Specifications gigantes

Una Specification debe representar una capacidad concreta.

Evitar:

```text
Sistema completo de clientes
```

Preferir:

```text
Actualizar dirección del cliente
```

---

## Documentación separada del código

Problema:

```
Código actualizado

Documentación antigua
```

Solución:

```
Pull Request

Código + Specification
```

---

## Dar poco contexto a la IA

Problema:

```text
Haz esta pantalla.
```

Solución:

```text
Implementa la pantalla siguiendo:

- diseño;
- componentes existentes;
- reglas;
- pruebas esperadas.
```

---

# Principios fundamentales

## Principio 1

La Specification es la fuente de verdad.

---

## Principio 2

El código implementa la Specification.

---

## Principio 3

Toda decisión importante debe quedar registrada.

---

## Principio 4

La IA necesita contexto, no solamente instrucciones.

---

## Principio 5

La responsabilidad final siempre permanece en el equipo humano.

---

# SDD en una frase

> Specification-Driven Development es construir software a partir de conocimiento estructurado, utilizando la IA como acelerador bajo supervisión humana.

---

# Resumen

Si solamente recuerdas cinco pasos:

1. Entiende el problema.
2. Escribe la Specification.
3. Diseña antes de implementar.
4. Usa IA con contexto.
5. Valida que código y Specification sean coherentes.

Ese es el ciclo fundamental de SDD.

---

# Próximo capítulo

El siguiente archivo será:

```text
07-learning-roadmap.md
```

donde cerraremos el Módulo 0 explicando el camino completo de aprendizaje y cómo utilizar este playbook para avanzar hacia una adopción empresarial de SDD.
