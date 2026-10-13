# 2.2.3. Guía: búsqueda avanzada de archivos y expresiones regulares

Cuando hay cientos de archivos, buscar por el nombre exacto no basta. Esta guía muestra cómo describir **patrones** para encontrar archivos en el ordenador y cómo buscar mejor desde el navegador.

## 1. ¿Qué es una expresión regular?

Una **expresión regular** (*regex*) es un texto formado por caracteres normales y símbolos especiales que describe un **patrón**. En lugar de buscar `informe1`, `informe2` e `informe3` por separado, se busca un patrón que los incluya a todos.

> **Importante:** el buscador del Explorador de archivos de Windows **no admite expresiones regulares completas**. Admite **comodines**, que son una versión más sencilla. Las expresiones regulares reales se usan en editores como Visual Studio Code, en PowerShell y en muchos lenguajes de programación.

## 2. Nivel 1: comodines (Explorador de archivos)

| Símbolo | Significado | Ejemplo | Encuentra |
|---|---|---|---|
| `*` | Cualquier número de caracteres | `*.pdf` | Todos los PDF |
| `?` | Exactamente un carácter | `tema?.docx` | `tema1.docx`, `temaA.docx` (no `tema10.docx`) |
| `*` combinado | Parte del nombre | `examen*` | `examen_mates.pdf`, `examen2.txt` |

Filtros propios del Explorador de Windows (escríbelos en el cuadro de búsqueda):

| Filtro | Ejemplo | Resultado |
|---|---|---|
| `tipo:` | `tipo:imagen` | Solo imágenes |
| `ext:` | `ext:pdf` | Solo archivos PDF |
| `modificado:` | `modificado:esta semana` | Archivos cambiados recientemente |
| `tamaño:` | `tamaño:grande` | Archivos grandes |
| `AND`, `OR`, `NOT` (en mayúsculas) | `redes NOT borrador` | Contienen «redes» pero no «borrador» |
| Comillas | `"esquema redes"` | La frase exacta |

> Los nombres de los filtros dependen del idioma del sistema. En Windows en inglés son `kind:`, `ext:`, `datemodified:` y `size:`.

**Ejemplo combinado:** `ext:pdf modificado:este mes redes` busca PDF de este mes que contengan «redes».

## 3. Nivel 2: expresiones regulares reales

### 3.1. Símbolos básicos

| Símbolo | Significado | Ejemplo |
|---|---|---|
| `.` | Cualquier carácter | `t.ma` → `tema`, `tima` |
| `*` | El carácter anterior se repite **0 o más** veces | `ab*` → `a`, `ab`, `abbb` |
| `+` | **1 o más** veces | `ab+` → `ab`, `abbb` |
| `?` | **0 o 1** vez (opcional) | `colou?r` → `color`, `colour` |
| `\d` | Un dígito (0-9) | `tema\d` → `tema1`, `tema7` |
| `\d{2}` | Exactamente 2 dígitos | `\d{2}` → `10`, `25` |
| `[abc]` | Uno de los caracteres indicados | `[ae]sto` → `asto`, `esto` |
| `[0-9]` | Un carácter de un rango | `nota[0-9]` |
| `[^abc]` | Cualquier carácter **excepto** esos | `[^0-9]` |
| `^` | Inicio de línea | `^Tema` |
| `$` | Final de línea | `\.pdf$` |
| `\.` | Un punto literal (la barra invertida «escapa» el símbolo) | `\.docx` |
| `a\|b` | «a» **o** «b» | `pdf\|docx` |
| `( )` | Agrupa partes del patrón | `(red\|web)es` |
| `\w` | Letra, número o guion bajo | `\w+` → `esquema_v1` |
| `\s` | Espacio en blanco | `esquema\sredes` |
| `{n,m}` | Entre *n* y *m* repeticiones | `\d{1,3}` → `7`, `42`, `120` |

