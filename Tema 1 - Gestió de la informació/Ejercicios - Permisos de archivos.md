# Ejercicios: permisos de archivos y carpetas

Material de apoyo: [Guía - Permisos de archivos](Guía%20-%20Permisos%20de%20archivos.md).

## Actividades

Estas actividades se realizan en **LliureX** (basado en Ubuntu, por lo que usa el modelo de permisos de Linux). Trabaja siempre en tu carpeta personal y no cambies permisos de carpetas del sistema.

1. **Observar.** En el gestor de archivos, haz clic derecho sobre una carpeta o un archivo de tu carpeta personal y abre **Propiedades > Permisos** (el nombre puede variar según el entorno de escritorio). Anota quién es el propietario, cuál es el grupo y qué permisos tiene cada categoría.
2. **Terminal.** Abre un terminal y ejecuta `ls -l` en tu carpeta personal. Elige tres elementos y para cada uno indica si es archivo o carpeta, quién es el propietario y qué permisos tiene cada categoría.
3. **Comparar.** Explica la diferencia entre **lectura**, **escritura** y **ejecución** en un archivo y en una carpeta.
4. **Interpretar.** Indica qué puede hacer el propietario, el grupo y los demás con estos permisos:
   - a) `-rw-r-----`
   - b) `drwxr-xr-x`
   - c) `-rw-------`
5. **Notación numérica.** Escribe el número que corresponde a cada caso y comprueba la respuesta con la tabla de la guía:
   - a) `rwxr-xr--`
   - b) propietario: leer y escribir; grupo: leer; otros: nada.
6. **Practicar con `chmod`.** En una carpeta de pruebas de tu carpeta personal:
   - a) Crea un archivo con `touch prueba.txt` y mira sus permisos con `ls -l prueba.txt`.
   - b) Quita la lectura a los demás con `chmod o-r prueba.txt` y comprueba el cambio.
   - c) Deja el archivo con permisos `600` y comprueba el resultado.
   - d) Crea un script con `echo 'echo Hola' > saludo.sh`, intenta ejecutarlo con `./saludo.sh` y observa el error. Añade el permiso de ejecución con `chmod u+x saludo.sh` y vuelve a probar.
   - e) Crea una carpeta con `mkdir privada` y quita el permiso `x` con `chmod a-x privada`. Intenta entrar con `cd privada` y explica qué ocurre. Después devuélvelo con `chmod 755 privada`.
7. **Compartir con criterio.** Comparte un documento de prueba a través del servicio que use el centro (por ejemplo, Moodle o la nube del instituto) con un compañero como **lector**. Comprueba qué puede hacer y qué no. Si el servicio lo permite, cámbialo después a **editor**.
8. **Caso práctico.** Un grupo de cuatro alumnos trabaja en un proyecto en una carpeta compartida del aula. Propón quién debería tener permisos de edición, quién de lectura y cómo revisarías los accesos al terminar.

> No uses `chmod 777` ni `sudo` en estas actividades: no hacen falta y pueden dejar archivos inseguros o dañar el sistema.

## Soluciones orientativas

- **4.** a) el propietario lee y escribe; el grupo solo lee; los demás no tienen acceso. b) es una carpeta: el propietario tiene todos los permisos, y el grupo y los demás pueden leer y entrar. c) solo el propietario puede leer y escribir; nadie más tiene acceso.
- **5.** a) `754`. b) `640`.
- **6.**
  - b) `ls -l` mostrará `-rw-r-----` si antes era `-rw-r--r--`.
  - c) `chmod 600 prueba.txt` deja `-rw-------`.
  - d) sin `x`, el sistema responde «Permiso denegado»; tras `chmod u+x`, el script se ejecuta y muestra `Hola`.
  - e) `cd privada` falla con «Permiso denegado» porque sin `x` no se puede entrar en la carpeta.
- **1, 2, 3, 7 y 8:** las respuestas dependen del equipo y del caso; comprueba que se aplica el **mínimo privilegio**.
