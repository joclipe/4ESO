# 2.2.3. Guia: cerca avançada d'arxius i expressions regulars

Quan hi ha centenars d'arxius, buscar pel nom exacte no basta. Esta guia mostra com descriure **patrons** per a trobar arxius a l'ordinador i com buscar millor des del navegador.

## 1. Què és una expressió regular?

Una **expressió regular** (*regex*) és un text format per caràcters normals i símbols especials que descriu un **patró**. En lloc de buscar `informe1`, `informe2` i `informe3` per separat, es busca un patró que els incloga tots.

> **Important:** el buscador de l'Explorador d'arxius de Windows **no admet expressions regulars completes**. Admet **comodins**, que són una versió més senzilla. Les expressions regulars reals s'utilitzen en editors com Visual Studio Code, en PowerShell i en molts llenguatges de programació.

## 2. Nivell 1: comodins (Explorador d'arxius)

| Símbol | Significat | Exemple | Troba |
|---|---|---|---|
| `*` | Qualsevol nombre de caràcters | `*.pdf` | Tots els PDF |
| `?` | Exactament un caràcter | `tema?.docx` | `tema1.docx`, `temaA.docx` (no `tema10.docx`) |
| `*` combinat | Part del nom | `examen*` | `examen_mates.pdf`, `examen2.txt` |

Filtres propis de l'Explorador de Windows (escriu-los al quadre de cerca):

| Filtre | Exemple | Resultat |
|---|---|---|
| `tipus:` | `tipus:imatge` | Només imatges |
| `ext:` | `ext:pdf` | Només arxius PDF |
| `modificat:` | `modificat:esta setmana` | Arxius canviats recentment |
| `mida:` | `mida:gran` | Arxius grans |
| `AND`, `OR`, `NOT` (en majúscules) | `xarxes NOT esborrany` | Contenen «xarxes» però no «esborrany» |
| Cometes | `"esquema xarxes"` | La frase exacta |

> Els noms dels filtres depenen de l'idioma del sistema. A Windows en anglés són `kind:`, `ext:`, `datemodified:` i `size:`.

**Exemple combinat:** `ext:pdf modificat:este mes xarxes` busca PDF d'este mes que continguen «xarxes».

## 3. Nivell 2: expressions regulars reals

### 3.1. Símbols bàsics

| Símbol | Significat | Exemple |
|---|---|---|
| `.` | Qualsevol caràcter | `t.ma` → `tema`, `tima` |
| `*` | El caràcter anterior es repetix **0 o més** vegades | `ab*` → `a`, `ab`, `abbb` |
| `+` | **1 o més** vegades | `ab+` → `ab`, `abbb` |
| `?` | **0 o 1** vegada (opcional) | `colou?r` → `color`, `colour` |
| `\d` | Un dígit (0-9) | `tema\d` → `tema1`, `tema7` |
| `\d{2}` | Exactament 2 dígits | `\d{2}` → `10`, `25` |
| `[abc]` | Un dels caràcters indicats | `[ae]sto` → `asto`, `esto` |
| `[0-9]` | Un caràcter d'un rang | `nota[0-9]` |
| `[^abc]` | Qualsevol caràcter **excepte** eixos | `[^0-9]` |
| `^` | Inici de línia | `^Tema` |
| `$` | Final de línia | `\.pdf$` |
| `\.` | Un punt literal (la barra invertida «escapa» el símbol) | `\.docx` |
| `a\|b` | «a» **o** «b» | `pdf\|docx` |
| `( )` | Agrupa parts del patró | `(red\|web)es` |
| `\w` | Lletra, número o guió baix | `\w+` → `esquema_v1` |
| `\s` | Espai en blanc | `esquema\sxarxes` |
| `{n,m}` | Entre *n* i *m* repeticions | `\d{1,3}` → `7`, `42`, `120` |