> Las expresiones regulares tienen **variantes** según el programa (VS Code, PowerShell, Python...). Los símbolos de esta tabla funcionan en casi todas. Además, algunas distinguen mayúsculas de minúsculas y otras no: en VS Code se controla con el botón `Aa`, y en PowerShell `-match` no las distingue (`-cmatch` sí).

### 3.2. Ejemplos con nombres de archivo

Supón que tienes estos archivos:

```text
2026-10-12_esquema_redes_v1.pdf
2026-10-15_esquema_redes_v2.pdf
2026-11-03_apuntes_seguridad.docx
foto_excursion_01.jpg
foto_excursion_02.jpg
borrador_final.txt
```

| Objetivo | Patrón | Encuentra |
|---|---|---|
| Archivos que empiezan por una fecha | `^\d{4}-\d{2}-\d{2}` | Los tres primeros |
| Solo los PDF | `\.pdf$` | Los dos esquemas |
| PDF o Word | `\.(pdf\|docx)$` | Los tres primeros |
| Versiones 1 o 2 | `_v[12]\.` | Los dos esquemas |
| Fotos numeradas | `foto_.*_\d{2}\.jpg` | Las dos fotos |
| Archivos de octubre de 2026 | `^2026-10` | Los dos esquemas |

### 3.3. Dónde probarlas

- **Visual Studio Code:** pulsa `Ctrl + Shift + F` (buscar en archivos) y activa el botón `.*` (**Usar expresión regular**, atajo `Alt + R`). Busca dentro del **contenido** de los archivos.
- **PowerShell:** para filtrar archivos por nombre.

  ```powershell
  Get-ChildItem -Recurse | Where-Object { $_.Name -match '^\d{4}-\d{2}-\d{2}.*\.pdf$' }
  ```

- **Símbolo del sistema (CMD):** `dir /s *.pdf` lista los PDF de una carpeta y sus subcarpetas (solo admite comodines `*` y `?`).
- **Herramientas en línea** como regex101.com permiten probar el patrón y ver qué coincide. No pegues en ellas datos personales ni documentos privados.

### 3.4. Errores frecuentes

- Olvidar escapar el punto: `.pdf` encuentra también `xpdf`; usa `\.pdf`.
- Confundir comodines con regex: `*.pdf` es un comodín; en regex sería `.*\.pdf`.
- Patrones demasiado generales: `.*` coincide con casi todo. Empieza por un patrón concreto y amplíalo.
- Probar sin comprobar los resultados: revisa siempre la lista antes de **borrar o mover** archivos.

## 4. Buscar desde el navegador

Los navegadores **no usan expresiones regulares** al buscar (ni en la página con `Ctrl + F` ni en el historial), pero ofrecen operadores y atajos muy útiles para recuperar información, por ejemplo una página visitada o un documento publicado en Internet.

### 4.1. Operadores de búsqueda

Los operadores dependen del **buscador** (Google, Brave Search, DuckDuckGo, etc.), no del navegador: puedes usar Google en Firefox o DuckDuckGo en Chrome. DuckDuckGo tiene su propia sección más abajo (4.1.1).

**Comunes a Google y Brave Search:**

| Operador | Ejemplo | Resultado |
|---|---|---|
| `" "` | `"seguridad de la información"` | La frase exacta |
| `-` | `redes -wifi` | Excluye resultados con «wifi» |
| `site:` | `site:gva.es calendario` | Solo resultados de ese sitio |
| `filetype:` | `filetype:pdf ciberseguridad` | Solo archivos de ese tipo |
| `intitle:` | `intitle:regex guía` | La palabra aparece en el título |
| `OR` (mayúsculas) | `copia OR respaldo` | Cualquiera de los dos términos |

**Solo Google (entre otros):**

