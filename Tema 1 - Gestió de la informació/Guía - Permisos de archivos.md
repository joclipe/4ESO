# 2.2.4. Guía: permisos de archivos y carpetas

Los **permisos** determinan **quién** puede hacer **qué** con un archivo o una carpeta. Son una parte básica de la seguridad: protegen la **confidencialidad** (no todo el mundo puede leer), la **integridad** (no todo el mundo puede modificar) y la **disponibilidad** (quien lo necesita puede acceder).

## 1. Conceptos básicos

- **Usuario:** persona o cuenta que usa el sistema (por ejemplo, `alumno`).
- **Grupo:** conjunto de usuarios con los mismos derechos (por ejemplo, `Alumnado` o `Profesorado`).
- **Propietario:** usuario que creó el archivo o que tiene el control principal sobre él.
- **Permiso:** autorización para realizar una acción sobre un archivo o una carpeta.
- **Principio del mínimo privilegio:** cada persona debe tener **solo los permisos que necesita**, y no más.

### Tipos de permisos más habituales

| Permiso | En un archivo | En una carpeta |
|---|---|---|
| **Lectura** | Ver su contenido | Ver qué contiene |
| **Escritura / modificación** | Cambiar su contenido | Crear, renombrar o borrar elementos dentro |
| **Ejecución** | Ejecutarlo si es un programa o script | Entrar en la carpeta y acceder a su contenido |

## 2. Permisos en Linux (LliureX) y macOS

LliureX está basado en Ubuntu, así que usa el modelo de permisos de Linux: un modelo sencillo con tres categorías y tres permisos. macOS usa un modelo muy parecido.

### 2.1. Categorías y permisos

- **Categorías:** propietario (`u`), grupo (`g`) y otros (`o`).
- **Permisos:** lectura (`r`), escritura (`w`) y ejecución (`x`).

Al ejecutar `ls -l` se obtiene algo así:

```text
-rwxr-xr--  1 ana  clase  2048  oct 12 10:30  script.sh
```

| Parte | Significado |
|---|---|
| `-` | Tipo (`-` archivo, `d` carpeta) |
| `rwx` | El propietario puede leer, escribir y ejecutar |
| `r-x` | El grupo puede leer y ejecutar, pero no escribir |
| `r--` | Los demás solo pueden leer |

### 2.2. Notación numérica

Cada permiso vale un número: `r = 4`, `w = 2`, `x = 1`. Se suman por categoría.

| Número | Permisos | Significado |
|---|---|---|
| `7` | `rwx` | Todo |
| `6` | `rw-` | Leer y escribir |
| `5` | `r-x` | Leer y ejecutar |
| `4` | `r--` | Solo leer |
| `0` | `---` | Ninguno |

Ejemplo: `chmod 640 notas.txt` da lectura y escritura al propietario (`6`), solo lectura al grupo (`4`) y ningún permiso a los demás (`0`).

### 2.3. Comandos útiles

| Comando | Para qué sirve | Ejemplo |
|---|---|---|
| `ls -l` | Ver permisos | `ls -l informe.txt` |
| `chmod` | Cambiar permisos | `chmod u+x script.sh` (añade ejecución al propietario) |
| `chown` | Cambiar propietario (requiere administrador) | `sudo chown ana:clase notas.txt` |

> En una **carpeta**, el permiso `x` es necesario para entrar en ella. Sin `x` no se puede acceder a lo que contiene, aunque se tenga `r`.

### 2.4. Desde el gestor de archivos

En LliureX, haz clic derecho sobre un archivo o una carpeta y elige **Propiedades**; en la pestaña **Permisos** se ven el propietario, el grupo y los permisos de cada categoría, y se pueden cambiar si eres el propietario. Los nombres exactos pueden variar según el entorno de escritorio.

En macOS se consultan desde el Finder: **Obtener información** > **Compartir y permisos**.

> No cambies permisos de carpetas del sistema y evita `chmod 777`: deja el archivo accesible y modificable por cualquiera.

## 3. Permisos en Windows

Windows usa listas de control de acceso (ACL) con permisos más detallados.

### 3.1. Usuarios y grupos habituales

| Nombre | Qué es |
|---|---|
| **Administradores** | Control total del equipo |
| **Usuarios** | Cuentas estándar; pueden usar el equipo pero no cambiar el sistema |
| **SYSTEM** | Cuenta interna que usa Windows para sus propios servicios |
| **Todos** (*Everyone*) | Cualquier persona, incluidas las que no tienen cuenta propia; evita darle permisos de escritura |

