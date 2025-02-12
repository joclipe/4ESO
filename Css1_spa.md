**Introducció a les Fulles d'Estil (CSS)**

Les Fulles d'Estil en Cascada (CSS, per les seues sigles en anglès) són un llenguatge utilitzat per descriure la presentació d'un document escrit en un llenguatge de marcatge, com HTML. CSS permet separar el contingut del disseny, facilitant l'aplicació d'estils visuals a diversos elements de la pàgina web, com ara colors, tipus de lletra, espais, mides i disposicions. Això proporciona una major flexibilitat i control en la presentació de les pàgines web, permetent que els estils s'apliquen de manera consistent i eficient en tot el document o en múltiples documents.

Es a dir, CSS és com la roba que li poses a una pàgina web. Mentre que l'HTML crea l'estructura i el contingut (com l'esquelet d'una casa), el CSS (Fulles d'Estil en Cascada) s'encarrega de l'aspecte visual i l'estil. Amb CSS, pots canviar colors, tipus de lletra, mides, espais i disposicions per a fer que la teua pàgina siga atractiva i única. És com decorar i pintar una casa perquè siga acollidora i bonica.


### **Com s'utilitza el CSS en HTML**

Hi ha tres formes bàsiques d'integrar CSS en els teus documents HTML:

1. **Estils en línia**: Afegixes l'estil directament en l'element HTML utilitzant l'atribut `style`.

   ```html
   <p style="color: blau;">Este és un paràgraf en blau.</p>
   ```

2. **Estils interns**: Inclous una secció `<style>` dins de l'etiqueta `<head>` del teu document HTML.

   ```html
   <head>
       <style>
           p {
               color: roig;
           }
       </style>
   </head>
   ```

3. **Estils externs**: Crees un arxiu CSS separat (per exemple, `estil.css`) i l'enllaces al teu document HTML amb l'etiqueta `<link>`.

   ```html
   <head>
       <link rel="stylesheet" type="text/css" href="estil.css">
   </head>
   ```

---

### **Estructura d'una Regla CSS**

Una regla CSS està composta per:

```css
selector {
    propietat: valor;
}
```

- **Selector**: Indica a quins elements s'aplicarà l'estil (per exemple, `p`, `.classe`, `#id`).
- **Propietat**: La característica que vols modificar (com ara `color`, `font-size`).
- **Valor**: El valor que assignes a la propietat (per exemple, `blau`, `16px`).

---

### **Atributs més Comuns Dividits per Categories**

#### **Propietats de Text**

1. **`color`**: Canvia el color del text.

   ```css
   p {
       color: verd;
   }
   ```

   *El text dels paràgrafs serà de color verd.*

2. **`text-align`**: Alinea el text dins de l'element.

   Valors comuns:

   - `left` (esquerra)
   - `center` (centre)
   - `right` (dreta)

   ```css
   h1 {
       text-align: center;
   }
   ```

   *Els encapçalaments `<h1>` estaran centrats en la pàgina.*

3. **`font-size`**: Ajusta la mida de la lletra.

   ```css
   p {
       font-size: 16px;
   }
   ```

   *Els paràgrafs tindran una lletra de 16 píxels.*

4. **`font-weight`**: Defineix el gruix de la lletra.

   Valors comuns:

   - `normal`
   - `bold` (negreta)

   ```css
   p {
       font-weight: bold;
   }
   ```

   *El text dels paràgrafs apareixerà en negreta.*

#### **Propietats de Fons**

1. **`background-color`**: Estableix el color de fons d'un element.

   ```css
   body {
       background-color: #f0f0f0;
   }
   ```

   *El fons de la pàgina serà de color gris clar.*

2. **`background-image`**: Assigna una imatge de fons.

   ```css
   div {
       background-image: url('imatge.jpg');
   }
   ```

   *El div tindrà una imatge de fons anomenada 'imatge.jpg'.*

#### **Propietats d'Espaiat**

1. **`margin`**: Controla l'espai exterior (marge) d'un element.

   ```css
   h1 {
       margin-top: 20px;
       margin-bottom: 10px;
   }
   ```

   *L'encapçalament `<h1>` tindrà un marge superior de 20 píxels i un marge inferior de 10 píxels.*

2. **`padding`**: Controla l'espai interior (farcit) d'un element.

   ```css
   p {
       padding: 15px;
   }
   ```

   *Els paràgrafs tindran un espai interior de 15 píxels en tots els costats.*

#### **Propietats de Dimensions**

1. **`width`**: Estableix l'amplària d'un element.

   ```css
   img {
       width: 300px;
   }
   ```

   *Totes les imatges tindran una amplària de 300 píxels.*

2. **`height`**: Estableix l'altura d'un element.

   ```css
   img {
       height: 200px;
   }
   ```

   *Totes les imatges tindran una altura de 200 píxels.*

#### **Propietats de Bordes**

1. **`border`**: Defineix el tipus, ample i color del borde d'un element.

   ```css
   div {
       border: 2px solid verd;
   }
   ```

   *El div tindrà un borde verd, sòlid i de 2 píxels d'ample.*

2. **`border-radius`**: Arredoneix les cantonades dels bordes.

   ```css
   img {
       border-radius: 10px;
   }
   ```

   *Les imatges tindran cantonades arrodonides de 10 píxels.*

---

### **Utilització de `class` i `id`**

#### **Atribut `class`**

- **Per a què serveix?**: L'atribut `class` s'utilitza per a assignar un nom comú a diversos elements. Açò ens permet aplicar els mateixos estils a tots ells.

- **Exemple en HTML:**

  ```html
  <p class="destacat">Este paràgraf està destacat.</p>
  <div class="destacat">Este div també està destacat.</div>
  ```

- **Exemple en CSS:**

  ```css
  .destacat {
      color: roig;
      font-weight: bold;
  }
  ```

#### **Atribut `id`**

- **Per a què serveix?**: L'atribut `id` s'utilitza per a identificar un element únic en la pàgina. Cada `id` ha de ser únic dins del document.

- **Exemple en HTML:**

  ```html
  <h1 id="titol-principal">Benvinguts a la meua pàgina web</h1>
  ```

- **Exemple en CSS:**

  ```css
  #titol-principal {
      color: blau;
      text-align: center;
  }
  ```

---

### **Exemple Final de l'Ús de CSS**

Anem a posar en pràctica tot el que hem aprés amb un exemple complet.

**HTML:**

```html
<!DOCTYPE html>
<html lang="va">
<head>
    <meta charset="UTF-8">
    <title>Exemple Bàsic de CSS</title>
    <link rel="stylesheet" type="text/css" href="estil.css">
</head>
<body>
    <h1 id="titol-principal">La meua Primera Pàgina Web</h1>
    <p>Este és un paràgraf normal.</p>
    <p class="destacat">Este paràgraf està destacat en roig i negreta.</p>
    <div class="caixa">
        <p>Açò és un paràgraf dins d'un div amb fons gris.</p>
    </div>
    <img src="imatge.jpg" alt="Imatge Exemple">
</body>
</html>
```

**CSS (`estil.css`):**

```css
/* Estil per al cos de la pàgina */
body {
    background-color: #e0f7fa;
    font-family: Arial, sans-serif;
    color: #333;
}

/* Estil per al títol principal */
#titol-principal {
    font-size: 28px;
    color: blau;
    text-align: center;
    margin-bottom: 20px;
}

/* Estil per als paràgrafs normals */
p {
    font-size: 16px;
    line-height: 1.5;
}

/* Estil per a la classe 'destacat' */
.destacat {
    color: roig;
    font-weight: bold;
}

/* Estil per al div amb classe 'caixa' */
.caixa {
    background-color: #f0f0f0;
    padding: 15px;
    border: 1px solid #ccc;
    border-radius: 5px;
    margin-top: 20px;
}

/* Estil per a les imatges */
img {
    width: 300px;
    height: auto;
    border-radius: 10px;
    display: block;
    margin: 0 auto;
}
```

**Explicació de l'Exemple:**

- **Cos de la pàgina (`body`)**: Establim un color de fons suau, una tipografia llegible i un color de text adequat.

- **Títol principal (`#titol-principal`)**: Utilitzem l'atribut `id` per a donar un estil únic al títol, augmentant la mida de la lletra, canviant el color a blau i centrant el text.

- **Paràgrafs normals (`p`)**: Definim la mida de la lletra i l'altura de línia per a una lectura còmoda.

- **Paràgrafs destacats (`.destacat`)**: Mitjançant la classe `destacat`, canviem el color del text a roig i l'estil en negreta per a ressaltar-los.

- **Div amb classe `caixa`**: Creem una caixa amb fons gris clar, farcit interior, un borde subtil i cantonades arrodonides per a millorar l'estètica.

- **Imatges (`img`)**: Ajustem l'amplària de la imatge, afegim cantonades arrodonides i centrem la imatge en la pàgina.

---

### **Consells Finals**

- **Practica i Experimenta**: No tingues por d'experimentar amb diferents propietats i valors. Així descobriràs com afecten l'aparença de la teua pàgina.

- **Utilitza Noms Significatius**: Quan crees classes i ids, dona'ls noms que reflectisquen la seua funció per a facilitar la comprensió del codi.

- **Mantín el Codi Organitzat**: Utilitza comentaris i estructura el teu CSS per seccions. Açò t'ajudarà a mantenir el codi net i fàcil de mantenir.

