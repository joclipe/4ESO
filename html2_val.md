# **Atributs i Valors HTML**

HTML (HyperText Markup Language) és el llenguatge estàndard per a crear pàgines web. Els atributs proporcionen informació addicional sobre els elements HTML. A continuació, es presenta un desglossament detallat dels atributs HTML i els seus valors:

## **1. Què són els Atributs HTML?**
- **Definició**: Els atributs són paraules especials que s'utilitzen dins de l'etiqueta d'obertura d'un element HTML per a controlar el comportament de l'element o proporcionar informació addicional.
- **Sintaxi**: Un atribut es compon d'un nom i un valor, format com `nom="valor"`.

## **2. Atributs HTML Comuns**
A continuació, es presenten alguns atributs HTML d'ús comú:

- **`id`**: 
  - **Propòsit**: Assigna un identificador únic a un element.
  - **Exemple**: `<div id="capçalera">Contingut de la capçalera</div>`

- **`class`**: 
  - **Propòsit**: Assigna un o més noms de classe a un element per a l'estilització amb CSS.
  - **Exemple**: `<p class="text-principal">Això és un paràgraf.</p>`

- **`style`**: 
  - **Propòsit**: Aplica estils CSS en línia a un element.
  - **Exemple**: `<h1 style="color: blue;">Hola món</h1>`

- **`src`**: 
  - **Propòsit**: Especifica la URL d'un recurs extern, comunament utilitzat en etiquetes `<img>` i `<script>`.
  - **Exemple**: `<img src="imatge.jpg" alt="Descripció de la imatge">`

- **`href`**: 
  - **Propòsit**: Especifica la URL d'un recurs enllaçat, utilitzat en etiquetes `<a>` (enllaç).
  - **Exemple**: `<a href="https://www.example.com">Visita Example</a>`

- **`alt`**: 
  - **Propòsit**: Proporciona text alternatiu per a una imatge si no es pot mostrar.
  - **Exemple**: `<img src="logo.png" alt="Logo de l'empresa">`

- **`title`**: 
  - **Propòsit**: Proporciona informació addicional sobre un element, sovint mostrada com un tooltip.
  - **Exemple**: `<button title="Fes clic en mi!">Enviar</button>`

## **3. Valors d'Atributs**
- **Tipus de Valors**:
  - **Cadenes**: La majoria dels valors d'atributs són cadenes tancades entre cometes (simples o dobles).
  - **Boolean**: Alguns atributs són booleanos, és a dir, poden estar presents o absents (per exemple, `disabled`, `checked`).
    - **Exemple**: `<input type="checkbox" checked>`

## **4. Bones Pràctiques**
- **Utilitza Noms Significatius**: Escull noms d'atributs que descriguen clarament el seu propòsit.
- **Evita Estils en Línia**: Prefereix CSS extern per a l'estilització per a mantenir HTML net i mantenible.
- **IDs Únics**: Assegura't que els atributs `id` siguin únics dins d'una pàgina per a evitar conflictes.

## **5. Codi d'Exemple**
A continuació, es presenta un fragment HTML senzill que demostra diversos atributs:

```html
<!DOCTYPE html>
<html lang="ca">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemple d'Atributs HTML</title>
    <link rel="stylesheet" href="estils.css">
</head>
<body>
    <header id="capçalera" class="capçalera-principal">
        <h1 style="color: blue;">Benvingut a la meua pàgina web</h1>
    </header>
    <nav>
        <ul>
            <li><a href="https://www.example.com" title="Ves a Example">Example</a></li>
        </ul>
    </nav>
    <img src="imatge.jpg" alt="Una bonica paisatge">
    <input type="checkbox" id="subscripcio" checked>
    <label for="subscripcio">Subscriure's al butlletí</label>
</body>
</html>
```

## **6. Opcions i Exemples de l'Atribut d'Estil HTML**

L'atribut `style` en HTML permet aplicar estils CSS directament a un element HTML. Això pot ser útil per a una estilització ràpida sense necessitat de crear un fitxer CSS separat. A continuació, es presenten algunes opcions comunes per a l'atribut `style`, juntament amb exemples.

### **Propietats CSS Comunes per a l'Atribut d'Estil**

1. **Color i Fons**
   - `color`: Estableix el color del text.
   - `background-color`: Estableix el color de fons.

   ```html
   <p style="color: blue; background-color: yellow;">Això és un paràgraf estilitzat.</p>
   ```

2. **Propietats de Font**
   - `font-size`: Estableix la mida de la font.
   - `font-family`: Especifica el tipus de font.
   - `font-weight`: Estableix el pes de la font (per exemple, negreta).

   ```html
   <h1 style="font-size: 24px; font-family: Arial, sans-serif; font-weight: bold;">Capçalera Estilitzada</h1>
   ```

3. **Alineació del Text**
   - `text-align`: Alinea el text (esquerra, dreta, centre, justificar).

   ```html
   <div style="text-align: center;">Este text està centrat.</div>
   ```

4. **Marge i Ompliment**
   - `border`: Estableix el contorn al voltant d'un element.
   - `padding`: Afegeix espai dins de l'element.

   ```html
   <div style="border: 1px solid black; padding: 10px;">Esta caixa té un contorn i ompliment.</div>
   ```

5. **Dimensions**
   - `width`: Estableix l'amplada d'un element.
   - `height`: Estableix l'alçada d'un element.

   ```html
   <div style="width: 200px; height: 100px; background-color: lightgray;">Esta caixa té dimensions específiques.</div>
   ```

6. **Marge**
   - `margin`: Estableix l'espai fora d'un element.

   ```html
   <p style="margin: 20px;">Este paràgraf té un marge al seu voltant.</p>
   ```

### **Exemple d'Ús de Múltiples Atributs d'Estil**

Es poden combinar múltiples atributs d'estil en un sol atribut `style`. A continuació, es presenta un exemple d'un botó estilitzat:

```html
<button style="background-color: green; color: white; padding: 10px 20px; border: none; border-radius: 5px;">
    Fes clic en mi!
</button>
```

## **Conclusió**

Entendre els atributs HTML i els seus valors és crucial per a un desenvolupament web efectiu. Milloren la funcionalitat i l'accessibilitat de les pàgines web, permetent una millor interacció i experiència de l'usuari.
