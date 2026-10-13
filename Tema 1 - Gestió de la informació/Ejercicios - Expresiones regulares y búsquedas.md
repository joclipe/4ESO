# Ejercicios: expresiones regulares y búsquedas en el navegador

Material de apoyo: [Guía - Expresiones regulares y búsqueda](Guía%20-%20Expresiones%20regulares%20y%20búsqueda.md).

## Parte A. Expresiones regulares

Para comprobar tus respuestas, usa la búsqueda con expresión regular de Visual Studio Code (VSCodium) (`Ctrl + Shift + F` o `Ctrl + F` con el botón `.*` activado) sobre un archivo que contenga la lista siguiente.

```text
2026-09-14_apuntes_redes.docx
2026-09-21_esquema_redes_v1.pdf
2026-09-28_esquema_redes_v2.pdf
2026-10-05_resumen_seguridad.pdf
2026-10-12_practica_permisos.docx
2026-11-02_examen_tema1.pdf
foto_clase_01.jpg
foto_clase_02.jpg
foto_clase_10.png
captura_pantalla.png
borrador_final.txt
notas.txt
presentacion_v3.pptx
Tema1.md
Tema2.md
Tema10.md
```

### A0. Comodines (Explorador de archivos)

Crea en una carpeta de prueba archivos vacíos con los nombres de la lista anterior y, en el buscador del Explorador, escribe `*.pdf`, `foto_*` y `*_v?.pdf`. Anota qué archivos aparecen en cada caso.

### A1. Nivel básico

Escribe un patrón que encuentre:

1. Todos los archivos `.pdf`.
2. Todos los archivos `.txt`.
3. Los archivos que empiezan por `foto`.
4. Los archivos que contienen la palabra `redes`.
5. Los archivos `.jpg` o `.png`.

### A2. Nivel medio

6. Los archivos que empiezan por una fecha con el formato `AAAA-MM-DD`.
7. Los archivos de octubre de 2026.
8. Los archivos con versión `v1` o `v2` antes de la extensión.
9. Las fotos numeradas con dos dígitos (`foto_clase_01.jpg`, `foto_clase_10.png`...), sea cual sea su extensión.
10. `Tema1.md` y `Tema2.md`, pero **no** `Tema10.md`.

### A3. Nivel avanzado

11. Los archivos de Word o PowerPoint (`.docx` o `.pptx`).
12. Los archivos que **no** empiezan por una fecha ni por `foto` (pista: puede ayudarte `^(?!...)`, pero también puedes resolverlo por partes).
13. Los archivos cuyo nombre tiene entre 10 y 20 caracteres antes de la extensión.
14. Explica con tus palabras qué hace cada uno de estos patrones y qué archivos encuentra:
    - a) `^\d{4}-1[0-1]-\d{2}_`
    - b) `_v\d\.`
    - c) `\.(md|txt)$`
    - d) `^[^_]+\.txt$`

### A4. Detectar errores

Cada patrón tiene un fallo. Encuéntralo y corrígelo.

| Objetivo | Patrón con error |
|---|---|
| Encontrar archivos PDF | `.pdf` |
| Encontrar archivos que empiezan por `foto` | `foto$` |
| Encontrar `Tema1.md` y `Tema2.md` | `Tema[1-2]*.md` |
| Encontrar fechas como `2026-10-05` | `\d{4}\d{2}\d{2}` |
| Encontrar `.jpg` o `.png` | `\.jpg\|png$` |

### A5. Crea tus propios patrones

15. Inventa **tres nombres de archivo** con un formato propio (por ejemplo, `curso_asignatura_numero.ext`).
16. Escribe un patrón que encuentre los tres.
17. Intercámbialo con un compañero. Cada uno debe explicar qué encuentra el patrón del otro y proponer un nombre de archivo que **no** debería coincidir.

## Parte B. Búsquedas en el navegador

Haz esta parte con **tres buscadores**: Google, Brave Search y DuckDuckGo. Anota en una tabla cuántos resultados útiles obtienes y qué cambia entre ellos.

> **Privacidad:** no escribas datos personales en las búsquedas. Algunos resultados pueden cambiar según tu ubicación e idioma.

### B1. Operadores básicos

1. Busca una frase exacta: `"copia de seguridad"`. ¿Qué cambia respecto a escribirla sin comillas?
2. Busca `redes` y después `redes -wifi`. Compara los resultados.
3. Busca `ciberseguridad filetype:pdf`. Abre uno de los resultados y comprueba que es un PDF.
4. Busca `calendario escolar site:gva.es`. ¿Todos los resultados pertenecen a ese sitio?
5. Busca `intitle:seguridad contraseñas` y comenta qué diferencia hay con buscar solo `seguridad contraseñas`.

### B2. Operadores específicos de cada buscador

