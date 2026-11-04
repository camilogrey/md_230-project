# Proyecto Final MB-230: Implementación de Dynamics 365 Customer Service

## 📋 Descripción General

Este repositorio contiene la documentación y guía de implementación completa para el proyecto final de la certificación **Microsoft Dynamics 365 Customer Service (MB-230)** . El proyecto está diseñado como una implementación práctica y real de un sistema de gestión de servicio al cliente, cubriendo desde la configuración inicial hasta la medición de satisfacción del cliente.

El enfoque es **técnico, práctico y directo**, garantizando tanto el éxito en la implementación real como en el examen de certificación.

---

## 🎯 Objetivos del Proyecto

- Configurar un entorno completo de Dynamics 365 Customer Service
- Implementar seguridad, datos maestros y enrutamiento de casos
- Definir Acuerdos de Nivel de Servicio (SLAs) y medir su cumplimiento
- Establecer un sistema de feedback y mejora continua
- Preparar al estudiante para el examen de certificación MB-230

---

## 🗂️ Estructura del Proyecto

### Fase 1: Configuración Inicial (Seguridad y Datos Maestros)

#### 1. Usuarios del Sistema / Agentes (Users / Agents)

**Descripción:** Gestión de identidades (Microsoft Entra ID) asignadas a roles de seguridad y unidades de negocio dentro de Dynamics 365.

**Implementación:**
- **Portal:** Power Platform Admin Center / Microsoft 365 Admin Center / Power Apps Maker Portal
- **Ruta:** `Customer Service Admin Center > Support settings > Users`
- **Campos Estándar:** Full Name, Primary Email, Business Unit, Security Roles
- **Campos Personalizados:** Nivel de Especialización (Choice: Nivel 1, Nivel 2, VIP)

#### 2. Cuentas, Clientes y Contactos (Accounts & Contacts)

**Descripción:** Entidades relacionales que representan empresas (Accounts) y personas (Contacts) que interactúan con el servicio.

**Implementación:**
- **Portal:** Customer Service Workspace / Customer Service Admin Center
- **Ruta:** `Customer Service Admin Center > Customer settings > Accounts and contacts`
- **Campos Estándar:** Account Name, Primary Contact, Email, Phone
- **Campos Personalizados:** Segmento de Cliente (Enterprise, SMB), Nivel de Soporte Contratado (Gold, Silver)

---

### Fase 2: Operación y Enrutamiento (Casos y Colas)

#### 3. Colas (Queues) y Actividades

**Descripción:** Contenedores temporales donde se acumulan casos o actividades pendientes de ser atendidos por un equipo o agente.

**Implementación:**
- **Portal:** Customer Service Admin Center
- **Ruta:** `Customer Service Admin Center > Queues > Basic/Advanced queues > New`
- **Configuración:** Tipo (Public/Private), miembros (Users/Teams), Owner, Incoming Email
- **Campos Personalizados:** Canal de Origen (Email, Web, Teléfono)

#### 4. Casos (Cases / Incident Management)

**Descripción:** El registro central de un problema, incidencia o solicitud del cliente. Es el núcleo del examen MB-230.

**Implementación:**
- **Portal:** Customer Service Admin Center / Customer Service Workspace
- **Ruta:** `Customer Service Admin Center > Case settings > Case types / Parent and child cases`
- **Campos Estándar:** Title, Customer, Origin, Priority, Case Type, Description
- **Campos Personalizados:** Subcategoría de Error (Lookup), Impacto en Negocio

---

### Fase 3: Acuerdos y Cumplimiento (SLAs)

#### 5. Acuerdos de Nivel de Servicio (SLAs)

**Descripción:** Acuerdos formales que definen los tiempos límite de respuesta y resolución (First Response y Resolve By).

**Implementación:**
- **Portal:** Customer Service Admin Center
- **Ruta:** `Customer Service Admin Center > Service terms > Service Level Agreements (SLAs) > Manage`
- **Configuración:** Enhanced SLAs, SLA KPIs (First Response By / Resolve By)
- **Campos Estándar:** Name, Applicable When, Success Condition, Failure Condition
- **Campos Personalizados:** SLA Pausado por Cliente (Condición de pausa personalizada)

---

### Fase 4: Medición y Mejora Continua

#### 6. Encuestas de Satisfacción (Customer Voice / Feedback)

**Descripción:** Herramienta integrada para recopilar el feedback del cliente (CSAT / NPS) tras la resolución de un caso.

**Implementación:**
- **Portal:** Customer Service Admin Center / Dynamics 365 Customer Voice
- **Ruta:** `Customer Service Admin Center > Customer feedback > Survey settings > Manage`
- **Automatización:** Power Automate para disparo al resolver el caso
- **Campos Estándar:** Rating, Comments, Customer
- **Campos Personalizados:** Puntuación CSAT Global (Numérica del 1 al 5)

---

## 🛠️ Tecnologías y Herramientas

| Herramienta | Uso |
|-------------|-----|
| Microsoft Dynamics 365 Customer Service | Plataforma principal |
| Power Platform Admin Center | Gestión de entornos y usuarios |
| Power Apps Maker Portal | Configuración de seguridad |
| Power Automate | Automatización de encuestas |
| Dynamics 365 Customer Voice | Gestión de encuestas y feedback |
| Microsoft Entra ID | Gestión de identidades |

---

## 📚 Temario Cubierto (Examen MB-230)

- ✅ Configuración de usuarios y roles de seguridad
- ✅ Gestión de cuentas y contactos
- ✅ Creación y configuración de colas
- ✅ Gestión del ciclo de vida de casos
- ✅ Business Process Flows para casos
- ✅ Configuración de Enhanced SLAs
- ✅ KPIs de SLA y acciones automáticas
- ✅ Integración con Customer Voice
- ✅ Automatización de encuestas con Power Automate

---

## 🚀 Cómo Utilizar Este Repositorio

1. **Clona el repositorio** en tu máquina local
2. **Sigue las fases en orden** (Fase 1 → Fase 4)
3. **Implementa cada configuración** en tu entorno de prácticas
4. **Documenta tus resultados** y personalizaciones
5. **Utiliza los campos personalizados** como referencia para el examen

```bash
git clone https://github.com/tu-usuario/mb230-customer-service-project.git