| Operador | Ejemplo | Resultado |
|---|---|---|
| `inurl:` | `inurl:tutorial` | La palabra aparece en la dirección |
| `*` | `"copia de * archivos"` | Comodín para una palabra desconocida |
| `..` | `portátil 400..600` | Intervalo numérico |
| `ext:` | `logotipo ext:png` | Equivale a `filetype:` (por ejemplo, `ext:png`, `ext:pdf`) |
| `intext:` | `intext:"copia de seguridad"` | El término aparece en el texto de la página |
| `allintitle:` | `allintitle:copia seguridad` | Todos los términos aparecen en el título |
| `before:` / `after:` | `ciberseguridad after:2025-01-01` | Páginas anteriores o posteriores a una fecha |
| `define:` | `define:backup` | Definición de una palabra |
| `AROUND(n)` | `copia AROUND(3) seguridad` | Dos términos separados por como máximo *n* palabras |

> **Sobre los corchetes:** `[png]` **no** es un operador de Google. Para filtrar por extensión se usa `filetype:png` o `ext:png`. Si se escribe entre corchetes o comillas, Google busca esa palabra como texto, no como tipo de archivo. Los corchetes tampoco filtran en Brave Search ni en DuckDuckGo.

**Solo Brave Search:**

| Operador | Ejemplo | Resultado |
|---|---|---|
| `ext:` | `manual ext:pdf` | Páginas con esa extensión |
| `inbody:` | `inbody:"copia de seguridad"` | El término está en el cuerpo de la página |
| `inpage:` | `inpage:regex` | El término está en el título o en el cuerpo |
| `lang:` | `visados lang:es` | Páginas en ese idioma (código de dos letras) |
| `loc:` | `cataratas loc:ca` | Páginas de ese país o región |
| `+` | `gpu +freesync` | Obliga a que el término aparezca |
| `AND`, `OR`, `NOT` | `redes NOT site:wikipedia.org` | Combinan condiciones |

> Los operadores se escriben **sin espacio** después de los dos puntos. Brave indica en su ayuda que sus operadores son **experimentales**, y el funcionamiento de ambos buscadores puede cambiar con el tiempo; si un operador no da resultados, pruébalo en otro buscador.

### 4.1.1. DuckDuckGo

DuckDuckGo es un buscador que no rastrea las búsquedas de sus usuarios. Admite estos operadores:

| Operador | Ejemplo | Resultado |
|---|---|---|
| `" "` | `"copia de seguridad"` | La frase exacta |
| `~" "` | `~"copia de seguridad"` | Experimental: también resultados de significado parecido |
| `-` | `redes -wifi` | Menos resultados con ese término |
| `+` | `redes +seguridad` | Más resultados con ese término |
| `filetype:` | `ciberseguridad filetype:pdf` | Solo ese tipo de archivo (pdf, doc(x), xls(x), ppt(x), html) |
| `site:` | `calendario site:gva.es` | Solo resultados de ese sitio |
| `-site:` | `redes -site:wikipedia.org` | Excluye un sitio |
| `intitle:` | `intitle:regex` | La palabra está en el título |
| `inurl:` | `inurl:tutorial` | La palabra está en la dirección |
| `\` | `\futurama` | Va directamente al primer resultado |
| `!safeon` / `!safeoff` | `ciencia !safeon` | Activa o desactiva la búsqueda segura solo en esa búsqueda |

**Bangs (`!`):** atajos para buscar directamente en otra web. Por ejemplo, `!w filtro burbuja` busca en Wikipedia y `!a portátil` en Amazon. Ten en cuenta que la búsqueda se hace en **esa otra web**, y se aplican sus políticas de datos.

> DuckDuckGo indica que parte de su sintaxis avanzada puede no funcionar al 100 % en todas las búsquedas. Si no hay resultados, muestra resultados relacionados.

### 4.1.2. Filtrar por tipo de archivo y extensión

| Buscador | Operador | Ejemplo | Notas |
|---|---|---|---|
| Google | `filetype:` o `ext:` | `esquema redes ext:png` | Admite muchos tipos (pdf, docx, xlsx, pptx, png, jpg...) |
| Brave Search | `filetype:` o `ext:` | `esquema redes ext:pdf` | Operadores experimentales |
| DuckDuckGo | `filetype:` | `esquema redes filetype:pdf` | Tipos admitidos: pdf, doc(x), xls(x), ppt(x), html; **no** imágenes |

Para **imágenes**, además de `ext:png`, los buscadores ofrecen filtros en la pestaña **Imágenes**: tamaño, color, tipo (foto, ilustración, GIF...) y licencia de uso. En Google se encuentran en **Herramientas**; en Brave y DuckDuckGo, en la barra de filtros situada sobre los resultados. Los nombres y la posición pueden cambiar.

> Antes de reutilizar una imagen o un documento, comprueba su **licencia** y cita la fuente.

### 4.2. Google Chrome

- **Buscar en la página:** `Ctrl + F`.
- **Historial:** `Ctrl + H` y escribe en el cuadro de búsqueda; también puedes ir a `chrome://history`.
- **Buscar entre las pestañas abiertas:** `Ctrl + Shift + A`.
- **Atajos en la barra de direcciones:** escribe `@historial`, `@marcadores` o `@pestañas` y pulsa `Tab` para buscar solo en ese ámbito (el nombre puede variar según el idioma).
- **Administrador de marcadores:** `Ctrl + Shift + O`.
- **Descargas:** `Ctrl + J` muestra y permite buscar los archivos descargados.