6. **Google:** busca `inurl:tutorial regex`. ¿Qué tienen en común las direcciones de los resultados?
7. **Brave Search:** busca `manual ext:pdf` y después `visados lang:es`. Explica qué hace cada operador.
8. **DuckDuckGo:** busca `!w expresión regular` y después `\wikipedia`. Explica qué hace cada símbolo.
9. **DuckDuckGo:** busca algo con `!safeon` al final y comprueba cómo cambia la búsqueda.
10. Prueba el mismo operador en los tres buscadores. ¿En cuál funciona peor? Anota el ejemplo.

### B3. Combinar operadores

11. Encuentra un documento PDF de un sitio oficial sobre protección de datos con una sola búsqueda. Anota la búsqueda que usaste.
12. Encuentra una página que **no** sea de Wikipedia sobre «historia de los videojuegos». Anota la búsqueda.
13. Elige un tema de otra asignatura y escribe una búsqueda que combine **al menos tres** operadores. Explica por qué la formulaste así.

### B4. Buscar dentro del navegador

14. Abre una página larga y localiza una palabra con `Ctrl + F`. Activa la opción de coincidir mayúsculas y comprueba qué cambia (en Firefox).
15. Visita tres páginas y búscalas después en el historial con `Ctrl + H`.
16. **Firefox:** escribe `^ nombre` o `% nombre` en la barra de direcciones para buscar solo en el historial o en las pestañas abiertas.
17. **Chrome o Brave:** abre varias pestañas y localiza una con `Ctrl + Shift + A`.
18. Abre la lista de descargas (`Ctrl + J`, o `Ctrl + Shift + Y` en Firefox) y localiza el último archivo descargado.

### B5. Reto final

Tienes que encontrar **un manual en PDF de un programa de edición de imágenes** publicado en una web de una universidad, sin contar resultados de Wikipedia.

1. Escribe la búsqueda que usarías en cada buscador.
2. Compara los resultados.
3. Elige uno, comprueba que la fuente sea fiable y anota por qué la consideras fiable (quién la publica, fecha, etc.).

### Rúbrica orientativa

| Criterio | Muy bien | Bien | A mejorar |
|---|---|---|---|
| Uso de operadores | Combina varios y explica el resultado | Usa operadores simples | Solo escribe palabras sueltas |
| Comparación de buscadores | Detecta diferencias y las explica | Detecta diferencias | No compara |
| Evaluación de fuentes | Justifica la fiabilidad con datos | Comprueba la fuente | No la comprueba |
| Seguridad y privacidad | No usa datos personales y revisa los enlaces | Lo hace casi siempre | Introduce datos personales |

## Soluciones orientativas

### Parte A

| N.º | Patrón |
|---|---|
| 1 | `\.pdf$` |
| 2 | `\.txt$` |
| 3 | `^foto` |
| 4 | `redes` |
| 5 | `\.(jpg\|png)$` |
| 6 | `^\d{4}-\d{2}-\d{2}` |
| 7 | `^2026-10` |
| 8 | `_v[12]\.` |
| 9 | `_\d{2}\.` |
| 10 | `^Tema[12]\.md$` |
| 11 | `\.(docx\|pptx)$` |
| 12 | `^(?!\d{4}-\|foto)` |
| 13 | `^.{10,20}\.` |

- **14.** a) archivos de octubre o noviembre de 2026 con fecha al inicio y un guion bajo; b) archivos con una versión de un dígito (`v1`, `v2`, `v3`); c) archivos `.md` o `.txt`; d) archivos `.txt` sin ningún guion bajo en el nombre (`notas.txt`).
- **A4, errores:**
  - `.pdf`: el punto significa «cualquier carácter»; correcto: `\.pdf$`.
  - `foto$`: busca `foto` al **final**; correcto: `^foto`.
  - `Tema[1-2]*.md`: el `*` repite el dígito 0 o más veces y el punto es comodín; correcto: `^Tema[12]\.md$`.
  - `\d{4}\d{2}\d{2}`: faltan los guiones; correcto: `\d{4}-\d{2}-\d{2}`.
  - `\.jpg|png$`: la alternancia afecta a todo el patrón; correcto: `\.(jpg|png)$`.
- **12:** actividad con la opción de expresión regular activada; la pista `^(?!...)` es una exclusión al inicio y puede no funcionar en todos los programas.

### Parte B

Las respuestas dependen de los buscadores y de los resultados del momento. Una posible búsqueda para el reto B5 es `manual ext:pdf site:edu gimp`, adaptada a cada buscador.
- **B2.8:** `!w` lleva a la búsqueda en Wikipedia; `\` abre directamente el primer resultado.
- **B4.16:** `^` restringe al historial y `%` a las pestañas abiertas (Firefox).
