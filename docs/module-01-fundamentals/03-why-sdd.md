# Módulo 1 – Fundamentos de Specification-Driven Development

# 1. ¿Por qué surge SDD?

## Introducción

Durante décadas, la industria del software ha buscado formas de construir sistemas más confiables, mantenibles y predecibles.

Hemos evolucionado desde modelos altamente secuenciales como Waterfall hasta metodologías ágiles como Scrum y Kanban.

Sin embargo, incluso con metodologías modernas, muchos equipos continúan enfrentando un problema fundamental:

> La distancia entre entender un problema y construir correctamente una solución.

Specification-Driven Development surge como una respuesta a este problema.

---

# El problema central: construir antes de comprender

En muchos equipos el ciclo comienza así:

```text
Necesidad del negocio

        │

        ▼

User Story

        │

        ▼

Desarrollador comienza a programar

        │

        ▼

Surgen preguntas

        │

        ▼

Cambios y retrabajo
```

El problema no es que los desarrolladores no sepan programar.

El problema es que muchas decisiones importantes se toman demasiado tarde.

---

# Ejemplo real

Supongamos una User Story:

```text
Como cliente quiero actualizar mi dirección
para recibir correctamente mis pedidos.
```

A primera vista parece sencilla.

Pero durante la implementación aparecen preguntas:

## Negocio

* ¿Puede cualquier cliente cambiar la dirección?
* ¿Se necesita aprobación?
* ¿Se guarda historial?
* ¿Qué ocurre con pedidos existentes?

---

## Seguridad

* ¿Cómo verificamos identidad?
* ¿Puede modificar datos sensibles?
* ¿Existe auditoría?

---

## Backend

* ¿Qué servicio actualizamos?
* ¿Existe una API?
* ¿Qué ocurre si falla la persistencia?

---

## Frontend

* ¿Qué validaciones necesita?
* ¿Qué mensajes mostramos?
* ¿Cómo manejamos errores?

---

## Testing

* ¿Cuáles son los escenarios esperados?
* ¿Qué casos negativos existen?

---

La User Story no estaba incorrecta.

Simplemente no tenía suficiente información para implementar una solución completa.

---

# El costo de la ambigüedad

La ambigüedad genera:

## Retrabajo

Una decisión incorrecta descubierta tarde cuesta más corregirla.

Ejemplo:

```text
Cambio detectado durante análisis

Costo bajo


Cambio detectado durante desarrollo

Costo medio


Cambio detectado en producción

Costo alto
```

---

## Dependencia del conocimiento tribal

Muchas organizaciones funcionan porque algunas personas conocen información que nunca fue documentada.

Ejemplo:

> "No uses ese endpoint porque falla con clientes antiguos."

Pero esa información solamente existe en la memoria de alguien.

---

## Problemas de comunicación

Negocio, arquitectura, desarrollo y QA pueden interpretar una misma historia de maneras diferentes.

Ejemplo:

Product Owner:

> "Necesitamos permitir editar datos."

Desarrollador:

> "Haré un formulario editable."

QA:

> "Necesito saber qué reglas aplicar."

Arquitecto:

> "Hay restricciones de integración."

Todos hablan del mismo tema, pero desde perspectivas diferentes.

---

# La evolución del desarrollo

Podemos visualizar la evolución así:

## Primera etapa: Código como centro

```text
Código

    ▲

Desarrollador
```

El conocimiento estaba principalmente en las personas.

---

## Segunda etapa: Procesos ágiles

```text
Backlog

    │

User Stories

    │

Equipo
```

Mejoró la comunicación, pero muchas decisiones seguían siendo implícitas.

---

## Tercera etapa: Specification-Driven Development

```text
              Specification

                    │

       ┌────────────┼────────────┐

       ▼            ▼            ▼

    Negocio     Desarrollo     IA

                    │

                    ▼

                  Código
```

La Specification se convierte en el punto común de entendimiento.

---

# El impacto de la Inteligencia Artificial

Antes de la IA generativa, una documentación incompleta afectaba principalmente a humanos.

Hoy afecta también a agentes.

Un desarrollador puede preguntar:

> "¿Cómo funciona este módulo?"

y dedicar tiempo a investigar.

Un agente de IA también necesita ese contexto.

Si recibe información incompleta puede generar:

* código incorrecto;
* soluciones incompatibles;
* cambios innecesarios.

---

# La nueva ecuación del desarrollo

Antes:

```text
Experiencia del desarrollador
+
Código
=
Software
```

Ahora:

```text
Experiencia humana
+
Specification
+
IA
+
Código
=
Software moderno
```

La Specification se convierte en el puente entre humanos e inteligencia artificial.

---

# SDD no elimina el análisis

Un error común es pensar:

> "La IA escribe código, entonces necesitamos menos análisis."

Ocurre exactamente lo contrario.

Cuanto más poderosa es la herramienta de implementación, más importante es comprender correctamente el problema.

La velocidad sin dirección solamente acelera errores.

---

# El nuevo rol del desarrollador

Con SDD el desarrollador evoluciona.

No solamente pregunta:

> "¿Cómo implemento esto?"

También pregunta:

* ¿Cuál es el problema real?
* ¿Qué restricciones existen?
* ¿Qué alternativas tenemos?
* ¿Qué impacto tendrá?
* ¿Cómo validaremos la solución?

La programación continúa siendo importante, pero aumenta la importancia del diseño y el razonamiento.

---

# Principios iniciales de SDD

De este capítulo podemos extraer cinco principios:

## 1. Comprender antes de construir

No comenzar por código.

---

## 2. Hacer explícito el conocimiento

Lo importante debe estar documentado.

---

## 3. Reducir decisiones tardías

Los problemas deben descubrirse temprano.

---

## 4. Crear contexto reutilizable

La información debe servir a humanos y máquinas.

---

## 5. Mantener trazabilidad

Cada cambio debe tener una razón.

---

# Resumen

Specification-Driven Development surge porque los equipos necesitan reducir la distancia entre la intención del negocio y la implementación técnica.

Las metodologías ágiles mejoraron la entrega de valor, pero muchas veces dejaron decisiones importantes implícitas.

SDD propone una evolución:

Antes de escribir código, construir una comprensión compartida mediante una Specification.

Esa Specification se convierte en la base para:

* diseñar;
* implementar;
* probar;
* colaborar;
* trabajar con IA.

---

# Próximo capítulo

En el siguiente capítulo analizaremos los problemas del desarrollo tradicional en profundidad y veremos por qué incluso equipos ágiles y maduros siguen enfrentando desafíos relacionados con contexto, documentación y conocimiento.