### 4.3. Mozilla Firefox

- **Buscar en la página:** `Ctrl + F`; las opciones permiten coincidir mayúsculas y palabras completas.
- **Historial:** `Ctrl + H` abre la barra lateral con buscador; `Ctrl + Shift + H` abre la biblioteca.
- **Marcadores:** `Ctrl + Shift + O` abre la biblioteca de marcadores con buscador.
- **Símbolos de restricción en la barra de direcciones** (escríbelos seguidos de un espacio y el término; pueden cambiar según la versión de Firefox):

  | Símbolo | Busca en |
  |---|---|
  | `*` | Marcadores |
  | `^` | Historial |
  | `%` | Pestañas abiertas |
  | `#` | Títulos de página |
  | `$` | Direcciones (URL) |

  Ejemplo: `^ redes` busca «redes» solo en el historial.
- **Descargas:** `Ctrl + Shift + Y`.

### 4.4. Brave

Brave está basado en Chromium, por lo que comparte muchos atajos con Chrome.

- **Buscar en la página:** `Ctrl + F`.
- **Historial:** `Ctrl + H`.
- **Buscar entre las pestañas abiertas:** `Ctrl + Shift + A`.
- **Marcadores:** `Ctrl + Shift + O`.
- **Descargas:** `Ctrl + J`.
- **Buscador:** Brave usa Brave Search por defecto (operadores en el apartado 4.1). El buscador predeterminado se cambia en `brave://settings/search`.
- **Bangs:** en Brave Search, escribir `!w` seguido de un término lleva directamente a Wikipedia (ver la ayuda de Brave Search sobre *bangs*).

### 4.5. Comparativa rápida

| Acción | Chrome | Firefox | Brave |
|---|---|---|---|
| Buscar en la página | `Ctrl + F` | `Ctrl + F` | `Ctrl + F` |
| Historial | `Ctrl + H` | `Ctrl + H` | `Ctrl + H` |
| Marcadores | `Ctrl + Shift + O` | `Ctrl + Shift + O` | `Ctrl + Shift + O` |
| Descargas | `Ctrl + J` | `Ctrl + Shift + Y` | `Ctrl + J` |
| Buscar pestañas | `Ctrl + Shift + A` | `%` en la barra | `Ctrl + Shift + A` |
| Expresiones regulares | No | No | No |

## 5. Practica

Los ejercicios de esta guía, con sus soluciones, están en [Ejercicios - Expresiones regulares y búsquedas](Ejercicios%20-%20Expresiones%20regulares%20y%20búsquedas.md).
