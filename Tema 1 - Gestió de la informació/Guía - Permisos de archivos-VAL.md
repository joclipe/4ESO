# 2.2.4. Guia: permisos d'arxius i carpetes

Els **permisos** determinen **qui** pot fer **què** amb un arxiu o una carpeta. Són una part bàsica de la seguretat: protegeixen la **confidencialitat** (no tothom pot llegir), la **integritat** (no tothom pot modificar) i la **disponibilitat** (qui ho necessita pot accedir-hi).

## 1. Conceptes bàsics

- **Usuari:** persona o compte que utilitza el sistema (per exemple, `alumne`).
- **Grup:** conjunt d'usuaris amb els mateixos drets (per exemple, `Alumnat` o `Professorat`).
- **Propietari:** usuari que va crear l'arxiu o que en té el control principal.
- **Permís:** autorització per a fer una acció sobre un arxiu o una carpeta.
- **Principi del mínim privilegi:** cada persona ha de tindre **només els permisos que necessita**, i no més.

### Tipus de permisos més habituals

| Permís | En un arxiu | En una carpeta |
|---|---|---|
| **Lectura** | Veure'n el contingut | Veure què conté |
| **Escriptura / modificació** | Canviar-ne el contingut | Crear, canviar de nom o esborrar elements dins |
| **Execució** | Executar-lo si és un programa o un script | Entrar a la carpeta i accedir al contingut |

## 2. Permisos en Linux (LliureX) i macOS

LliureX està basat en Ubuntu, així que utilitza el model de permisos de Linux: un model senzill amb tres categories i tres permisos. macOS utilitza un model molt paregut.

### 2.1. Categories i permisos

- **Categories:** propietari (`u`), grup (`g`) i altres (`o`).
- **Permisos:** lectura (`r`), escriptura (`w`) i execució (`x`).

En executar `ls -l` s'obté una cosa així:

```text
-rwxr-xr--  1 ana  classe  2048  oct 12 10:30  script.sh
```

| Part | Significat |
|---|---|
| `-` | Tipus (`-` arxiu, `d` carpeta) |
| `rwx` | El propietari pot llegir, escriure i executar |
| `r-x` | El grup pot llegir i executar, però no escriure |
| `r--` | Els altres només poden llegir |

### 2.2. Notació numèrica

Cada permís val un número: `r = 4`, `w = 2`, `x = 1`. Se sumen per categoria.

| Número | Permisos | Significat |
|---|---|---|
| `7` | `rwx` | Tot |
| `6` | `rw-` | Llegir i escriure |
| `5` | `r-x` | Llegir i executar |
| `4` | `r--` | Només llegir |
| `0` | `---` | Cap |

Exemple: `chmod 640 notes.txt` dona lectura i escriptura al propietari (`6`), només lectura al grup (`4`) i cap permís als altres (`0`).

### 2.3. Ordres útils

| Ordre | Per a què serveix | Exemple |
|---|---|---|
| `ls -l` | Veure els permisos | `ls -l informe.txt` |
| `chmod` | Canviar els permisos | `chmod u+x script.sh` (afig execució al propietari) |
| `chown` | Canviar el propietari (requerix administrador) | `sudo chown ana:classe notes.txt` |

> En una **carpeta**, el permís `x` és necessari per a entrar-hi. Sense `x` no es pot accedir al que conté, encara que es tinga `r`.

### 2.4. Des del gestor d'arxius

A LliureX, fes clic dret sobre un arxiu o una carpeta i tria **Propietats**; a la pestanya **Permisos** es veuen el propietari, el grup i els permisos de cada categoria, i es poden canviar si eres el propietari. Els noms exactes poden variar segons l'entorn d'escriptori.

A macOS es consulten des del Finder: **Obtindre informació** > **Compartir i permisos**.

> No canvies els permisos de carpetes del sistema i evita `chmod 777`: deixa l'arxiu accessible i modificable per qualsevol.

## 3. Permisos en Windows

Windows utilitza llistes de control d'accés (ACL) amb permisos més detallats.

### 3.1. Usuaris i grups habituals

| Nom | Què és |
|---|---|
| **Administradors** | Control total de l'equip |
| **Usuaris** | Comptes estàndard; poden utilitzar l'equip però no canviar el sistema |
| **SYSTEM** | Compte interna que utilitza Windows per als seus propis serveis |
| **Tots** (*Everyone*) | Qualsevol persona, també les que no tenen compte pròpia; evita donar-li permisos d'escriptura |

