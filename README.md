# Proyecto Piloto: CG_SupportHub — Implementación de Dynamics 365 Customer Service

[![Microsoft Dynamics 365 Customer Service](https://img.shields.io/badge/Microsoft_Dynamics_365_Customer_Service-002050?logo=dynamics365&logoColor=white)](https://dynamics.microsoft.com/customer-service/)
[![Microsoft Power Platform](https://img.shields.io/badge/Microsoft_Power_Platform-742774?logo=powerplatform&logoColor=white)](https://powerplatform.microsoft.com/)
[![Power Apps](https://img.shields.io/badge/Power_Apps-742774?logo=powerapps&logoColor=white)](https://make.powerapps.com/)
[![Power Automate](https://img.shields.io/badge/Power_Automate-0066FF?logo=powerautomate&logoColor=white)](https://make.powerautomate.com/)
[![Microsoft Entra ID](https://img.shields.io/badge/Microsoft_Entra_ID-0078D4?logo=microsoft&logoColor=white)](https://entra.microsoft.com/)
[![Microsoft 365 Admin Center](https://img.shields.io/badge/Microsoft_365_Admin_Center-D83B01?logo=microsoft&logoColor=white)](https://admin.microsoft.com/)
[![Dynamics 365 Customer Voice](https://img.shields.io/badge/Dynamics_365_Customer_Voice-00A2ED?logo=dynamics365&logoColor=white)](https://dynamics.microsoft.com/customer-voice/)
[![Microsoft Dataverse](https://img.shields.io/badge/Microsoft_Dataverse-0078D4?logo=powerplatform&logoColor=white)](https://powerplatform.microsoft.com/dataverse/)

## 📋 Descripción General

Este repositorio contiene la documentación y guía de implementación del proyecto piloto **CG_SupportHub**, un sistema de gestión de servicio al cliente construido sobre **Microsoft Dynamics 365 Customer Service** para la empresa ficticia **CG_TechSolutions**, dedicada al soporte técnico de hardware y software para clientes corporativos.

El proyecto está diseñado como una implementación práctica de tamaño moderado que permita comprender la **interacción entre todos los componentes** del ecosistema de Customer Service: cuentas, contactos, colas, casos, actividades, SLAs, automatizaciones y encuestas de satisfacción. Se desarrolla íntegramente en un **entorno de prueba (Sandbox)** compartido, por lo que **todos los registros creados deben iniciar con el prefijo `CG_`** para su correcta identificación.

El enfoque es **técnico, práctico y guiado**, con una metodología tipo "profesor": se explica el *por qué* antes del *cómo*, y se valida cada fase antes de avanzar a la siguiente.

---

## 🎯 Objetivo del Proyecto

Configurar un sistema funcional de soporte técnico en Dynamics 365 Customer Service que permita:

- Manejar incidencias de clientes corporativos mediante **colas** y reglas de enrutamiento.
- Clasificar y medir el cumplimiento mediante **SLA** por niveles de servicio.
- Registrar interacciones en **casos** y **actividades**.
- Recoger la satisfacción del cliente mediante **encuestas de Dynamics 365 Customer Voice**.
- Automatizar la asignación, el seguimiento y las notificaciones con **Power Automate**.
- Gestionar la información maestra mediante **cuentas** y **contactos**.
- Comprender la relación e interacción entre **todos los elementos** del sistema.

---

## 📐 Alcance

### Alcance Inicial (Piloto)

El piloto cubre el **ciclo completo de una incidencia**, desde su entrada hasta la medición de satisfacción, sin incluir integraciones avanzadas ni personalizaciones de código:

1. **Canales de entrada:** creación manual de casos desde el Centro de servicio **y** configuración de **Email-to-Case** con un buzón dedicado y regla de creación automática de registros.
2. **Datos maestros:** cuentas corporativas, contactos y agentes con roles definidos.
3. **Colas y enrutamiento:** colas con prefijo `CG_` y asignación automática según nivel de SLA u origen.
4. **SLA:** tres niveles — **CG_Oro** (respuesta en 1 día), **CG_Plata** (2 días) y **CG_Bronce** (3 días).
5. **Automatizaciones clave:**
   - Enrutamiento por colas.
   - Notificación al cliente al resolver el caso.
   - Escalado automático si el SLA está por vencer.
   - Creación de tarea de seguimiento post-resolución.
   - Encuesta de Customer Voice al resolver el caso, con acción condicionada al **NPS (< 7 o > 8)**.
6. **Roles de usuario:** `CG_AgenteN1`, `CG_AgenteN2`, `CG_Supervisor`.

### Alcance General (Visión ampliada)

Fuera del alcance del piloto, pero considerado como evolución futura del sistema:

- Enrutamiento unificado (*unified routing*) con asignación por capacidad y habilidades.
- Integración con portal de autoservicio y chatbots.
- Gestión de derechos (*entitlements*) por contrato corporativo.
- Paneles analíticos avanzados (Customer Service Insights / Omnichannel).
- Procesos de promoción de soluciones desde Sandbox a producción.

---

## 🗂️ Estructura del Proyecto

### Fase 1: Configuración Inicial (Seguridad y Datos Maestros)

#### 1. Usuarios del Sistema / Agentes (Users / Agents)

**Descripción:** Gestión de identidades (Microsoft Entra ID) asignadas a roles de seguridad y unidades de negocio dentro de Dynamics 365, utilizadas para simular la jerarquía de soporte.

**Implementación:**
- **Portal:** Power Platform Admin Center / Microsoft 365 Admin Center / Power Apps Maker Portal
- **Ruta:** `Customer Service Admin Center > Support settings > Users`
- **Campos Estándar:** Full Name, Primary Email, Business Unit, Security Roles
- **Campos Personalizados:** Nivel de Especialización (Choice: Nivel 1, Nivel 2, Supervisor)

**Roles a crear:** `CG_AgenteN1`, `CG_AgenteN2`, `CG_Supervisor`

#### 2. Cuentas, Clientes y Contactos (Accounts & Contacts)

**Descripción:** Entidades relacionales que representan empresas (Accounts) y personas (Contacts) que interactúan con el servicio de CG_TechSolutions.

**Implementación:**
- **Portal:** Customer Service Workspace / Customer Service Admin Center
- **Ruta:** `Customer Service Admin Center > Customer settings > Accounts and contacts`
- **Campos Estándar:** Account Name, Primary Contact, Email, Phone
- **Campos Personalizados:** Segmento de Cliente (Enterprise, SMB), Nivel de Soporte Contratado (Oro, Plata, Bronce)

---

### Fase 2: Operación y Enrutamiento (Casos y Colas)

#### 3. Colas (Queues), Email-to-Case y Actividades

**Descripción:** Contenedores donde se acumulan casos o actividades pendientes de ser atendidos por un equipo o agente, además del canal de entrada por correo electrónico.

**Implementación:**
- **Portal:** Customer Service Admin Center
- **Ruta:** `Customer Service Admin Center > Customer support > Queues > Basic queues > New`
- **Configuración:** Tipo (Public/Private), miembros (Users/Teams), Owner, Incoming Email
- **Email-to-Case:** Buzón dedicado + regla de creación automática de registros (Automatic Record Creation)
- **Campos Personalizados:** Canal de Origen (Email, Manual)

#### 4. Casos (Cases / Incident Management)

**Descripción:** El registro central de un problema, incidencia o solicitud del cliente. Es el núcleo del proyecto y el punto donde convergen colas, SLA, actividades y encuestas.

**Implementación:**
- **Portal:** Customer Service Admin Center / Customer Service Workspace
- **Ruta:** `Customer Service Admin Center > Case settings > Case types / Parent and child cases`
- **Campos Estándar:** Title, Customer, Origin, Priority, Case Type, Description
- **Campos Personalizados:** Nivel de SLA (Lookup a CG_Oro / CG_Plata / CG_Bronce), Impacto en Negocio

---

### Fase 3: Acuerdos y Cumplimiento (SLAs)

#### 5. Acuerdos de Nivel de Servicio (SLAs)

**Descripción:** Acuerdos formales que definen los tiempos límite de respuesta y resolución, diferenciados por nivel de servicio contratado.

**Implementación:**
- **Portal:** Customer Service Admin Center
- **Ruta:** `Customer Service Admin Center > Service terms > Service Level Agreements (SLAs) > Manage`
- **Configuración:** Enhanced SLAs, SLA KPIs (First Response By / Resolve By), acciones de advertencia e incumplimiento
- **Niveles a configurar:**
  - **CG_Oro** — respuesta en 1 día
  - **CG_Plata** — respuesta en 2 días
  - **CG_Bronce** — respuesta en 3 días
- **Campos Personalizados:** Condición de pausa personalizada por cliente

---

### Fase 4: Automatización y Medición Continua

#### 6. Automatizaciones con Power Automate

**Descripción:** Flujos que conectan los componentes del sistema para dar respuesta automática a eventos clave del ciclo de vida del caso.

**Implementación:**
- **Portal:** Power Automate Maker Portal
- **Flujos a crear (todos con prefijo `CG_`):**
  - **CG_NotificarClienteResolucion** — notificación al cliente al resolver el caso.
  - **CG_EscaladoSLAProximo** — escalado automático si el SLA está por vencer.
  - **CG_TareaSeguimiento** — creación de tarea de seguimiento post-resolución.
  - **CG_EncuestaNPS** — disparo de encuesta de Customer Voice al resolver, con acción condicionada al NPS.

#### 7. Encuestas de Satisfacción (Customer Voice / Feedback)

**Descripción:** Herramienta integrada para recopilar el feedback del cliente (CSAT / NPS) tras la resolución de un caso.

**Implementación:**
- **Portal:** Customer Service Admin Center / Dynamics 365 Customer Voice
- **Ruta:** `Customer Service Admin Center > Customer feedback > Survey settings > Manage`
- **Automatización:** Power Automate para disparo al resolver el caso
- **Lógica NPS:** si el **NPS < 7** o **NPS > 8**, se activa una acción específica (alerta o seguimiento). El rango 7–8 queda como neutro.
- **Campos Estándar:** Rating, Comments, Customer
- **Campos Personalizados:** Puntuación CSAT Global (Numérica del 1 al 5)

---

## 🔄 Ciclo Completo a Validar

Al finalizar las cuatro fases, el piloto debe permitir probar de extremo a extremo.


---

## 📚 Conceptos Cubiertos

- ✅ Configuración de usuarios y roles de seguridad
- ✅ Gestión de cuentas y contactos
- ✅ Creación y configuración de colas
- ✅ Configuración de Email-to-Case
- ✅ Gestión del ciclo de vida de casos
- ✅ Configuración de Enhanced SLAs con múltiples niveles
- ✅ KPIs de SLA y acciones automáticas de advertencia/incumplimiento
- ✅ Automatizaciones con Power Automate (notificaciones, escalados, tareas)
- ✅ Integración con Customer Voice
- ✅ Automatización de encuestas condicionada al NPS

---

## 🚀 Cómo Utilizar Este Repositorio

1. **Clona el repositorio** en tu máquina local
2. **Sigue las fases en orden** (Fase 1 → Fase 4)
3. **Respeta la nomenclatura `CG_`** en todos los registros creados
4. **Implementa cada configuración** en tu entorno de pruebas (Sandbox)
5. **Valida cada fase** antes de avanzar a la siguiente
6. **Documenta tus resultados** y personalizaciones


## 👤🍋‍🟩 Autor
**Camilo García Rey** 
- LinkedIn: https://www.linkedin.com/in/camilo-garcia-rey/  
- GitHub Portfolio: github.com/camilogrey 