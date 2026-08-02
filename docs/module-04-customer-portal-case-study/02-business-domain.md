# Dominio del negocio

## Introducción

Todo sistema de software existe para resolver un problema de negocio.

Antes de definir arquitecturas, tecnologías o componentes, debemos comprender:

* quién utiliza el sistema;
* qué problema intenta resolver;
* qué valor aporta;
* cuáles son las reglas del negocio.

En Specification-Driven Development este conocimiento se captura explícitamente desde el comienzo.

Las Specifications describen capacidades del negocio, no únicamente funcionalidades técnicas.

---

# Nuestra empresa ficticia

Durante el resto del curso trabajaremos con una empresa ficticia llamada:

```text
Acme Insurance
```

Acme Insurance ofrece distintos productos de seguros para personas y empresas.

Actualmente sus clientes realizan muchas gestiones mediante:

* llamadas telefónicas;
* correos electrónicos;
* sucursales físicas.

Esto genera:

* altos costos operativos;
* tiempos de espera elevados;
* baja satisfacción del cliente.

La empresa decide construir un Customer Portal para digitalizar estos procesos.

---

# Objetivos del negocio

La dirección de la empresa define los siguientes objetivos estratégicos.

## Objetivo 1

Reducir el volumen de llamadas al centro de atención.

---

## Objetivo 2

Permitir que los clientes resuelvan sus gestiones sin intervención humana.

---

## Objetivo 3

Disminuir los tiempos de respuesta.

---

## Objetivo 4

Ofrecer una experiencia consistente desde cualquier dispositivo.

---

## Objetivo 5

Crear una plataforma preparada para incorporar nuevas capacidades durante los próximos años.

---

# El problema que resolveremos

Actualmente un cliente necesita contactar al soporte para tareas como:

* descargar una factura;
* consultar un beneficio;
* actualizar sus datos personales;
* revisar el estado de un reclamo;
* obtener un documento.

Cada interacción implica costos para la empresa y demoras para el cliente.

Nuestro portal busca transformar estas operaciones en procesos de autoservicio.

---

# ¿Quiénes son nuestros usuarios?

El sistema tendrá varios tipos de usuarios.

## Cliente

Es el usuario principal.

Puede:

* consultar información;
* administrar su perfil;
* descargar documentos;
* iniciar reclamos;
* revisar beneficios.

---

## Operador

Trabaja dentro de la empresa.

Puede:

* visualizar información de clientes;
* responder consultas;
* gestionar reclamos;
* revisar auditorías.

---

## Administrador

Gestiona la plataforma.

Puede:

* administrar usuarios;
* configurar parámetros;
* habilitar funcionalidades;
* revisar métricas.

---

## Sistemas externos

El portal también interactuará con otros sistemas.

Ejemplos:

* sistema de facturación;
* sistema documental;
* autenticación corporativa;
* motor de notificaciones.

No todos los actores son personas.

---

# Capacidades del producto

El Customer Portal crecerá mediante capacidades independientes.

Durante el curso implementaremos, entre otras:

```text
Authentication

↓

Customer Profile

↓

Benefits

↓

Claims

↓

Invoices

↓

Documents

↓

Notifications

↓

Administration
```

Cada capacidad tendrá su propio conjunto de Specifications.

---

# Principios del dominio

Definimos algunos principios que guiarán todas las decisiones.

## Autoservicio

Siempre que sea posible, el cliente debe resolver la gestión sin intervención del soporte.

---

## Seguridad

Toda información sensible requiere autenticación y autorización.

---

## Simplicidad

La experiencia del usuario debe ser sencilla.

La complejidad pertenece al sistema, no al usuario.

---

## Escalabilidad

Las nuevas funcionalidades deben integrarse sin rediseñar el producto completo.

---

## Trazabilidad

Toda capacidad implementada debe poder relacionarse con una necesidad de negocio.

---

# Reglas generales

Estas reglas aplicarán a todo el sistema.

## RG-001

Todo usuario debe autenticarse antes de acceder a información privada.

---

## RG-002

Un cliente únicamente puede acceder a sus propios datos.

---

## RG-003

Toda operación importante debe quedar registrada para auditoría.

---

## RG-004

Las operaciones deben ser idempotentes siempre que sea posible.

---

## RG-005

Toda capacidad debe estar documentada mediante una Specification.

---

# Métricas de éxito

¿Cómo sabremos que el proyecto fue exitoso?

Algunos indicadores podrían ser:

* reducción del volumen de llamadas;
* incremento del uso del portal;
* tiempo medio para completar una gestión;
* porcentaje de gestiones resueltas sin soporte;
* satisfacción del cliente.

Estas métricas permitirán evaluar el impacto del producto más allá del desarrollo técnico.

---

# Relación con Azure DevOps

El dominio del negocio dará origen al backlog.

Por ejemplo:

```text
Epic

Customer Self-Service

↓

Feature

Invoice Management

↓

User Story

Download Invoice
```

Azure DevOps organizará el trabajo.

OpenSpec describirá el conocimiento.

---

# Relación con OpenSpec

Cada capacidad del negocio se convertirá en una Specification.

Ejemplo:

```text
specs/

authentication/

customer-profile/

benefits/

claims/

invoices/

documents/

notifications/
```

Cada Specification evolucionará de forma independiente.

---

# Relación con los agentes IA

Los agentes no deberían recibir únicamente tareas técnicas.

También necesitan comprender el contexto del negocio.

Por ejemplo, antes de implementar una funcionalidad de facturación, el agente debería conocer:

* quién utiliza esa funcionalidad;
* qué problema resuelve;
* cuáles son las reglas del negocio;
* qué restricciones existen.

Ese contexto reduce implementaciones incorrectas.

---

# Caso práctico

Supongamos la siguiente petición:

> "Permitir descargar una factura."

Antes de escribir código debemos responder:

* ¿Quién puede descargarla?
* ¿Qué tipos de factura existen?
* ¿Durante cuánto tiempo están disponibles?
* ¿Qué ocurre si no existe?
* ¿Debe registrarse la descarga?
* ¿Existen restricciones legales?

Estas preguntas pertenecen al dominio del negocio.

Las respuestas terminarán formando parte de la Specification.

---

# Buenas prácticas

* Comprender el negocio antes de diseñar la solución.
* Separar reglas de negocio de decisiones técnicas.
* Mantener el lenguaje del dominio consistente.
* Evitar términos ambiguos.
* Versionar el conocimiento junto con el código.

---

# Errores comunes

## Comenzar por la arquitectura

La arquitectura responde **cómo**.

Primero debemos entender **qué** y **por qué**.

---

## Mezclar reglas del negocio con detalles técnicos

Una Specification funcional no debería depender de Angular, React o cualquier otra tecnología.

---

## Pensar que el dominio pertenece únicamente al Product Owner

El dominio debe ser comprendido por todo el equipo.

---

# Resumen

El dominio del negocio es el punto de partida de Specification-Driven Development.

Comprender el problema, los usuarios y las reglas permite construir Specifications de mayor calidad y proporciona el contexto que tanto los desarrolladores como los agentes de IA necesitan para tomar mejores decisiones.

---

# Próximo capítulo

```text
docs/module-04-customer-portal-case-study/

03-product-vision.md
```

En el siguiente capítulo transformaremos el conocimiento del negocio en una visión concreta del producto. Definiremos el alcance inicial del Customer Portal, sus capacidades principales y cómo evolucionará mediante un roadmap incremental.
