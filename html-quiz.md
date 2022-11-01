## HTML

#### Q1. What is the purpose of the `<track>` tag, and when should it be used?

- [ ] The `<track>` tag is used for specifying subtitles. It is typically applied as a child of the `<audio>`
  and `<video>` tags.
- [ ] The `<track>` tag is used for specifying subtitles. It is typically applied as a child of the `<video>` tag.
- [ ] The `<track>` tag is used for specifying subtitles, captions, and other types of time-based text. It is typically
  applied as a child of the `<video>` tag.
- [x] The `<track>` tag is used for specifying subtitles, captions, and other types of time-based text. It is typically
  applied as a child of the `<audio>` and `<video>` tag.

#### Explanation

The `<track>` tag specifies text tracks for `<audio>` or `<video>` elements.

This element is used to specify subtitles, caption files or other files containing text, that should be visible when the
media is playing.

Example: a video with subtitle tracks for two languages.

```html
<video width="320" height="240" controls>
    <source src="forrest_gump.mp4" type="video/mp4">
    <source src="forrest_gump.ogg" type="video/ogg">
    <track src="fgsubtitles_en.vtt" kind="subtitles" srclang="en" label="English">
    <track src="fgsubtitles_no.vtt" kind="subtitles" srclang="no" label="Norwegian">
</video>
```

#### Q2. What are the best examples of void elements?

- [ ] `<link><meta><title>`
- [x] `<br><base><source>`
- [ ] `<input><br><p>`
- [ ] `<area><embed><strong>`

#### Explanation

A void element is an element whose content model never allows it to have contents under any circumstances.

Void elements can have attributes. The following is a complete list of the void elements in HTML: area , base , br , col
, command , embed , hr , img , input , keygen , link , meta , param , source , track , wbr.

The `<br>` tag inserts a single line break.

The `<base>` tag specifies the base URL and/or target for all relative URLs in a document.

Example: specify a default URL and a default target for all links on a page.

```html
<head>
    <base href="https://www.w3schools.com/" target="_blank">
    <title>Base tag</title>
</head>

<body>
<img src="images/stickman.gif" width="24" height="39" alt="Stickman">
<a href="tags/tag_base.asp">HTML base Tag</a>
</body>
```

The `<source>` tag is used to specify multiple media resources for media elements, such as `<video>`, `<audio>`,
and `<picture>`.

Example: an audio player with two source files. The browser will choose the first `<source>` it supports.

```html
<audio controls>
    <source src="horse.ogg" type="audio/ogg">
    <source src="horse.mp3" type="audio/mpeg">
    Your browser does not support the audio element.
</audio>
```

#### Q3. In HTML5, which tag or tags embed a webpage inside a webpage?

- [ ] `<iframe>, <frame>, and <frameset>`
- [ ] `<frame>`
- [x] `<iframe>`
- [ ] `<frame> and <frameset>`

#### Explanation

The `<iframe>` tag specifies an inline frame.

An inline frame is used to embed another document within the current HTML document.

**Tip**: Use CSS to style the `<iframe>` (see example below).

**Tip**: It is a good practice to always include a title attribute for the `<iframe>`. This is used by screen readers to
read out what the content of the `<iframe>` is.

Example: an inline frame is marked up as follows:

```html
<iframe src="https://www.w3schools.com" title="W3Schools Free Online Web Tutorials"></iframe>
```

#### Q4. Where do `<header>` and `<footer>` tags typically occur?

- [ ] as children of `<body>, <article>, <aside>, and <section>` tags
- [x] as children of `<body>, <article>, and <section>` tags
- [ ] as children of `<body>, <article>, <aside>, <nav>, and <section>` tags
- [ ] as children of `<body>, <article>, <table>, and <section>` tags

#### Explanation

If there is a `<header>` there must be a `<footer>`.

A `<footer>` is generally found at the bottom of a document (`body` tag), a `section`, or an `article`. Just like
the <header> the content is generally meta-information, such as author details, legal information, and/or links to
related information.

#### Q5. What is the best way to apply bold styling to text?

- [x] `<strong>`
- [ ] Use CSS.
- [ ] `<bold>`
- [ ] `<b>`

#### Explanation

To make text bold in HTML, use the `<b>` … `</b>` tag or `<strong>` … `</strong>` tag.

Both the tags have the same functioning, but `<strong>` tag adds semantic strong importance to the text.

#### Q6. When is the `<link>` tag used?

- [ ] when linking style sheets, JavaScript, and icons for mobile apps
- [x] when linking style sheets, favicons, and preloading assets
- [ ] when linking one webpage to another
- [ ] when linking style sheets, external URLs, and favicons

#### Explanation

The `<link>` tag defines the relationship between the current document and an external resource.

The `<link>` tag is most often used to link to external style sheets or to add a favicon to your website.

The `<link>` element is an empty element, it contains attributes only.

#### Q7. What should fill the two blanks in the HTML code below?

```html
<address ______ _____>
    <span itemprop="streetAddress">6410 Via Real</span><br/>
    <span itemprop="addressLocality">Carpinteria</span>,
    <span itemprop="addressRegion">CA</span>
    <span itemprop="addressCode">93013</span>
</address>
```