> Les expressions regulars tenen **variants** segons el programa (VS Code, PowerShell, Python...). Els símbols d'esta taula funcionen en quasi totes. A més, algunes distingixen majúscules i minúscules i altres no: en VS Code es controla amb el botó `Aa`, i en PowerShell `-match` no les distingix (`-cmatch` sí).

### 3.2. Exemples amb noms d'arxiu

Supón que tens estos arxius:

```text
2026-10-12_esquema_xarxes_v1.pdf
2026-10-15_esquema_xarxes_v2.pdf
2026-11-03_apunts_seguretat.docx
foto_excursio_01.jpg
foto_excursio_02.jpg
esborrany_final.txt
```

| Objectiu | Patró | Troba |
|---|---|---|
| Arxius que comencen per una data | `^\d{4}-\d{2}-\d{2}` | Els tres primers |
| Només els PDF | `\.pdf$` | Els dos esquemes |
| PDF o Word | `\.(pdf\|docx)$` | Els tres primers |
| Versions 1 o 2 | `_v[12]\.` | Els dos esquemes |
| Fotos numerades | `foto_.*_\d{2}\.jpg` | Les dos fotos |
| Arxius d'octubre de 2026 | `^2026-10` | Els dos esquemes |

### 3.3. On provar-les

- **Visual Studio Code:** prem `Ctrl + Shift + F` (buscar en arxius) i activa el botó `.*` (**Usar expressió regular**, drecera `Alt + R`). Busca dins del **contingut** dels arxius.
- **PowerShell:** per a filtrar arxius pel nom.

  ```powershell
  Get-ChildItem -Recurse | Where-Object { $_.Name -match '^\d{4}-\d{2}-\d{2}.*\.pdf$' }
  ```

- **Símbol del sistema (CMD):** `dir /s *.pdf` llista els PDF d'una carpeta i les seues subcarpetes (només admet els comodins `*` i `?`).
- **Ferramentes en línia** com regex101.com permeten provar el patró i veure què coincidix. No apegues en elles dades personals ni documents privats.

### 3.4. Errors freqüents

- Oblidar escapar el punt: `.pdf` troba també `xpdf`; utilitza `\.pdf`.
- Confondre comodins amb regex: `*.pdf` és un comodí; en regex seria `.*\.pdf`.
- Patrons massa generals: `.*` coincidix amb quasi tot. Comença per un patró concret i amplia'l.
- Provar sense comprovar els resultats: revisa sempre la llista abans d'**esborrar o moure** arxius.

## 4. Buscar des del navegador

