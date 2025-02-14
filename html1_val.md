#HTML (HyperText Markup Language)

## **Què és HTML?**

HTML (HyperText Markup Language) és el llenguatge estàndard per a crear pàgines web. Defineix l'estructura i el contingut d'una pàgina web mitjançant etiquetes. Cada etiqueta té una funció específica i ajuda a organitzar i formatar el contingut.

## **Com funciona HTML?**

HTML utilitza etiquetes per a definir diferents elements dins d'una pàgina web. Aquestes etiquetes vénen en parelles, amb una etiqueta d'obertura i una etiqueta de tancament. Per exemple, l'etiqueta per a un paràgraf es escriu així:
```html
<p>Això és un paràgraf.</p>
```
En aquest cas, `<p>` és l'etiqueta d'obertura que indica l'inici del paràgraf, i `</p>` és l'etiqueta de tancament que indica el final del paràgraf.

## **Etiquetes bàsiques de formatatge de contingut**

1. **Negreta**
   ```html
   <b>Text en negreta</b>
   ```
   L'etiqueta `<b>` s'utilitza per a fer el text en negreta. Les etiquetes d'obertura `<b>` i de tancament `</b>` envolten el text que vols emfatitzar.
   - **Alternativa:** L'etiqueta `<strong>` també s'utilitza per a emfatitzar el text amb una importància forta:
     ```html
     <strong>Text fort</strong>
     ```

2. **Cursiva**
   ```html
   <i>Text en cursiva</i>
   ```
   L'etiqueta `<i>` s'utilitza per a posar el text en cursiva. Envolta el text amb les etiquetes d'obertura `<i>` i de tancament `</i>`.
   - **Alternativa:** L'etiqueta `<em>` s'utilitza per a emfatitzar el text, donant-li un significat emfatitzat:
     ```html
     <em>Text emfatitzat</em>
     ```

3. **Subratllat**
   ```html
   <u>Text subratllat</u>
   ```
   L'etiqueta `<u>` s'utilitza per a subratllar el text, envoltant-lo amb `<u>` i `</u>`.

4. **Tachado**
   ```html
   <s>Text tachado</s>
   ```
   L'etiqueta `<s>` s'utilitza per a tachar el text, envoltant-lo amb `<s>` i `</s>`.

5. **Destacat**
   ```html
   <mark>Text destacat</mark>
   ```
   L'etiqueta `<mark>` s'utilitza per a destacar el text.

6. **Subíndex**
   ```html
   <sub>Text subíndex</sub>
   ```
   L'etiqueta `<sub>` s'utilitza per a crear text subíndex, que apareix lleugerament per sota de la línia normal del text.

7. **Superíndex**
   ```html
   <sup>Text superíndex</sup>
   ```
   L'etiqueta `<sup>` s'utilitza per a crear text superíndex, que apareix lleugerament per sobre de la línia normal del text.

## **Estructuració**

1. **Capçalera**
   ```html
   <header>
     <h1>Benvingut a la meua pàgina web</h1>
   </header>
   ```
   L'etiqueta `<header>` s'utilitza per a definir la secció de capçalera de la pàgina, sovint incloent títols i logotips. Dins de `<header>`, pots utilitzar `<h1>` per a indicar el títol principal.

2. **Peu de pàgina**
   ```html
   <footer>
     <p>&copy; 2025 La meua pàgina web</p>
   </footer>
   ```
   L'etiqueta `<footer>` s'utilitza per a definir el peu de pàgina, que normalment conté informació de contacte, avisos de copyright, etc. En aquest exemple, `<p>` s'utilitza per a afegir un paràgraf dins del peu de pàgina.

3. **Seccions**
   ```html
   <section>
     <h2>Secció de contingut</h2>
     <p>Contingut de la secció.</p>
   </section>
   ```
   L'etiqueta `<section>` s'utilitza per a definir seccions de la pàgina que contenen contingut temàticament relacionat. Dins de `<section>`, `<h2>` defineix un subtítol, i `<p>` afegeix un paràgraf.