- [x] `itemscope` `itemtype="http://schema.org/PostalAddress"`
- [ ] `itemsref="http://schema.org/PostalAddress"` `itemid="address"`
- [ ] `itemscope` `itemref="http://schema.org/PostalAddress"`
- [ ] `itemid="address"` `itemtype="http://schema.org/PostalAddress"`

#### Explanation

The `<address>` tag defines the contact information for the author/owner of a document or an article.

The `itemscope` is a boolean global attribute that defines the scope of associated metadata. Specifying the `itemscope`
attribute for an element creates a new item, which results in a number of name-value pairs that are associated with the
element.

Example:

```html
<address itemscope itemtype="schema.org/PostalAddress">
    <span itemprop="name">COMPANY NAME</span>
    <span itemprop="streetAddress">ADDRESS</span>
    <!-- more itemprop here -->
</address>
```

#### Q8. When should you use the `<aside>` element?

- [x] when the content can be removed without detracting from the page's message
- [ ] for anything you want to move to the side, like a pull quote box, a sidebar, or an image with text wrapping around
  it
- [ ] for anything in parentheses
- [ ] for anything in a sidebar

#### Explanation

The `<aside>` HTML element represents a portion of a document whose content is only indirectly related to the document's
main content.

Asides are frequently presented as sidebars or call-out boxes.

![HTML Base structure](src/html/html-base-structure.gif)

#### Q9. With which tags are the `<source>` element associated?

- [ ] `<svg>, <picture>, <audio>, and <video>`
- [x] `<picture>, <audio>, and <video>`
- [ ] It is interchangeable with the `src` attribute, so any element which uses `src` may use `<source>`
- [ ] `<audio> and <video>`

#### Explanation

The `<source>` tag is used to specify multiple media resources for media elements, such as `<video>`, `<audio>`,
and `<picture>`.

Example: an audio player with two source files. The browser will choose the first `<source>` it supports.

```html
<audio controls>
    <source src="horse.ogg" type="audio/ogg">
    <source src="horse.mp3" type="audio/mpeg">
    Your browser does not support the audio element.
</audio>
```

#### Q10. What is NOT a valid attribute for the `<textarea>` element?

- [ ] readonly
- [x] max
- [ ] form
- [ ] spellcheck

#### Explanation

The `<textarea>` tag defines a multi-line text input control.

The `<textarea>` element is often used in a form, to collect user inputs like comments or reviews.

Example: a multi-line text input control (text area).

```html
<label for="w3review">Review of W3Schools:</label>
<textarea id="w3review" name="w3review" rows="4" cols="50">
At w3schools.com you will learn how to make a website. They offer free tutorials in all web development technologies.
</textarea>
```

| Attribute   | Value            | Description                                                                     |
|-------------|------------------|---------------------------------------------------------------------------------|
| autofocus   | autofocus        | Specifies that a text area should automatically get focus when the page loads   |
| cols        | number           | Specifies the visible width of a text area                                      |
| dirname     | textareaname.dir | Specifies that the text direction of the textarea will be submitted             |
| disabled    | disabled         | Specifies that a text area should be disabled                                   |
| form        | form_id          | Specifies which form the text area belongs to                                   |
| maxlength   | number           | Specifies the maximum number of characters allowed in the text area             |
| name        | text             | Specifies a name for a text area                                                |
| placeholder | text             | Specifies a short hint that describes the expected value of a text area         |
| readonly    | readonly         | Specifies that a text area should be read-only                                  |
| required    | required         | Specifies that a text area is required/must be filled out                       |
| rows        | number           | Specifies the visible number of lines in a text area                            |
| wrap        | hard soft        | Specifies how the text in a text area is to be wrapped when submitted in a form |

The `max` attribute specifies the maximum value for an `<input>` element (not relevant for `<textarea>`).

#### Q11. What is the best way to code the sample shown?

