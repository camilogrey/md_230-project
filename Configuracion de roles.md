# Laboratorio: Configuración de Roles, Equipos y Unidades de Negocio en Power Platform Admin Center

En este laboratorio, realicé la configuración de usuarios, la asignación de roles de seguridad, la revisión de equipos y la estructura de unidades de negocio dentro del entorno `3618-GameOfCodes` en el centro de administración de Power Platform.

## 1. Acceso a la configuración del entorno

**1.1.** Ingresé al centro de administración de Power Platform y en el menú lateral izquierdo seleccioné la opción **Administrar** y luego **Entornos**.

**1.2.** Seleccioné el entorno específico denominado `3618-GameOfCodes`.

**1.3.** Una vez dentro del entorno, hice clic en la pestaña **Configuración** en el menú superior.

![Acceso a configuración del entorno](roles/21.%20Configuracion%20PP%20admin.png)

## 2. Gestión de usuarios y asignación de roles

**2.1.** Dentro de la sección de Configuración, navegué por el menú de la izquierda hasta **Usuarios y permisos** y seleccioné **Usuarios**.

![Menú de usuarios y permisos](roles/22.%20Usuarios%20y%20permisos.png)

**2.2.** En la lista de usuarios del entorno, localicé y seleccioné al usuario **Camilo Andrés García Rey**.

![Lista de usuarios del entorno](roles/23.%20usuario.png)

**2.3.** Se abrió un panel lateral con los detalles del usuario. En la sección de **Roles asignados directamente**, hice clic en el enlace **Administrar roles**.

![Detalles del usuario](roles/24.%20Admin%20Roles.png)

**2.4.** Se desplegó la ventana **Administrar roles de seguridad**, donde pude visualizar la lista completa de roles disponibles para la unidad de negocio `3618-gameofcodes`. Desde aquí se pueden marcar o desmarcar los roles que se le asignarán al usuario.

![Administrar roles de seguridad](roles/25.%20roles%20disponibles.png)

## 3. Revisión de equipos

**3.1.** De vuelta en el menú de **Usuarios y permisos**, seleccioné la opción **Equipos**.

![Menú de equipos y unidades de negocio](roles/26.%20config%20equipos%20y%20unidades%20de%20negocio.png)

**3.2.** En la lista de equipos disponibles, localicé y seleccioné el equipo llamado **CG Equipo propio**.

![Lista de equipos](roles/27.%20creacion%20de%20equipo%20propio.png)

**3.3.** Se abrió la vista de detalles del equipo, donde pude verificar su información general, incluyendo la unidad de negocio a la que pertenece (`3618-gameofcodes`), el administrador (Equipo Gameof Codes), el tipo de equipo (Propietario) y la sección de miembros del equipo (Team members), la cual se encontraba vacía en ese momento.

![Detalles del equipo](roles/28.%20config%20de%20equipo.png)

## 4. Revisión de unidades de negocio

**4.1.** Finalmente, en el menú de **Usuarios y permisos**, hice clic en **Unidades de negocio**.

**4.2.** Se desplegó la lista de unidades de negocio activas, donde pude observar la jerarquía y estructura de la organización. La unidad principal es `3618-gameofcodes`, de la cual dependen otras unidades como `Externos`, `FP`, `Masters` y `Tajamar`.

![Lista de unidades de negocio](roles/29.%20Creacion%20de%20unidades%20de%20negocio.png)