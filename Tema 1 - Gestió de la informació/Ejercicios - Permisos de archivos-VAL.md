# Exercicis: permisos d'arxius i carpetes

Material de suport: [Guia - Permisos d'arxius](Guía%20-%20Permisos%20de%20archivos-VAL.md).

## Activitats

Estes activitats es fan a **LliureX** (basat en Ubuntu, per la qual cosa utilitza el model de permisos de Linux). Treballa sempre a la teua carpeta personal i no canvies els permisos de carpetes del sistema.

1. **Observar.** Al gestor d'arxius, fes clic dret sobre una carpeta o un arxiu de la teua carpeta personal i obri **Propietats > Permisos** (el nom pot variar segons l'entorn d'escriptori). Anota qui és el propietari, quin és el grup i quins permisos té cada categoria.
2. **Terminal.** Obri un terminal i executa `ls -l` a la teua carpeta personal. Tria tres elements i, per a cadascun, indica si és arxiu o carpeta, qui és el propietari i quins permisos té cada categoria.
3. **Comparar.** Explica la diferència entre **lectura**, **escriptura** i **execució** en un arxiu i en una carpeta.
4. **Interpretar.** Indica què poden fer el propietari, el grup i els altres amb estos permisos:
   - a) `-rw-r-----`
   - b) `drwxr-xr-x`
   - c) `-rw-------`
5. **Notació numèrica.** Escriu el número que correspon a cada cas i comprova la resposta amb la taula de la guia:
   - a) `rwxr-xr--`
   - b) propietari: llegir i escriure; grup: llegir; altres: res.
6. **Practicar amb `chmod`.** En una carpeta de proves de la teua carpeta personal:
   - a) Crea un arxiu amb `touch prova.txt` i mira els permisos amb `ls -l prova.txt`.
   - b) Lleva la lectura als altres amb `chmod o-r prova.txt` i comprova el canvi.
   - c) Deixa l'arxiu amb permisos `600` i comprova el resultat.
   - d) Crea un script amb `echo 'echo Hola' > salutacio.sh`, intenta executar-lo amb `./salutacio.sh` i observa l'error. Afig el permís d'execució amb `chmod u+x salutacio.sh` i torna a provar.
   - e) Crea una carpeta amb `mkdir privada` i lleva el permís `x` amb `chmod a-x privada`. Intenta entrar-hi amb `cd privada` i explica què passa. Després torna'l a deixar com estava amb `chmod 755 privada`.
7. **Compartir amb criteri.** Comparteix un document de prova a través del servei que utilitze el centre (per exemple, Moodle o el núvol de l'institut) amb un company o companya com a **lector**. Comprova què pot fer i què no. Si el servei ho permet, canvia-ho després a **editor**.
8. **Cas pràctic.** Un grup de quatre alumnes treballa en un projecte en una carpeta compartida de l'aula. Proposa qui hauria de tindre permisos d'edició, qui de lectura i com revisaries els accessos en acabar.

> No utilitzes `chmod 777` ni `sudo` en estes activitats: no fan falta i poden deixar arxius insegurs o danyar el sistema.

## Solucions orientatives

- **4.** a) el propietari llig i escriu; el grup només llig; els altres no tenen accés. b) és una carpeta: el propietari té tots els permisos, i el grup i els altres poden llegir i entrar. c) només el propietari pot llegir i escriure; ningú més té accés.
- **5.** a) `754`. b) `640`.
- **6.**
  - b) `ls -l` mostrarà `-rw-r-----` si abans era `-rw-r--r--`.
  - c) `chmod 600 prova.txt` deixa `-rw-------`.
  - d) sense `x`, el sistema respon «Permís denegat»; després de `chmod u+x`, l'script s'executa i mostra `Hola`.
  - e) `cd privada` falla amb «Permís denegat» perquè sense `x` no es pot entrar a la carpeta.
- **1, 2, 3, 7 i 8:** les respostes depenen de l'equip i del cas; comprova que s'aplica el **mínim privilegi**.