![Sample text](src/html//q11.png?raw=true)

- [ ] A

```html
<details>
    <summary>Parmesan Deviled Eggs</summary>
    <p>
        These delectable little bites are made with organic eggs, fresh Parmesan, and chopped pine nuts.
    </p>
</details>
```

- [ ] B

```html
<h4>▸ Parmesan Deviled Eggs</h4>
<p>
    These delectable little bites are made with organic eggs, fresh Parmesan, and chopped pine nuts.
</p>
```

- [x] C

```html
<details open>
    <summary>Parmesan Deviled Eggs</summary>
    <p>
        These delectable little bites are made with organic eggs, fresh Parmesan, and chopped pine nuts.
    </p>
</details>
```

- [ ] D

```html
<details>
    <h4>▸ Parmesan Deviled Eggs</h4>
    <p>
        These delectable little bites are made with organic eggs, fresh Parmesan, and chopped pine nuts.
    </p>
</details>
```

#### Explanation

The `<details>` tag specifies additional details that the user can open and close on demand.

The `<details>` tag is often used to create an interactive widget that the user can open and close. By default, the
widget is closed. When open, it expands, and displays the content within.

Example: specify details that the user can open and close on demand.

```html
<details>
    <summary>Epcot Center</summary>
    <p>Epcot is a theme park at Walt Disney World Resort featuring exciting attractions, international pavilions,
        award-winning fireworks and seasonal special events.</p>
</details>
```

#### Q12. What is the purpose of the `<samp>` element?

- [ ] It connects the web browser to a SA-MP server.
- [ ] It identifies enclosed text as a sampler or an example.
- [x] It identifies sample output from a computer program.
- [ ] It uses a simple application messaging protocol to connect the browser to a texting device.

#### Explanation

The `<samp>` tag is used to define sample output from a computer program. The content inside is displayed in the
browser's default monospace font.

**Note**: This tag is not deprecated. However, it is possible to achieve richer effect by using CSS.

Example: define some text as sample output from a computer program in a document.

```html
<p>Message from my computer:</p>
<p><samp>File not found.<br>Press F1 to continue</samp></p>
```

#### Q13. When should you use `<ol>` and `<ul>` elements?

- [x] Use `<ul>` when you want a bulleted list and `<ol>` when you want a numbered list.
- [ ] Use `<ul>` when you have a list of items in which the order of the items matters. Use `<ol>` when you have a list
  of items that could go in any order.
- [ ] Use `<ol>` when you want a bulleted list and `<ul>` when you want a numbered list.
- [ ] Use `<ol>` when you have a list of items in which the order of the items matters. Use `<ul>` when you have a list
  of items that could go in any order.

#### Explanation

An unordered list starts with the `<ul>` tag. Each list item starts with the `<li>` tag.

The list items will be marked with bullets (small black circles) by default:

```html
<ul>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
</ul>
```

An ordered list starts with the `<ol>` tag. Each list item starts with the `<li>` tag.

The list items will be marked with numbers by default:

```html
<ol>
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
</ol>
```

#### Q14. What is the difference between the post and get methods in a form?

- [ ] post is used for sending information to the server. get is used for retrieving form information from the server.
- [ ] get is used for sending information to the server. post is used for retrieving form information from the server.
- [ ] With get, data is included in the form body when send to the server. With post, the data goes through the URL.
- [x] With post, data is included in the form body when send to the server. With get, the data goes through the URL.

#### Explanation

Both GET and POST method is used to transfer data from client to server in HTTP protocol but Main difference between
POST and GET method is that GET carries request parameter appended in URL string while POST carries request parameter in
message body.

#### Q15. What is the difference between the `<div>` and `<span>` tags?

- [x] `<div>` is used where a generic block-level tag is needed, while `<span>` is used where a generic inline tag is
  needed.
- [ ] `<div>` is used for major divisions on a page, while `<span>` is used to span across columns.
- [ ] `<div>` is the industry-standard default tag, but you could use `<span>` if you prefer.
- [ ] `<div>` is used where a generic inline tag is needed, while `<span>` is used where a generic block-level tag is
  needed.

#### Explanation

Span and div are both generic HTML elements that group together related parts of a web page. However, they serve
different functions. A div element is used for block-level organization and styling of page elements, whereas a span
element is used for inline organization and styling.

A basic example of a div element in HTML looks like this:

```html
<div id=“paragraphs”>
    <p>This is my first paragraph.</p>
    <p>This is my second paragraph.</p>
    <p>This is my final paragraph.</p>
</div>
```

A basic example of a span element in HTML looks like this:

```html
<p>This is a paragraph with <span id=“special-text”>a little something extra</span> inside it.</p>
```

#### Q16. What should fill the blank in the HTML code bellow?

```html
<form method="post" action="mailto:info@linkedin.com" ____="text/plain"></form>
```

- [x] enctype
- [ ] media
- [ ] type
- [ ] rel

#### Explanation

The `enctype` attribute specifies how the form-data should be encoded when submitting it to the server.

The `enctype` attribute can be used only if method="post".

Example:

```html
<form action=”mailto:contact@yourdomain.com” method=”POST” enctype=”text/plain” name=”EmailForm”>

    <label for="name">Name:</label><br>
    <input type="text" id="name" name="name"><br>
  
    <label for="ContactCommentt">Message:</label><br>
    <textarea id=”ContactCommentt” rows=”6″ cols=”20″>

<input type="submit" value="Send">
</form>
```

#### Q17. What is the correct markup for `alt` attribute of an image?

- [ ] A

```html
<img src="cubism.jpg" alt="Version of ""Whistler's Mother"" in cubist style">
```

- [ ] B

```html
<img src="cubism.jpg" alt="Version of "Whistler's Mother" in cubist style">
```
- [x] C
```html
<img src="cubism.jpg" alt='Version of "Whistler\'s Mother" in cubist style'>
```
- [ ] D
```html
<img src="cubism.jpg" alt="Version of \"Whistler's Mother\" in cubist style">
```

#### Q18. In the code below, what is the purpose of the **id** attribute?

```html
<p id="warning">Be careful when installing this product.</p>
```

- [x] It establishes that id is a unique identifier in the document, used for styling CSS, scripting, and linking within a webpage.
- [ ] It establishes that id is a unique identifier in the document, used for styling CSS and with Javascript code.
- [ ] It establishes that id may be used for styling CSS several times per page.
- [ ] It establishes that id is a unique identifier in the website, used for styling CSS, scripting, and linking within a webpage.

#### Explanation

The `id` attribute specifies a unique id for an HTML element. The value of the id attribute must be unique within the HTML document.

The `id` attribute is used to point to a specific style declaration in a style sheet. It is also used by JavaScript to access and manipulate the element with the specific id.

#### Q19. What is the best semantic markup for the sentence shown?

```
On July 21, 1969, Neil Armstrong said, "One small step for man, one giant leap for mankind."
```

- [x] A

```html
<p>
  On <time datetime="1969-07-21">July 21, 1969</time>, Neil Armstrong said,
  <q cite="https://www.hq.nasa.gov/alsj/a11l/a11.html"
    >One small step for man, one giant leap for mankind.</q
  >
</p>
```

- [ ] B

```html
<p>
  On July 21, 1969, Neil Armstrong said,
  <q cite="https://www.hq.nasa.gov/alsj/a11l/a11.html"
    >"One small step for man, one giant leap for mankind."</q
  >
</p>
```

- [ ] C

```html
<p>
  On July 21, 1969, Neil Armstrong said,
  <q>"One small step for man, one giant leap for mankind."</q>
</p>
```

- [ ] D

```html
<p>
  On <time datetime="07-21-1969">July 21, 1969</time>, Neil Armstrong said,
  <q cite="https://www.hq.nasa.gov/alsj/a11l/a11.html"
    >One small step for man, one giant leap for mankind.</q
  >
</p>
```

#### Explanation

The `<q>` tag defines a short quotation.

Browsers normally insert quotation marks around the quotation.

**Note**: Use `<blockquote>` for long quotations. 

Example:

```html
<p>WWF's goal is to:
<q>Build a future where people live in harmony with nature.</q>
We hope they succeed.</p>
```

The `<time>` tag defines a specific time (or datetime).

The `datetime` attribute of this element is used translate the time into a machine-readable format so that browsers can offer to add date reminders through the user's calendar, and search engines can produce smarter search results.

Example:

```html
<p>Open from <time>10:00</time> to <time>21:00</time> every weekday.</p>
<p>I have a date on <time datetime="2008-02-14 20:00">Valentines day</time>.</p>
```

#### Q20. What should fill the blank in this HTML code?

```html
<a href="https://es.yahoo.com/" hreflang="____" target="_blank">Visita Yahoo</a>
```

- [ ] es
- [ ] es-spanish
- [x] es-es
- [ ] spanish

#### Explanation

The `hreflang` attribute specifies the language of the linked document.

This attribute is only used if the href attribute is set.

**Note**: This attribute is purely advisory.

Example:

```html
<a href="https://www.w3schools.com" hreflang="en">W3Schools</a>
```

For example, for Spain the hreflang is "es-es", while for Mexico it is "es-mx".

#### Q21. Review the text in the red box in the image shown. What is the best way to code this in HTML?

![Image of footer](src/html/q21.png?raw=true)

- [ ] ordered list
- [x] unordered list inside a nav element
- [ ] ordered list inside a nav element
- [ ] unordered list

#### Explanation

The `<footer>` HTML element represents a footer for its nearest ancestor sectioning content or sectioning root element.

The `<footer>` typically contains information about the author of the section, copyright data or links to related documents.

Example:

```html
<body>
  <nav id="footer">
    <ul>
      <li><a href="#">Home</a>|</li>
      <li><a href="#">About our Hotel</a>|</li>
      <li><a href="#">Services</a>|</li>
      <li><a href="#">Photogallery</a>|</li>
      <li><a href="#">Testimonials</a>|</li>
      <li><a href="#">Locations</a>|</li>
      <li><a href="#">Contacts</a></li>
    </ul>
    <div id="copyright">
      <span>Copyright &copy; </span>
      <span>&copy; Design by <a href="" target="_blank">Best Free Templates</a></span>
    </div>
  </nav>  
</body>
```

#### Q22. What is the best way to code three choices within a form so that the user can select only one item?

- [ ] A

```html
<label for="example">Make a choice:</label>
<datalist id="example">
  <option value="Choice 1"></option>
  <option value="Choice 2"></option>
  <option value="Choice 3"></option>
</datalist>
```

- [ ] B

```html
<p>Make a choice:</p>
<input id="choices" name="example" />

<datalist value="choices">
  <option value="Choice 1"></option>
  <option value="Choice 2"></option>
  <option value="Choice 3"></option>
</datalist>
```

- [ ] C

```html
<label for="example">Make a choice:</label>
<input list="example" id="choices" name="choices" />

<datalist id="choices">
  <option value="Choice 1">Choice 1</option>
  <option value="Choice 2">Choice 2</option>
  <option value="Choice 3">Choice 3</option>
</datalist>
```

- [x] D

```html
<label for="example">Make a choice:</label>
<input list="choices" id="example" name="example" />

<datalist id="choices">
  <option value="Choice 1"></option>
  <option value="Choice 2"></option>
  <option value="Choice 3"></option>
</datalist>
```

#### Explanation

The `<datalist>` tag specifies a list of pre-defined options for an `<input>` element.

The `<datalist>` tag is used to provide an "autocomplete" feature for `<input>` elements. Users will see a drop-down list of pre-defined options as they input data.

The `<datalist>` element's id attribute must be equal to the `<input>` element's list attribute (this binds them together).

Example:

```html
<label for="browser">Choose your browser from the list:</label>
<input list="browsers" name="browser" id="browser">

<datalist id="browsers">
  <option value="Edge">
  <option value="Firefox">
  <option value="Chrome">
  <option value="Opera">
  <option value="Safari">
</datalist>
```

#### Q23. How do you confirm that a document is written in HTML5?

- [ ] The server wraps the webpage in an HTML5 wrapper.
- [x] Use the `<!DOCTYPE html>` declaration that starts the document.
- [ ] The browser receives encoding from the server to display the document with HTML5.
- [ ] It is enclosed in a `<html>` tag.

#### Q24. What does the code shown below accomplish?

```html
<picture>
  <source srcset="image1.jpg" media="(min-width: 1000px)" />
  <source srcset="image2.jpg" media="(min-width: 750px)" />
  <img src="image3.jpg" />
</picture>
```

- [x] It displays image1.jpg at 1000px and higher, image2.jpg at 750-999px, and image3.jpg at 749px and lower.
- [ ] It displays image1.jps at 1000px and higher and image2.jpg at 750-999px, image3.jpg is a default in case `<picture>` is not supported.
- [ ] It displays image1.jpg at 1000px and higher and image2.jpg at 750px and higher, image3.jpg is a default in case `<picture>` is not supported.
- [ ] It displays image1.jpg, image2.jpg and image3.jpg at 1000px and higher.

#### Explanation

The `<picture>` tag gives web developers more flexibility in specifying image resources.

The most common use of the `<picture>` element will be for art direction in responsive designs. Instead of having one image that is scaled up or down based on the viewport width, multiple images can be designed to more nicely fill the browser viewport.

The `<picture>` element contains two tags: one or more `<source>` tags and one `<img>` tag.

The browser will look for the first `<source>` element where the media query matches the current viewport width, and then it will display the proper image (specified in the srcset attribute). The `<img>` element is required as the last child of the `<picture>` element, as a fallback option if none of the source tags matches.

**Note**: The `<picture>` element works "similar" to `<video>` and `<audio>`. You set up different sources, and the first source that fits the preferences is the one being used.

Example:

```html
<picture>
  <source media="(min-width:650px)" srcset="img_pink_flowers.jpg">
  <source media="(min-width:465px)" srcset="img_white_flower.jpg">
  <img src="img_orange_flowers.jpg" alt="Flowers" style="width:auto;">
</picture>
```

#### Q25. What code will produce this table?

![Table with yellow background](src/html/q25.png?raw=true)

- [ ] A

```html
<table>
  <scope cols="2" style="background-color: yellow">
  <tr>
    <th>Col 1</th>
    <th>Col 2</th>
    <th>Col 3</th>
  </tr>
  <tr>
    <td>first</td>
    <td>second</td>
    <td>third</td>
  </tr>
</table>
```

- [x] B

```html
<table>
  <colgroup span="2" style="background-color: yellow">
  <tr>
    <th>Col 1</th>
    <th>Col 2</th>
    <th>Col 3</th>
  </tr>
  <tr>
    <td>first</td>
    <td>second</td>
    <td>third</td>
  </tr>
</table>
```

- [ ] C

```html
<table>
  <group cols="2" style="background-color: yellow">
  <tr scope="row">
    <th>Col 1</th>
    <th>Col 2</th>
    <th>Col 3</th>
  </tr>
  <tr scope="row">
    <td>first</td>
    <td>second</td>
    <td>third</td>
  </tr>
</table>
```

- [ ] D

```html
<table>
  <columns colspan="2" style="background-color: yellow">
  <tr>
    <th>Col 1</th>
    <th>Col 2</th>
    <th>Col 3</th>
  </tr>
  <tr>
    <td>first</td>
    <td>second</td>
    <td>third</td>
  </tr>
</table>
```

#### Explanation

The `<colgroup>` tag specifies a group of one or more columns in a table for formatting.

The `<colgroup>` tag is useful for applying styles to entire columns, instead of repeating the styles for each cell, for each row.

Example:

```html
<table>
  <colgroup>
    <col span="2" style="background-color:red">
    <col style="background-color:yellow">
  </colgroup>
  <tr>
    <th>ISBN</th>
    <th>Title</th>
    <th>Price</th>
  </tr>
  <tr>
    <td>3476896</td>
    <td>My first HTML</td>
    <td>$53</td>
  </tr>
</table>
```

#### Q26. What is the `<hr>`tag typically used for? / Alt.: What is the semantic meaning of the `<hr>` tag?

- [ ] This tag is depreciated (alt.: deprecated) and should not be used.
- [x] It designates a topic shift within a section at the paragraph level.
- [ ] It draws a horizontal line.
- [ ] It designates a shift of topic at the section level. / Alt.: It designates a separation of sections within an `<article>`.

#### Explanation

This is a confusing question and there can be an arguments for both the second and the third options being correct.

The `<hr>` tag defines a thematic break in an HTML page (e.g. a shift of topic).

The `<hr>` element is most often displayed as a horizontal rule that is used to separate content (or define a change) in an HTML page.

Example:

```html
<!DOCTYPE html>
<html>
<body>

<h1>The Main Languages of the Web</h1>

<p>HTML is the standard markup language for creating Web pages. HTML describes the structure of a Web page, and consists of a series of elements. HTML elements tell the browser how to display the content.</p>

<hr>

<p>CSS is a language that describes how HTML elements are to be displayed on screen, paper, or in other media. CSS saves a lot of work, because it can control the layout of multiple web pages all at once.</p>

<hr>

<p>JavaScript is the programming language of HTML and the Web. JavaScript can change HTML content and attribute values. JavaScript can change CSS. JavaScript can hide and show HTML elements, and more.</p>

</body>
</html>
```

#### Q27. What should fill the two blanks in the HTML code below?

```html
<section itemscope itemtype="http://schema.org/Restaurant">
  <h1 itemprop="name">Nadia's Garden</h1>
  <p itemscope ______ ______>
    <span itemprop="ratingValue">4.5</span> stars - based on
    <span itemprop="reviewCount">120</span> reviews
  </p>
</section>
```

- [ ] `itemprop="aggregateRating" itemref="http://schema.org/AggregateRating"`
- [x] `itemprop="aggregateRating" itemtype="http://schema.org/AggregateRating"`
- [ ] `itemid="aggregateRating" itemtype="http://schema.org/AggregateRating"`
- [ ] `itemid="aggregateRating" itemref="http://schema.org/AggregateRating"`

#### Explanation

The global attribute `itemscope` is a boolean attribute that defines the scope of associated metadata. Specifying the `itemscope` attribute for an element creates a new item, which results in a number of name-value pairs that are associated with the element.

The global attribute `itemtype` specifies the URL of the vocabulary that will be used to define `itemprop`'s (item properties) in the data structure.

```html
<div itemscope itemtype="http://schema.org/Product">
  <span itemprop="brand">ACME<br /></span>
  <span itemprop="name">Executive Anvil<br /></span>
  <img
    itemprop="image"
    src="https://pixabay.com/static/uploads/photo/2015/09/05/18/15/suitcase-924605_960_720.png"
    width="50"
    height="50"
    alt="Executive Anvil logo" /><br />

  <span itemprop="description">
    Sleeker than ACME's Classic Anvil, the Executive Anvil is perfect for the
    business traveler looking for something to drop from a height.
    <br />
  </span>

Product #: <span itemprop="mpn">925872<br /></span>
<span
itemprop="aggregateRating"
itemscope
itemtype="http://schema.org/AggregateRating">
Rating: <span itemprop="ratingValue">4.4</span> stars, based on
<span itemprop="reviewCount">89 </span> reviews
</span>
  <p>
    <span itemprop="offers" itemscope itemtype="http://schema.org/Offer">
      Regular price: $179.99<br />
      <meta itemprop="priceCurrency" content="USD" />
      <span itemprop="price">Sale price: $119.99<br /></span>
      (Sale ends
      <time itemprop="priceValidUntil" datetime="2020-11-05"> 5 November!</time>)<br />
      Available from:
      <span
        itemprop="seller"
        itemscope
        itemtype="http://schema.org/Organization">
        <span itemprop="name">Executive Objects<br /></span>
      </span>
      Condition:
      <link
        itemprop="itemCondition"
        href="http://schema.org/UsedCondition" />Previously owned, in excellent
      condition<br />
      <link itemprop="availability" href="http://schema.org/InStock" />In stock!
      Order now!
    </span>
  </p>
</div>
```

#### Q28. Which HTML snippet links back to the very top of a webpage?

- [x] A

```html
<a id="top"></a>

<!-- placed at the top of the page -->

<a href="#top">back to top</a>
```

- [ ] B

```html
<a name="top"></a>

<!-- placed at the top of the page -->

<a href="#top">back to top</a>
```

- [ ] C

```html
<a href="#">back to top</a> <a href="#top">back to top</a>
```

- [ ] D

```html
<button href="#">back to top</button> <button href="#top">back to top</button>
```

#### Explanation

To create a link that goes to the top of a web page, follow the steps below.

In your HTML code, find the opening `<body>` tag (this should be located right after the closing `</head>` tag). Immediately after the opening `<body>` tag, add the following code.

```html
<a id="top"></a>
```

The code above creates an anchor on the page named top.

Next, add the top of page link using the `#` symbol and "top" anchor id as the value of the `href` attribute, as shown below.

```html
<a href="#top">Back to top of page</a>
```

**Note**: All modern browsers understand the `#top` value. Even if the `id` anchor is not used, you still return to the top of the page. However, all other anchors need to be defined in the page.

#### Q29. Which three tags where deprecated in HTML4 but returned to HTML5?

- [x] `<rb> <rp> <rt>`
- [ ] `<acronym> <code> <wbr>`
- [ ] `<hgroup> <q> <wbr>`
- [ ] `<b> <i> <u>`

#### Q30. The **\_** tag is used for marking up a short code snippet, while the \_ tag is used for marking up a longer block of code

- [ ] `<kdb>`, `<pre>`
- [ ] `<pre>`, `<code>`
- [ ] `<kdb>`, `<mark>`
- [x] `<code>`, `<pre>`

#### Explanation

The `<pre>` tag defines preformatted text.

Text in a `<pre>` element is displayed in a fixed-width font, and the text preserves both spaces and line breaks. The text will be displayed exactly as written in the HTML source code.

Example:

```html
<!DOCTYPE html>
<html>
<body>

<h2>Standard pre</h2>
<pre>This is a standard pre. It will use as much space as it needs.</pre>

<h2>Fixed width pre</h2>
<div style="width:200px;overflow:auto">
  <pre>This is a pre with a fixed width. It will use as much space as specified.</pre>
</div>

</body>
</html>
```

The `<code>` tag is used to define a piece of computer code. The content inside is displayed in the browser's default monospace font.

```html
<!DOCTYPE html>
<html>
<head>
<style>
code {
  font-family: Consolas,"courier new";
  color: crimson;
  background-color: #f1f1f1;
  padding: 2px;
  font-size: 105%;
}
</style>
</head>
<body>

<h1>The code element + CSS</h1>

<p>The HTML <code>button</code> tag defines a clickable button.</p>
<p>The CSS <code>background-color</code> property defines the background color of an element.</p>

</body>
</html>
```

#### Q31. What does the `<label>` element do?

- [ ] It labels webpages with important information.
- [ ] It creates an ID for a corresponding input element.
- [ ] It overrides the name attribute's value on a child input element.
- [x] It programmatically associates a text label with an interface element.

#### Explanation

The `<label>` tag defines a label for several elements:

- `<input type="checkbox">`
- `<input type="color">`
- `<input type="date">`

... and others.

Proper use of labels with the elements above will benefit:

1. Screen reader users (will read out loud the label, when the user is focused on the element)
2. Users who have difficulty clicking on very small regions (such as checkboxes) - because when a user clicks the text within the <label> element, it toggles the input (this increases the hit area). 

Example:

```html
<form action="/action_page.php">
  <input type="radio" id="html" name="fav_language" value="HTML">
  <label for="html">HTML</label><br>
  <input type="radio" id="css" name="fav_language" value="CSS">
  <label for="css">CSS</label><br>
  <input type="radio" id="javascript" name="fav_language" value="JavaScript">
  <label for="javascript">JavaScript</label><br><br>
  <input type="submit" value="Submit">
</form>
```

#### Q32. To get a link to open in a new window or tab, use the **\_** attribute

- [x] `_blank`
- [ ] `_self`
- [ ] `_new`
- [ ] `_parent`

#### Explanation

The `target` attribute specifies where to open the linked document.

| Value      | Description                                                                     |
|------------|---------------------------------------------------------------------------------|
| **_blank** | **Opens the linked document in a new window or tab**                            |
| _self      | Opens the linked document in the same frame as it was clicked (this is default) |
| _parent    | Opens the linked document in the parent frame                                   |
| _top       | Opens the linked document in the full body of the window                        |
| framename  | Opens the linked document in the named iframe                                   |


#### Q33. What is the most semantically accurate way to mark up the sentence shown below? Note: "TLAs" stands for "three-letter acronyms."

**We are fond of our TLAs in web design.**

- [ ] A

```html
<p>We are fond of our <span title="three-letter acronyms">TLAs</span> in web design.</p>
```

- [ ] B

```html
<p>We are fond of our TLAs in web design.</p>
```

- [x] C

```html
<p>we are fond of our <abbr title="three-letter acronyms">TLAs</abbr> in web design.</p>
```

- [ ] D

```html
<p>we are fond of our <acronym title="three-letter acronym">TLAs</acronym> in web design.</p>
```

`<acronym>` has been removed in HTML5 and shouldn't be used anymore. Instead web developers should use the `<abbr>` element.

#### Explanation

The `<abbr>` tag defines an abbreviation or an acronym, like "HTML", "CSS", "Mr.", "Dr.", "ASAP", "ATM".

```html
<!DOCTYPE html>
<html>
<body>

<h1>The abbr element</h1>

<p>The <abbr title="World Health Organization">WHO</abbr> was founded in 1948.</p>

</body>
</html>
```

#### Q34. What is the correctly nested markup for this list?

![Sample list](src/html/q34.png?raw=true)

- [ ] A

```html
<ul>
  <li>
    office
    <ol style="circle">
      <li>staple</li>
      <li>paper</li>
    </ol>
  </li>
  <li>
    groceries
    <ol style="circle">
      <li>milk</li>
    </ol>
  </li>
</ul>
```


- [x] B

```html
<ul>
  <li>
    Office Supplies
    <ul>
      <li>Stapler</li>
      <li>Paper clips</li>
    </ul>
  </li>
  <li>
    Groceries
    <ul>
      <li>Milk</li>
    </ul>
  </li>
</ul>
```

- [ ] C

```html
<ul>
  <li>office</li>
  <li>staple</li>
  <li>paper</li>
  <li>groceries</li>
  <li>milk</li>
</ul>
```

#### Explanation

A nested list or a sublist is a list within a list. The trick to marking nested lists up correctly in HTML is to recognize that the sublist is actually a child of a list item and not of a list.

Start by creating a list. It can be ordered or unordered:

```html
<ul>
  <li>Fruit</li>
  <li>Vegetables</li>
  <li>Meat</li>
</ul>
```

Now add a nested list to the first list item:

```html
<ul>
  <li>Fruit
    <ul>
      <li>Bananas</li>
      <li>Apples</li>
      <li>Pears</li>
    </ul>
  </li>
  <li>Vegetables</li>
  <li>Meat</li>
</ul>
```

Notice that the sublist is a child and not a sibling of an `<li>` tag.

#### Q35. What should fill the blank below?

```html
<link href="phone.css" rel="stylesheet" _____="print" />
```

- [ ] title
- [ ] type
- [ ] device
- [x] media

#### Explanation

The `media` attribute specifies what media/device the target resource is optimized for.

This attribute is mostly used with CSS style sheets to specify different styles for different media types.

The `media` attribute can accept several values.

Example:

```html
<head>
  <link rel="stylesheet" type="text/css" href="theme.css">
  <link rel="stylesheet" type="text/css" href="print.css" media="print">
</head>
```

#### Q36. What is the semantically correct way to mark up this layout?

![quote](src/html/q36.png?raw=true)

- [ ] A

```html
<p>
  "Making money is what you have to do to sustain a business—being driven to make something of value
  and purpose is much more powerful."
</p>
<p><em>Lynda Weinman</em></p>
```

- [ ] B

```html
<blockquote>
  <q
    >"Making money is what you have to do to sustain a business—being driven to make something of
    value and purpose is much more powerful."</q
  >
  <cite><em>Lynda Weinman</em></cite>
</blockquote>
```

- [x] C

```html
<blockquote>
  <p>
    "Making money is what you have to do to sustain a business—being driven to make something of
    value and purpose is much more powerful."
  </p>
  <cite>Lynda Weinman</cite>
</blockquote>
```

- [ ] D

```html
<section>
  <q
    >"Making money is what you have to do to sustain a business—being driven to make something of
    value and purpose is much more powerful."</q
  >
  <cite>Lynda Weinman</cite>
</section>
```

#### Explanation

The `<blockquote>` tag specifies a section that is quoted from another source.

Browsers usually indent `<blockquote>` elements (look at example below to see how to remove the indentation).

Example:

```html
<!DOCTYPE html>
<html>
<body>

<h1>The blockquote element</h1>

<p>Here is a quote from WWF's website:</p>

<blockquote cite="http://www.worldwildlife.org/who/index.html">
For 50 years, WWF has been protecting the future of nature. The world's leading conservation organization, WWF works in 100 countries and is supported by 1.2 million members in the United States and close to 5 million globally.
</blockquote>

</body>
</html>
```

#### Q37. Which choice uses the correct terminology in describing this markup: `<p>info</p>`?

- [ ] The element opener is `<p>`, the element closer is `</p>`, and the element information is info.
- [ ] The start tag is `<p>`, the end tag is `</p>`, and the enclosed HTML is info.
- [x] The start tag is `<p>`, the end tag is `</p>`, and the element content is info.
- [ ] The start element is `<p>`, the end element is `</p>`, and the tag content is info.

#### Q38. What is the difference between `<input type="submit" value="click me">` and `<button type="submit">Click me</button>`?

- [ ] There is no difference. Both will render a button that submits a form.
- [x] Both will submit a form. However, the `<button>` can have content other than text, like an image or nested HTML elements, while the `<input>` cannot.
- [ ] `<input type="button">` has been deprecated in HTML5. You should use the `<button>` tag instead.
- [ ] Both will submit a form. However, the `<input>` can have content other than text, like an image or nested HTML elements, while the `<button>` cannot.

#### Explanation

Both `<button type="submit">` and `<input type="submit">` display as buttons and cause the form data to be submitted to the server.

The difference is that `<button>` can have content, whereas `<input>` cannot (it is a null element).

#### Q39. What is the best semantic way to indicate that text refers to keyboard entry?

- [ ] `<p>Press the <tt>Enter</tt> key to proceed.</p>`
- [x] `<p>Press the <kbd>Enter</kbd> key to proceed.</p>`
- [ ] `<p>Press the <samp>Enter</samp> key to proceed.</p>`
- [ ] `<p>Press the Enter key to proceed.</p>`

#### Explanation

The `<kbd>` tag is used to define keyboard input. The content inside is displayed in the browser's default monospace font.

#### Q40. What does this code do?

```html
<audio controls>
  <source src="sound.mp3" type="audio/mpeg" />
  <source src="sound.ogg" type="audio/ogg" />
  <source src="sound.wav" type="audio/wav" />
</audio>
```

- [x] The browser chooses the first supported format to play with the browser's default controls.
- [ ] The browser chooses the best audio format to play with JavaScript-provided controls.
- [ ] The browser plays each sound file in order automatically. The user has controls to stop playback.
- [ ] The browser chooses the first supported sound file and will loop the sound until the user stops it.

#### Explanation

The `src` attribute specifies the location (URL) of the audio file.

The example above uses an Ogg file, and will work in Firefox, Opera, Chrome, and Edge. However, to play the audio file in IE or Safari, we must use an MP3 file.

To make it work in all browsers - use `<source>` elements inside the `<audio>` element.

Each `<source>` element can link to different audio files. The browser will use the first recognized format:

```html
<audio controls>
  <source src="horse.ogg" type="audio/ogg">
  <source src="horse.mp3" type="audio/mpeg">
  Your browser does not support the audio tag.
</audio>
```