### 3.2. Veure els permisos d'un arxiu o una carpeta

1. Fes clic dret sobre l'element i tria **Propietats**.
2. Obri la pestanya **Seguretat**.
3. Selecciona un usuari o grup de la llista i consulta els permisos que té.

> Si no apareix la pestanya **Seguretat**, pot ser que l'element estiga en una unitat amb un sistema d'arxius que no l'admet (com FAT32 o exFAT) o que el teu compte no hi tinga accés.

### 3.3. Permisos principals

| Permís | Què permet |
|---|---|
| **Control total** | Fer-ho tot, inclòs canviar els permisos |
| **Modificar** | Llegir, canviar i eliminar |
| **Lectura i execució** | Veure i executar, sense canviar |
| **Mostrar el contingut de la carpeta** | Veure la llista d'elements (només carpetes) |
| **Lectura** | Veure el contingut i les propietats |
| **Escriptura** | Crear i modificar arxius |

Cada permís pot estar en **Permetre** o **Denegar**. **Denegar té prioritat sobre Permetre**, així que convé utilitzar-lo amb cura.

### 3.4. Canviar permisos

Només pot fer-ho el propietari, un administrador o qui tinga *Control total*.

1. **Propietats > Seguretat > Editar**.
2. Tria un usuari o grup, o prem **Afegir** per a incloure'n un altre.
3. Marca o desmarca els permisos i prem **Aplicar**.

> Canviar els permisos en carpetes del sistema (com `C:\Windows`) pot impedir que l'equip funcione correctament. No modifiques el que no reconegues.

### 3.5. Herència

Per defecte, els arxius **hereten** els permisos de la carpeta que els conté. Si canvies els permisos d'una carpeta, el normal és que s'apliquen a tot el que hi ha dins. Es pot deshabilitar des d'**Opcions avançades**, però convé evitar-ho llevat que siga necessari.

A **Opcions avançades** també es pot veure el **propietari** de l'element i consultar l'**accés efectiu** d'un usuari concret.

### 3.6. Des de la línia d'ordres

```powershell
# Veure els permisos d'una carpeta
icacls "C:\Users\alumne\Documentos\Projecte"
```

L'ordre `icacls` també permet modificar-los, però un error pot deixar-te sense accés. Practica només en carpetes de prova.

## 4. Permisos en compartir en el núvol

Serveis com Google Drive, OneDrive o Moodle solen utilitzar estos nivells:

| Nivell | Què pot fer la persona |
|---|---|
| **Lector / Només lectura** | Veure (i de vegades descarregar) |
| **Comentarista** | Veure i comentar |
| **Editor** | Modificar el contingut |
| **Propietari** | Controlar els permisos i eliminar l'arxiu |

Bones pràctiques:

- **Comparteix amb persones concretes** en lloc d'utilitzar «qualsevol persona amb l'enllaç», llevat que el contingut siga públic.
- **Tria el nivell més baix que servisca:** si només ha de llegir, dona-li permís de lectura.
- **Revisa periòdicament** amb qui has compartit cada arxiu i retira els accessos que ja no calguen.
- **Posa data de caducitat** a l'accés quan el servei ho permeta.
- **Desactiva la descàrrega o la còpia** de documents delicats si l'opció està disponible.
- **Tin en compte que un editor pot esborrar o espatllar el treball:** conserva còpies i activa l'historial de versions.

## 5. Bones pràctiques generals

1. Aplica el **mínim privilegi**.
2. Assigna permisos a **grups** en lloc de a persones una per una: és més fàcil de mantindre.
3. No utilitzes un compte d'**administrador** per al treball diari.
4. Revisa els permisos quan canvien els equips de treball o acaba un projecte.
5. No dones «Control total» ni permisos `777` per a «arreglar» un error d'accés: és una solució insegura.
6. Els permisos **no substituïxen** les còpies de seguretat ni el xifratge: protegeixen l'accés, no eviten pèrdues per fallada o esborrat. A més, qui tinga accés físic al dispositiu o siga administrador pot saltar-se alguns permisos si el contingut no està xifrat.
7. Documenta qui té accés a què, sobretot en carpetes compartides del centre o d'un equip.

## 6. Practica

Les activitats d'esta guia, amb les solucions, estan a [Exercicis - Permisos d'arxius](Ejercicios%20-%20Permisos%20de%20archivos-VAL.md).
