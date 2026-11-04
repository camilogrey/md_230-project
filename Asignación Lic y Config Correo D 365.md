# Guía Paso a Paso: Asignación de Licencias y Configuración de Correo en Dynamics 365

Esta guía documenta el proceso completo para preparar un entorno de prueba (Trial) de Dynamics 365 Customer Service. Abarca desde la asignación de licencias a los usuarios en Microsoft 365, hasta la habilitación y aprobación del buzón de correo electrónico en Dynamics 365.

## Requisitos Previos
*   Contar con permisos de **Administrador Global** o **Administrador de Dynamics 365**.
*   Tener un entorno de prueba (Trial) o de producción activo.

---

## Fase 1: Asignación de Licencias de Usuario (Microsoft 365)

**Paso 1: Acceder al Centro de Administración**
Desde la página principal de Microsoft, haz clic en el botón **"Centro de administración"** ubicado en la esquina superior derecha.
![Texto alternativo](licencia/1.%20verificar%20la%20creacion%20y%20y%20activacion%20de%20la%20cuenat.png)

**Paso 2: Navegar a Usuarios Activos**
En el menú de la izquierda, despliega la sección **"Usuarios"** y selecciona **"Usuarios activos"**. Aquí verás la lista de todos los usuarios de tu organización.

**Paso 3: Seleccionar el Usuario**
Busca y haz clic en el usuario al que deseas asignar licencias (en este ejemplo, el usuario **Camilo**).
![Texto alternativo](licencia/2.%20verificacion%20los%20usuarios%20activos%20en%20en%20centro%20de%20admin%20365.png)

**Paso 4: Asignar Licencias**
En el panel lateral que se abre, ve a la pestaña **"Licencias y aplicaciones"**. Asegúrate de seleccionar la ubicación (ej. España) y marca las casillas de las licencias que el usuario necesita. 
En este caso, se habilitan:
*   `Microsoft Teams Enterprise`
*   `Office 365 E5 (sin Teams)`

Finalmente, haz clic en **"Guardar cambios"** en la parte inferior.
![Texto alternativo](licencia/3.%20ver%20licencias%20y%20app%20de%20la%20cuenta%20activa.png)

![Texto alternativo](licencia/4.%20licencias%20activas.png)

---

## Fase 2: Acceso al Entorno de Power Platform

**Paso 5: Abrir el Centro de Administración de Power Platform**
Dirígete al **Centro de administración de Power Platform**.
En el menú izquierdo, selecciona **"Entornos"**. Localiza y haz clic en el entorno de prueba llamado **`CustomerService Trial`**.
![Texto alternativo](licencia/5.%20entramos%20al%20centro%20de%20admin%20de%20power%20pltaform%20para%20verificar%20la%20conexion%20del%20buzonmailbox.png)

**Paso 6: Obtener la URL del Entorno**
En la página de detalles del entorno, localiza y copia la **"URL de entorno"** (ej. `org6cc946bb.crm.dynamics.com`). Esta URL te servirá para acceder directamente a la aplicación de Dynamics.
![Texto alternativo](licencia/6.%20vemos%20que%20el%20entorno%20de%20tabajo%20esta%20activo.png)

![Texto alternativo](licencia/12.%20ingresamos%20a%20nuestro%20entorno%20de%20trabajo%20.png)

---

## Fase 3: Acceso a la Configuración de Dynamics 365

**Paso 7: Abrir la Aplicación**
Dentro de los detalles del entorno en Power Platform, haz clic en el menú desplegable **"Recursos"** y selecciona **"Aplicaciones de Dynamics 365"**.
![Texto alternativo](licencia/7.%20verificacios%20si%20en%20los%20recursos%20den%20entorno%20contamos%20con%20dynamos%20365%20app%20for%20outlook.png)

**Paso 8: Acceder a la Configuración**
Una vez dentro de la aplicación de Dynamics (o desde el menú superior de Power Platform), haz clic en el engranaje de **"Configuración"**.
![Texto alternativo](licencia/8.%20vamos%20a%20configuracion%20para%20formzar%20la%20isntalacionen%20el%20outlook%20la%20app%20dymanics%20365%20for%20outlook.png)

**Paso 9: Ir a Configuración de Correo**
En la página de configuración, despliega la sección **"Correo electrónico"** y haz clic en **"Configuración de correo electrónico"**.
![Texto alternativo](licencia/9.%20Vamos%20a%20configuracio%20de%20email.png)


---

## Fase 4: Aprobación del Buzón de Correo

**Paso 10: Seleccionar el Buzón**
Serás redirigido a la vista **"Mis buzones activos"**. Verás una lista con los buzones configurados. Marca la casilla de verificación del usuario correspondiente (ej. el buzón de *Camilo*).
![Texto alternativo](licencia/10.%20selccionamos%20el%20correo%20y%20lo%20aprobamos.png)


**Paso 11: Aprobar el Correo Electrónico**
Con el buzón seleccionado, haz clic en el botón **"Aprobar correo electr..."** (Aprobar correo electrónico) en la barra de herramientas superior.
![Texto alternativo](licencia/10.%20selccionamos%20el%20correo%20y%20lo%20aprobamos.png)


**Paso 12: Confirmar la Aprobación**
Aparecerá una ventana emergente indicando *"Aprobar correo electrónico principal"*. Lee el mensaje de confirmación sobre el intercambio de datos y haz clic en **"Aceptar"** (o el botón de confirmación). 
Espera unos segundos mientras el sistema actualiza el estado del buzón.
![Texto alternativo](licencia/11.%20porcede%20a%20aprovarl%20el%20correo.png)

---
**Nota Final:** Una vez completados estos pasos, el usuario tendrá las licencias correctas asignadas y su buzón de correo estará aprobado y listo para sincronizar correos, citas y contactos con Dynamics 365.