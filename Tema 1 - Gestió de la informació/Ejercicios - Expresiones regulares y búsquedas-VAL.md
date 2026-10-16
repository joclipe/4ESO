# Exercicis: expressions regulars i cerques en el navegador

Material de suport: [Guia - Expressions regulars i cerca](Guía%20-%20Expresiones%20regulares%20y%20búsqueda-VAL.md).

## Part A. Expressions regulars

Per a comprovar les respostes, utilitza la cerca amb expressió regular de Visual Studio Code (VSCodium) (`Ctrl + Shift + F` o `Ctrl + F` amb el botó `.*` activat) sobre un arxiu que continga la llista següent.

```text
2026-09-14_apunts_xarxes.docx
2026-09-21_esquema_xarxes_v1.pdf
2026-09-28_esquema_xarxes_v2.pdf
2026-10-05_resum_seguretat.pdf
2026-10-12_practica_permisos.docx
2026-11-02_examen_tema1.pdf
foto_classe_01.jpg
foto_classe_02.jpg
foto_classe_10.png
captura_pantalla.png
esborrany_final.txt
notes.txt
presentacio_v3.pptx
Tema1.md
Tema2.md
Tema10.md


### A1. Nivell bàsic

Escriu un patró que trobe:

1. Tots els arxius `.pdf`.
2. Tots els arxius `.txt`.
3. Els arxius que comencen per `foto`.
4. Els arxius que contenen la paraula `xarxes`.
5. Els arxius `.jpg` o `.png`.

### A2. Nivell mitjà

6. Els arxius que comencen per una data amb el format `AAAA-MM-DD`.
7. Els arxius d'octubre de 2026.
8. Els arxius amb versió `v1` o `v2` abans de l'extensió.
9. Les fotos numerades amb dos dígits (`foto_classe_01.jpg`, `foto_classe_10.png`...), siga quina siga l'extensió.
10. `Tema1.md` i `Tema2.md`, però **no** `Tema10.md`.

### A3. Nivell avançat

11. Els arxius de Word o PowerPoint (`.docx` o `.pptx`).
12. Els arxius que **no** comencen per una data ni per `foto` (pista: et pot ajudar `^(?!...)`, però també pots resoldre-ho per parts).
13. Els arxius el nom dels quals té entre 10 i 20 caràcters abans de l'extensió.
14. Explica amb les teues paraules què fa cadascun d'estos patrons i quins arxius troba:
    - a) `^\d{4}-1[0-1]-\d{2}_`
    - b) `_v\d\.`
    - c) `\.(md|txt)$`
    - d) `^[^_]+\.txt$`

### A4. Detectar errors

Cada patró té una errada. Troba-la i corregix-la.

| Objectiu | Patró amb error |
|---|---|
| Trobar arxius PDF | `.pdf` |
| Trobar arxius que comencen per `foto` | `foto$` |
| Trobar `Tema1.md` i `Tema2.md` | `Tema[1-2]*.md` |
| Trobar dates com `2026-10-05` | `\d{4}\d{2}\d{2}` |
| Trobar `.jpg` o `.png` | `\.jpg\|png$` |

### A5. Crea els teus propis patrons

15. Inventa **tres noms d'arxiu** amb un format propi (per exemple, `curs_assignatura_numero.ext`).
16. Escriu un patró que els trobe tots tres.
17. Intercanvia'l amb un company o companya. Cadascú ha d'explicar què troba el patró de l'altre i proposar un nom d'arxiu que **no** hauria de coincidir.

## Part B. Cerques en el navegador

Fes esta part amb **tres buscadors**: Google, Brave Search i DuckDuckGo. Anota en una taula quants resultats útils obtens i què canvia entre ells.

> **Privacitat:** no escrigues dades personals en les cerques. Alguns resultats poden canviar segons la teua ubicació i idioma.

### B1. Operadors bàsics

1. Busca una frase exacta: `"còpia de seguretat"`. Què canvia respecte a escriure-la sense cometes?
2. Busca `xarxes` i després `xarxes -wifi`. Compara els resultats.
3. Busca `ciberseguretat filetype:pdf`. Obri un dels resultats i comprova que és un PDF.
4. Busca `calendari escolar site:gva.es`. Tots els resultats pertanyen a eixe lloc?
5. Busca `intitle:seguretat contrasenyes` i comenta quina diferència hi ha amb buscar només `seguretat contrasenyes`.

### B2. Operadors específics de cada buscador

6. **Google:** busca `inurl:tutorial regex`. Què tenen en comú les adreces dels resultats?
7. **Brave Search:** busca `manual ext:pdf` i després `visats lang:es`. Explica què fa cada operador.
8. **DuckDuckGo:** busca `!w expressió regular` i després `\wikipedia`. Explica què fa cada símbol.
9. **DuckDuckGo:** busca alguna cosa amb `!safeon` al final i comprova com canvia la cerca.
10. Prova el mateix operador en els tres buscadors. En quin funciona pitjor? Anota l'exemple.

### B3. Combinar operadors

11. Troba un document PDF d'un lloc oficial sobre protecció de dades amb una sola cerca. Anota la cerca que has utilitzat.
12. Troba una pàgina que **no** siga de Wikipedia sobre «història dels videojocs». Anota la cerca.
13. Tria un tema d'una altra assignatura i escriu una cerca que combine **almenys tres** operadors. Explica per què l'has formulada així.

### B4. Buscar dins del navegador

14. Obri una pàgina llarga i localitza una paraula amb `Ctrl + F`. Activa l'opció de coincidir majúscules i comprova què canvia (en Firefox).
15. Visita tres pàgines i busca-les després a l'historial amb `Ctrl + H`.
16. **Firefox:** escriu `^ nom` o `% nom` a la barra d'adreces per a buscar només a l'historial o a les pestanyes obertes.
17. **Chrome o Brave:** obri diverses pestanyes i localitza'n una amb `Ctrl + Shift + A`.
18. Obri la llista de descàrregues (`Ctrl + J`, o `Ctrl + Shift + Y` en Firefox) i localitza l'últim arxiu descarregat.

### B5. Repte final

Has de trobar **un manual en PDF d'un programa d'edició d'imatges** publicat en un web d'una universitat, sense comptar els resultats de Wikipedia.

1. Escriu la cerca que utilitzaries en cada buscador.
2. Compara els resultats.
3. Tria'n un, comprova que la font siga fiable i anota per què la consideres fiable (qui la publica, data, etc.).

### Rúbrica orientativa

| Criteri | Molt bé | Bé | A millorar |
|---|---|---|---|
| Ús d'operadors | En combina diversos i explica el resultat | Utilitza operadors simples | Només escriu paraules soltes |
| Comparació de buscadors | Detecta diferències i les explica | Detecta diferències | No compara |
| Avaluació de fonts | Justifica la fiabilitat amb dades | Comprova la font | No la comprova |
| Seguretat i privacitat | No utilitza dades personals i revisa els enllaços | Ho fa quasi sempre | Introduïx dades personals |

## Solucions orientatives

### Part A

| N.º | Patró |
|---|---|
| 1 | `\.pdf$` |
| 2 | `\.txt$` |
| 3 | `^foto` |
| 4 | `xarxes` |
| 5 | `\.(jpg\|png)$` |
| 6 | `^\d{4}-\d{2}-\d{2}` |
| 7 | `^2026-10` |
| 8 | `_v[12]\.` |
| 9 | `_\d{2}\.` |
| 10 | `^Tema[12]\.md$` |
| 11 | `\.(docx\|pptx)$` |
| 12 | `^(?!\d{4}-\|foto)` |
| 13 | `^.{10,20}\.` |

- **14.** a) arxius d'octubre o novembre de 2026 amb data a l'inici i un guió baix; b) arxius amb una versió d'un dígit (`v1`, `v2`, `v3`); c) arxius `.md` o `.txt`; d) arxius `.txt` sense cap guió baix en el nom (`notes.txt`).
- **A4, errors:**
  - `.pdf`: el punt significa «qualsevol caràcter»; correcte: `\.pdf$`.
  - `foto$`: busca `foto` al **final**; correcte: `^foto`.
  - `Tema[1-2]*.md`: l'`*` repetix el dígit 0 o més vegades i el punt és comodí; correcte: `^Tema[12]\.md$`.
  - `\d{4}\d{2}\d{2}`: falten els guions; correcte: `\d{4}-\d{2}-\d{2}`.
  - `\.jpg|png$`: l'alternança afecta tot el patró; correcte: `\.(jpg|png)$`.
- **12:** activitat amb l'opció d'expressió regular activada; la pista `^(?!...)` és una exclusió a l'inici i pot no funcionar en tots els programes.

### Part B

Les respostes depenen dels buscadors i dels resultats del moment. Una possible cerca per al repte B5 és `manual ext:pdf site:edu gimp`, adaptada a cada buscador.
- **B2.8:** `!w` porta a la cerca a Wikipedia; `\` obri directament el primer resultat.
- **B4.16:** `^` restringix a l'historial i `%` a les pestanyes obertes (Firefox).
