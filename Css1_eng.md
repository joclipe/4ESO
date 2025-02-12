### **Introduction to Cascading Style Sheets (CSS)**

Cascading Style Sheets (CSS) is a language used to describe the presentation of a document written in a markup language, such as HTML. CSS allows you to separate content from design, making it easier to apply visual styles to various elements of a web page, such as colors, fonts, spacing, sizes, and layouts. This provides greater flexibility and control over the presentation of web pages, enabling styles to be applied consistently and efficiently across an entire document or multiple documents.

In other words, CSS is like the clothing you put on a web page. While HTML creates the structure and content (like the skeleton of a house), CSS handles the visual appearance and style. With CSS, you can change colors, fonts, sizes, spacing, and layouts to make your web page attractive and unique. It's like decorating and painting a house to make it cozy and beautiful.


### **How to Use CSS in HTML**

There are three basic ways to integrate CSS into your HTML documents:

1. **Inline Styles**: You add the style directly within the HTML element using the `style` attribute.

   ```html
   <p style="color: blue;">This is a blue paragraph.</p>
   ```

2. **Internal Styles**: You include a `<style>` section within the `<head>` tag of your HTML document.

   ```html
   <head>
       <style>
           p {
               color: red;
           }
       </style>
   </head>
   ```

3. **External Styles**: You create a separate CSS file (e.g., `styles.css`) and link it to your HTML document using the `<link>` tag.

   ```html
   <head>
       <link rel="stylesheet" type="text/css" href="styles.css">
   </head>
   ```

---

### **Structure of a CSS Rule**

A CSS rule is composed of:

```css
selector {
    property: value;
}
```

- **Selector**: Indicates which elements the style will apply to (e.g., `p`, `.class`, `#id`).
- **Property**: The characteristic you want to modify (e.g., `color`, `font-size`).
- **Value**: The value you assign to the property (e.g., `blue`, `16px`).

---

### **Common Attributes Divided by Categories**

#### **Text Properties**

1. **`color`**: Changes the color of the text.

   ```css
   p {
       color: green;
   }
   ```

   *The text of the paragraphs will be green.*

2. **`text-align`**: Aligns the text within the element.

   Common values:

   - `left` (default)
   - `center`
   - `right`

   ```css
   h1 {
       text-align: center;
   }
   ```

   *The `<h1>` headers will be centered on the page.*

3. **`font-size`**: Adjusts the size of the text.

   ```css
   p {
       font-size: 16px;
   }
   ```

   *Paragraphs will have a font size of 16 pixels.*

4. **`font-weight`**: Defines the weight (boldness) of the text.

   Common values:

   - `normal`
   - `bold`

   ```css
   p {
       font-weight: bold;
   }
   ```

   *The text in paragraphs will appear in bold.*

#### **Background Properties**

1. **`background-color`**: Sets the background color of an element.

   ```css
   body {
       background-color: #f0f0f0;
   }
   ```

   *The page background will be light gray.*

2. **`background-image`**: Assigns a background image.

   ```css
   div {
       background-image: url('image.jpg');
   }
   ```

   *The div will have a background image named 'image.jpg'.*

#### **Spacing Properties**

1. **`margin`**: Controls the external space (margin) of an element.

   ```css
   h1 {
       margin-top: 20px;
       margin-bottom: 10px;
   }
   ```

   *The `<h1>` header will have a top margin of 20 pixels and a bottom margin of 10 pixels.*

2. **`padding`**: Controls the internal space (padding) of an element.

   ```css
   p {
       padding: 15px;
   }
   ```

   *Paragraphs will have 15 pixels of padding on all sides.*

#### **Dimension Properties**

1. **`width`**: Sets the width of an element.

   ```css
   img {
       width: 300px;
   }
   ```

   *All images will have a width of 300 pixels.*

2. **`height`**: Sets the height of an element.

   ```css
   img {
       height: 200px;
   }
   ```

   *All images will have a height of 200 pixels.*