4. **Article**
   ```html
   <article>
     <h2>Títol de l'article</h2>
     <p>Això és un article.</p>
   </article>
   ```
   L'etiqueta `<article>` s'utilitza per a representar una composició autònoma en un document, com un post de blog o un article de notícies.

5. **Navegació**
   ```html
   <nav>
     <ul>
       <li><a href="#home">Inici</a></li>
       <li><a href="#about">Sobre</a></li>
       <li><a href="#contact">Contacte</a></li>
     </ul>
   </nav>
   ```
   L'etiqueta `<nav>` s'utilitza per a definir enllaços de navegació.

6. **Principal**
   ```html
   <main>
     <h2>Contingut principal</h2>
     <p>Això és el contingut principal de la pàgina.</p>
   </main>
   ```
   L'etiqueta `<main>` s'utilitza per a especificar el contingut principal d'un document. El contingut dins de l'etiqueta `<main>` ha de ser únic per al document i no ha de contenir contingut de barra lateral, peu de pàgina o capçalera.

## **Etiquetes per a crear paràgrafs, taules, llistes i enllaços**

1. **Paràgrafs**
   ```html
   <p>Això és un paràgraf.</p>
   ```
   L'etiqueta `<p>` s'utilitza per a definir paràgrafs en el contingut. Cada bloc de text que vulguis separar en un paràgraf ha de ser dins de `<p>` i `</p>`.

2. **Taules**
   ```html
   <table>
     <tr>
       <th>Capçalera 1</th>
       <th>Capçalera 2</th>
     </tr>
     <tr>
       <td>Cel·la 1</td>
       <td>Cel·la 2</td>
     </tr>
   </table>
   ```
   - `<table>` defineix l'inici i el final de la taula.
   - `<tr>` s'utilitza per a definir una fila de la taula.
   - `<th>` s'utilitza per a definir cel·les de capçalera.
   - `<td>` s'utilitza per a definir cel·les de dades.

3. **Llistes**
   - **Llista no ordenada**
     ```html
     <ul>
       <li>Element 1</li>
       <li>Element 2</li>
       <li>Element 3</li>
     </ul>
     ```
     - `<ul>` defineix una llista no ordenada.
     - `<li>` defineix cada element de la llista.
   
   - **Llista ordenada**
     ```html
     <ol>
       <li>Element 1</li>
       <li>Element 2</li>
       <li>Element 3</li>
     </ol>
     ```
     - `<ol>` defineix una llista ordenada.
     - `<li>` defineix cada element de la llista.

4. **Llista de descripcions**
   ```html
   <dl>
     <dt>Term 1</dt>
     <dd>Descripció per al Term 1</dd>
     <dt>Term 2</dt>
     <dd>Descripció per al Term 2</dd>
   </dl>
   ```
   - `<dl>` defineix una llista de descripcions.
   - `<dt>` defineix un terme en la llista de descripcions.
   - `<dd>` defineix la descripció del terme.

5. **Enllaços**
   ```html
   <a href="https://www.example.com">Visita Example.com</a>
   ```
   L'etiqueta `<a>` s'utilitza per a crear enllaços. L'atribut `href` defineix la URL de l'enllaç, i el text entre `<a>` i `</a>` és el que es mostra com l'enllaç clicable.

6. **Imatge**
   ```html
   <img src="image.jpg" alt="Descripció de la imatge">
   ```
   L'etiqueta `<img>` s'utilitza per a incrustar una imatge en una pàgina web. L'atribut `src` especifica el camí cap a la imatge, i l'atribut `alt` proporciona una descripció alternativa de text de la imatge.

## **Conclusió**

HTML és el bloc fonamental per a crear pàgines web. Entenent aquestes etiquetes bàsiques i com funcionen, pots començar a estructurar i formatar el teu propi contingut web. Diverteix-te experimentant i creant!
