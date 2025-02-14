--- 
title: "HTML Guide" 
style: styles.css 
---

# **HTML Guide 1**

## **What is HTML?**

HTML (HyperText Markup Language) is the standard language for creating web pages. It defines the structure and content of a web page using tags. Each tag has a specific function and helps organize and format the content.

## **How does HTML work?**

HTML uses tags to define different elements within a web page. These tags come in pairs, with an opening tag and a closing tag. For example, the tag for a paragraph is written like this:
```html
<p>This is a paragraph.</p>
```
In this case, `<p>` is the opening tag indicating the start of the paragraph, and `</p>` is the closing tag indicating the end of the paragraph.

## **Basic Content Formatting Tags**

1. **Bold**
   ```html
   <b>Bold text</b>
   ```
   The `<b>` tag is used to make text bold. The opening `<b>` and closing `</b>` tags wrap the text you want to emphasize.
   - **Alternative:** The `<strong>` tag is also used to emphasize text with strong importance:
     ```html
     <strong>Strong text</strong>
     ```

2. **Italic**
   ```html
   <i>Italic text</i>
   ```
   The `<i>` tag is used to italicize text. It wraps the text with opening `<i>` and closing `</i>` tags.
   - **Alternative:** The `<em>` tag is used to emphasize text, giving it emphasized meaning:
     ```html
     <em>Emphasized text</em>
     ```

3. **Underline**
   ```html
   <u>Underlined text</u>
   ```
   The `<u>` tag is used to underline text, wrapping it with `<u>` and `</u>`.

4. **Strikethrough**
   ```html
   <s>Strikethrough text</s>
   ```
   The `<s>` tag is used to strikethrough text, wrapping it with `<s>` and `</s>`.

5. **Highlight**
   ```html
   <mark>Highlighted text</mark>
   ```
   The `<mark>` tag is used to highlight text.

6. **Subscript**
   ```html
   <sub>Subscript text</sub>
   ```
   The `<sub>` tag is used to create subscript text, which appears slightly below the normal text line.

7. **Superscript**
   ```html
   <sup>Superscript text</sup>
   ```
   The `<sup>` tag is used to create superscript text, which appears slightly above the normal text line.

## **Structuring**

1. **Header**
   ```html
   <header>
     <h1>Welcome to my website</h1>
   </header>
   ```
   The `<header>` tag is used to define the header section of the page, often including titles and logos. Within `<header>`, you can use `<h1>` to indicate the main title.

2. **Footer**
   ```html
   <footer>
     <p>&copy; 2025 My Website</p>
   </footer>
   ```
   The `<footer>` tag is used to define the footer of the web page, usually containing contact information, copyright notices, etc. In this example, `<p>` is used to add a paragraph within the footer.

3. **Sections**
   ```html
   <section>
     <h2>Content Section</h2>
     <p>Section content.</p>
   </section>
   ```
   The `<section>` tag is used to define sections of the page that contain thematically related content. Inside `<section>`, `<h2>` defines a subheading, and `<p>` adds a paragraph.

4. **Article**
   ```html
   <article>
     <h2>Article Title</h2>
     <p>This is an article.</p>
   </article>
   ```
   The `<article>` tag is used to represent a self-contained composition in a document, such as a blog post or news article.

5. **Navigation**
   ```html
   <nav>
     <ul>
       <li><a href="#home">Home</a></li>
       <li><a href="#about">About</a></li>
       <li><a href="#contact">Contact</a></li>
     </ul>
   </nav>
   ```
   The `<nav>` tag is used to define navigation links.

6. **Main**
   ```html
   <main>
     <h2>Main Content</h2>
     <p>This is the main content of the page.</p>
   </main>
   ```
   The `<main>` tag is used to specify the main content of a document. The content inside the `<main>` tag should be unique to the document and not contain sidebars, footer, or header content.

## **Tags for Creating Paragraphs, Tables, Lists, and Links**

1. **Paragraphs**
   ```html
   <p>This is a paragraph.</p>
   ```
   The `<p>` tag is used to define paragraphs in the content. Each block of text you want to separate into a paragraph should be within `<p>` and `</p>`.

2. **Tables**
   ```html
   <table>
     <tr>
       <th>Header 1</th>
       <th>Header 2</th>
     </tr>
     <tr>
       <td>Cell 1</td>
       <td>Cell 2</td>
     </tr>
   </table>
   ```
   - `<table>` defines the start and end of the table.
   - `<tr>` is used to define a row of the table.
   - `<th>` is used to define header cells.
   - `<td>` is used to define data cells.

3. **Lists**
   - **Unordered List**
     ```html
     <ul>
       <li>Item 1</li>
       <li>Item 2</li>
       <li>Item 3</li>
     </ul>
     ```
     - `<ul>` defines an unordered list.
     - `<li>` defines each list item.
   
   - **Ordered List**
     ```html
     <ol>
       <li>Item 1</li>
       <li>Item 2</li>
       <li>Item 3</li>
     </ol>
     ```
     - `<ol>` defines an ordered list.
     - `<li>` defines each list item.

4. **Description List**
   ```html
   <dl>
     <dt>Term 1</dt>
     <dd>Description for Term 1</dd>
     <dt>Term 2</dt>
     <dd>Description for Term 2</dd>
   </dl>
   ```
   - `<dl>` defines a description list.
   - `<dt>` defines a term in the description list.
   - `<dd>` defines the description of the term.

5. **Links**
   ```html
   <a href="https://www.example.com">Visit Example.com</a>
   ```
   The `<a>` tag is used to create links. The `href` attribute defines the URL of the link, and the text between `<a>` and `</a>` is what is shown as the clickable link.

6. **Image**
   ```html
   <img src="image.jpg" alt="Description of image">
   ```
   The `<img>` tag is used to embed an image in a web page. The `src` attribute specifies the path to the image, and the `alt` attribute provides an alternative text description of the image.

## **Conclusion**

HTML is the fundamental building block for creating web pages. By understanding these basic tags and how they work, you can start to structure and format your own web content. Have fun experimenting and creating!