#### **Border Properties**

1. **`border`**: Defines the type, width, and color of the border of an element.

   ```css
   div {
       border: 2px solid green;
   }
   ```

   *The div will have a solid green border that is 2 pixels wide.*

2. **`border-radius`**: Rounds the corners of the border.

   ```css
   img {
       border-radius: 10px;
   }
   ```

   *Images will have rounded corners with a radius of 10 pixels.*

---

### **Using `class` and `id`**

#### **`class` Attribute**

- **What is it for?**: The `class` attribute is used to assign a common name to multiple elements. This allows you to apply the same styles to all of them.

- **HTML Example:**

  ```html
  <p class="highlighted">This paragraph is highlighted.</p>
  <div class="highlighted">This div is also highlighted.</div>
  ```

- **CSS Example:**

  ```css
  .highlighted {
      color: red;
      font-weight: bold;
  }
  ```

#### **`id` Attribute**

- **What is it for?**: The `id` attribute is used to identify a unique element on the page. Each `id` must be unique within the document.

- **HTML Example:**

  ```html
  <h1 id="main-title">Welcome to my webpage</h1>
  ```

- **CSS Example:**

  ```css
  #main-title {
      color: blue;
      text-align: center;
  }
  ```

---

### **Final Example of CSS Usage**

Let's put everything we've learned into practice with a complete example.

**HTML:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Basic CSS Example</title>
    <link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
    <h1 id="main-title">My First Web Page</h1>
    <p>This is a normal paragraph.</p>
    <p class="highlighted">This paragraph is highlighted in red and bold.</p>
    <div class="box">
        <p>This is a paragraph inside a div with a gray background.</p>
    </div>
    <img src="image.jpg" alt="Example Image">
</body>
</html>
```

**CSS (`styles.css`):**

```css
/* Style for the body of the page */
body {
    background-color: #e0f7fa;
    font-family: Arial, sans-serif;
    color: #333;
}

/* Style for the main title */
#main-title {
    font-size: 28px;
    color: blue;
    text-align: center;
    margin-bottom: 20px;
}

/* Style for normal paragraphs */
p {
    font-size: 16px;
    line-height: 1.5;
}

/* Style for the 'highlighted' class */
.highlighted {
    color: red;
    font-weight: bold;
}

/* Style for the div with class 'box' */
.box {
    background-color: #f0f0f0;
    padding: 15px;
    border: 1px solid #ccc;
    border-radius: 5px;
    margin-top: 20px;
}

/* Style for images */
img {
    width: 300px;
    height: auto;
    border-radius: 10px;
    display: block;
    margin: 0 auto;
}
```

**Explanation of the Example:**

- **Body of the page (`body`)**: We set a soft background color, a readable font, and a suitable text color.
- **Main title (`#main-title`)**: We use the `id` attribute to give a unique style to the title, increasing the font size, changing the color to blue, and centering the text.
- **Normal paragraphs (`p`)**: We define the font size and line height for comfortable reading.
- **Highlighted paragraphs (`.highlighted`)**: Using the `highlighted` class, we change the text color to red and apply bold styling to highlight them.
- **Div with `box` class (`.box`)**: We create a box with a light gray background, internal padding, a subtle border, and rounded corners to enhance aesthetics.
- **Images (`img`)**: We set the width of the image, add rounded corners, and center the image on the page.

---

### **Final Tips**

- **Practice and Experiment**: Don't be afraid to experiment with different properties and values. This way, you'll discover how they affect the appearance of your page.

- **Use Meaningful Names**: When creating classes and ids, give them names that reflect their function to make the code easier to understand.

- **Keep the Code Organized**: Use comments and structure your CSS by sections. This will help keep the code clean and easy to maintain.

---

With these basic concepts, you now have the tools to start designing and styling your own web pages. **Go ahead and have fun creating!**