### 3.2. Ver los permisos de un archivo o carpeta

1. Haz clic derecho sobre el elemento y elige **Propiedades**.
2. Abre la pestaña **Seguridad**.
3. Selecciona un usuario o grupo de la lista y consulta los permisos que tiene.

> Si no aparece la pestaña **Seguridad**, puede que el elemento esté en una unidad con un sistema de archivos que no la admite (como FAT32 o exFAT) o que tu cuenta no tenga acceso.

### 3.3. Permisos principales

| Permiso | Qué permite |
|---|---|
| **Control total** | Hacer todo, incluido cambiar los permisos |
| **Modificar** | Leer, cambiar y eliminar |
| **Lectura y ejecución** | Ver y ejecutar, sin cambiar |
| **Mostrar el contenido de la carpeta** | Ver la lista de elementos (solo carpetas) |
| **Lectura** | Ver contenido y propiedades |
| **Escritura** | Crear y modificar archivos |

Cada permiso puede estar en **Permitir** o **Denegar**. **Denegar tiene prioridad sobre Permitir**, así que conviene usarlo con cuidado.

### 3.4. Cambiar permisos

Solo puede hacerlo el propietario, un administrador o quien tenga *Control total*.

1. **Propiedades > Seguridad > Editar**.
2. Elige un usuario o grupo, o pulsa **Agregar** para incluir otro.
3. Marca o desmarca los permisos y pulsa **Aplicar**.

> Cambiar permisos en carpetas del sistema (como `C:\Windows`) puede impedir que el equipo funcione correctamente. No modifiques lo que no reconozcas.

### 3.5. Herencia

Por defecto, los archivos **heredan** los permisos de la carpeta que los contiene. Si cambias los permisos de una carpeta, lo normal es que se apliquen a todo lo que hay dentro. Puede deshabilitarse desde **Opciones avanzadas**, pero conviene evitarlo salvo que sea necesario.

En **Opciones avanzadas** también se puede ver el **propietario** del elemento y consultar el **acceso efectivo** de un usuario concreto.

### 3.6. Desde la línea de comandos

```powershell
# Ver los permisos de una carpeta
icacls "C:\Users\alumno\Documentos\Proyecto"
```

El comando `icacls` también permite modificarlos, pero un error puede dejarte sin acceso. Practica solo en carpetas de prueba.

## 4. Permisos al compartir en la nube

Servicios como Google Drive, OneDrive o Moodle suelen usar estos niveles:

| Nivel | Qué puede hacer la persona |
|---|---|
| **Lector / Solo lectura** | Ver (y a veces descargar) |
| **Comentarista** | Ver y comentar |
| **Editor** | Modificar el contenido |
| **Propietario** | Controlar permisos y eliminar el archivo |

Buenas prácticas:

- **Comparte con personas concretas** en lugar de usar «cualquiera con el enlace», salvo que el contenido sea público.
- **Elige el nivel más bajo que sirva:** si solo tiene que leer, dale permiso de lectura.
- **Revisa periódicamente** con quién has compartido cada archivo y retira accesos que ya no hagan falta.
- **Pon fecha de caducidad** al acceso cuando el servicio lo permita.
- **Desactiva la descarga o la copia** de documentos delicados si la opción está disponible.
- **Ten en cuenta que un editor puede borrar o estropear el trabajo:** conserva copias y activa el historial de versiones.

## 5. Buenas prácticas generales

1. Aplica el **mínimo privilegio**.
2. Asigna permisos a **grupos** en lugar de a personas una a una: es más fácil de mantener.
3. No uses una cuenta de **administrador** para el trabajo diario.
4. Revisa los permisos cuando cambian los equipos de trabajo o termina un proyecto.
5. No des «Control total» ni permisos `777` para «arreglar» un error de acceso: es una solución insegura.
6. Los permisos **no sustituyen** a las copias de seguridad ni al cifrado: protegen el acceso, no evitan pérdidas por fallo o borrado. Además, quien tenga acceso físico al dispositivo o sea administrador puede saltarse algunos permisos si el contenido no está cifrado.
7. Documenta quién tiene acceso a qué, sobre todo en carpetas compartidas del centro o de un equipo.

## 6. Practica

Las actividades de esta guía, con sus soluciones, están en [Ejercicios - Permisos de archivos](Ejercicios%20-%20Permisos%20de%20archivos.md).