Els navegadors **no utilitzen expressions regulars** en buscar (ni en la pàgina amb `Ctrl + F` ni en l'historial), però oferixen operadors i dreceres molt útils per a recuperar informació, per exemple una pàgina visitada o un document publicat a Internet.

### 4.1. Operadors de cerca

Els operadors depenen del **buscador** (Google, Brave Search, DuckDuckGo, etc.), no del navegador: pots utilitzar Google en Firefox o DuckDuckGo en Chrome. DuckDuckGo té la seua pròpia secció més avall (4.1.1).

**Comuns a Google i Brave Search:**

| Operador | Exemple | Resultat |
|---|---|---|
| `" "` | `"seguretat de la informació"` | La frase exacta |
| `-` | `xarxes -wifi` | Exclou resultats amb «wifi» |
| `site:` | `site:gva.es calendari` | Només resultats d'eixe lloc |
| `filetype:` | `filetype:pdf ciberseguretat` | Només arxius d'eixe tipus |
| `intitle:` | `intitle:regex guia` | La paraula apareix al títol |
| `OR` (majúscules) | `còpia OR còpies` | Qualsevol dels dos termes |

**Només Google (entre altres):**

| Operador | Exemple | Resultat |
|---|---|---|
| `inurl:` | `inurl:tutorial` | La paraula apareix a l'adreça |
| `*` | `"còpia de * arxius"` | Comodí per a una paraula desconeguda |
| `..` | `portàtil 400..600` | Interval numèric |
| `ext:` | `logotip ext:png` | Equival a `filetype:` (per exemple, `ext:png`, `ext:pdf`) |
| `intext:` | `intext:"còpia de seguretat"` | El terme apareix al text de la pàgina |
| `allintitle:` | `allintitle:còpia seguretat` | Tots els termes apareixen al títol |
| `before:` / `after:` | `ciberseguretat after:2025-01-01` | Pàgines anteriors o posteriors a una data |
| `define:` | `define:backup` | Definició d'una paraula |
| `AROUND(n)` | `còpia AROUND(3) seguretat` | Dos termes separats per com a màxim *n* paraules |

> **Sobre els claudàtors:** `[png]` **no** és un operador de Google. Per a filtrar per extensió s'utilitza `filetype:png` o `ext:png`. Si s'escriu entre claudàtors o cometes, Google busca eixa paraula com a text, no com a tipus d'arxiu. Els claudàtors tampoc filtren en Brave Search ni en DuckDuckGo.

**Només Brave Search:**

| Operador | Exemple | Resultat |
|---|---|---|
| `ext:` | `manual ext:pdf` | Pàgines amb eixa extensió |
| `inbody:` | `inbody:"còpia de seguretat"` | El terme està al cos de la pàgina |
| `inpage:` | `inpage:regex` | El terme està al títol o al cos |
| `lang:` | `visats lang:es` | Pàgines en eixe idioma (codi de dos lletres) |
| `loc:` | `cataractes loc:ca` | Pàgines d'eixe país o regió |
| `+` | `gpu +freesync` | Obliga que el terme aparega |
| `AND`, `OR`, `NOT` | `xarxes NOT site:wikipedia.org` | Combinen condicions |

> Els operadors s'escriuen **sense espai** després dels dos punts. Brave indica a la seua ajuda que els seus operadors són **experimentals**, i el funcionament de tots dos buscadors pot canviar amb el temps; si un operador no dona resultats, prova'l en un altre buscador.

### 4.1.1. DuckDuckGo

DuckDuckGo és un buscador que no rastreja les cerques dels seus usuaris. Admet estos operadors:

| Operador | Exemple | Resultat |
|---|---|---|
| `" "` | `"còpia de seguretat"` | La frase exacta |
| `~" "` | `~"còpia de seguretat"` | Experimental: també resultats de significat paregut |
| `-` | `xarxes -wifi` | Menys resultats amb eixe terme |
| `+` | `xarxes +seguretat` | Més resultats amb eixe terme |
| `filetype:` | `ciberseguretat filetype:pdf` | Només eixe tipus d'arxiu (pdf, doc(x), xls(x), ppt(x), html) |
| `site:` | `calendari site:gva.es` | Només resultats d'eixe lloc |
| `-site:` | `xarxes -site:wikipedia.org` | Exclou un lloc |
| `intitle:` | `intitle:regex` | La paraula està al títol |
| `inurl:` | `inurl:tutorial` | La paraula està a l'adreça |
| `\` | `\futurama` | Va directament al primer resultat |
| `!safeon` / `!safeoff` | `ciència !safeon` | Activa o desactiva la cerca segura només en eixa cerca |

**Bangs (`!`):** dreceres per a buscar directament en un altre web. Per exemple, `!w filtre bambolla` busca a Wikipedia i `!a portàtil` a Amazon. Tin en compte que la cerca es fa en **eixe altre web**, i s'apliquen les seues polítiques de dades.

> DuckDuckGo indica que part de la seua sintaxi avançada pot no funcionar al 100 % en totes les cerques. Si no hi ha resultats, mostra resultats relacionats.

### 4.1.2. Filtrar per tipus d'arxiu i extensió

| Buscador | Operador | Exemple | Notes |
|---|---|---|---|
| Google | `filetype:` o `ext:` | `esquema xarxes ext:png` | Admet molts tipus (pdf, docx, xlsx, pptx, png, jpg...) |
| Brave Search | `filetype:` o `ext:` | `esquema xarxes ext:pdf` | Operadors experimentals |
| DuckDuckGo | `filetype:` | `esquema xarxes filetype:pdf` | Tipus admesos: pdf, doc(x), xls(x), ppt(x), html; **no** imatges |

Per a **imatges**, a més d'`ext:png`, els buscadors oferixen filtres a la pestanya **Imatges**: grandària, color, tipus (foto, il·lustració, GIF...) i llicència d'ús. A Google es troben a **Eines**; a Brave i DuckDuckGo, a la barra de filtres situada damunt dels resultats. Els noms i la posició poden canviar.

> Abans de reutilitzar una imatge o un document, comprova'n la **llicència** i cita la font.

### 4.2. Google Chrome

- **Buscar a la pàgina:** `Ctrl + F`.
- **Historial:** `Ctrl + H` i escriu al quadre de cerca; també pots anar a `chrome://history`.
- **Buscar entre les pestanyes obertes:** `Ctrl + Shift + A`.
- **Dreceres a la barra d'adreces:** escriu `@historial`, `@marcadors` o `@pestanyes` i prem `Tab` per a buscar només en eixe àmbit (el nom pot variar segons l'idioma).
- **Administrador de marcadors:** `Ctrl + Shift + O`.
- **Descàrregues:** `Ctrl + J` mostra i permet buscar els arxius descarregats.

### 4.3. Mozilla Firefox

- **Buscar a la pàgina:** `Ctrl + F`; les opcions permeten coincidir majúscules i paraules completes.
- **Historial:** `Ctrl + H` obri la barra lateral amb buscador; `Ctrl + Shift + H` obri la biblioteca.
- **Marcadors:** `Ctrl + Shift + O` obri la biblioteca de marcadors amb buscador.
- **Símbols de restricció a la barra d'adreces** (escriu-los seguits d'un espai i el terme; poden canviar segons la versió de Firefox):

  | Símbol | Busca en |
  |---|---|
  | `*` | Marcadors |
  | `^` | Historial |
  | `%` | Pestanyes obertes |
  | `#` | Títols de pàgina |
  | `$` | Adreces (URL) |

  Exemple: `^ xarxes` busca «xarxes» només a l'historial.
- **Descàrregues:** `Ctrl + Shift + Y`.

### 4.4. Brave

Brave està basat en Chromium, per la qual cosa comparteix moltes dreceres amb Chrome.

- **Buscar a la pàgina:** `Ctrl + F`.
- **Historial:** `Ctrl + H`.
- **Buscar entre les pestanyes obertes:** `Ctrl + Shift + A`.
- **Marcadors:** `Ctrl + Shift + O`.
- **Descàrregues:** `Ctrl + J`.
- **Buscador:** Brave utilitza Brave Search per defecte (operadors a l'apartat 4.1). El buscador predeterminat es canvia a `brave://settings/search`.
- **Bangs:** a Brave Search, escriure `!w` seguit d'un terme porta directament a Wikipedia (consulta l'ajuda de Brave Search sobre els *bangs*).

### 4.5. Comparativa ràpida

| Acció | Chrome | Firefox | Brave |
|---|---|---|---|
| Buscar a la pàgina | `Ctrl + F` | `Ctrl + F` | `Ctrl + F` |
| Historial | `Ctrl + H` | `Ctrl + H` | `Ctrl + H` |
| Marcadors | `Ctrl + Shift + O` | `Ctrl + Shift + O` | `Ctrl + Shift + O` |
| Descàrregues | `Ctrl + J` | `Ctrl + Shift + Y` | `Ctrl + J` |
| Buscar pestanyes | `Ctrl + Shift + A` | `%` a la barra | `Ctrl + Shift + A` |
| Expressions regulars | No | No | No |

## 5. Practica

Els exercicis d'esta guia, amb les solucions, estan a [Exercicis - Expressions regulars i cerques](Ejercicios%20-%20Expresiones%20regulares%20y%20búsquedas-VAL.md).
