---
id: HTML
created_date: 2024-09-28
updated_date: 2024-09-28
type: note
tags:
  - "#webdev"
  - "#html"
---

# HTML

## Elements and Tags

HTML (HyperText Markup Language) defines the structure and content of web pages using elements and tags. Most elements on an HTML page are pieces of content wrapped in opening and closing HTML tags. A paragraph opening and closing tag looks like this.

```html
<p>hello world</p>
```

HTML has many [predefined](https://developer.mozilla.org/en-US/docs/Web/HTML/Element) tags that can be used to create different different elements in in page. Using the correct tags is important, it impacts two aspects of a website: search engine rankings; and how accessible the site is to users who rely on assistive technologies.

**Void Elements**

Some elements do not have a closing tag such as `<br>`, these are called void elements.

## HTML Boilerplate

All HTML docs use the same basic structure. To create a HTML file use the `.html` extension. The homepage of the site should always be in `index.html` because web servers look for `index.html` by default.

### DOCTYPE

Every HTML page starts with a doctype declaration. The doctype's purpose is to tell the browser what version of HTML it should use to render the document. For the latest version of HTML use `<!DOCTYPE html>`.

### HTML Element

After the declaring the doctype we need to provide an HTML element. This is known as the root element of the document.

```html
<!DOCTYPE html>
<html lang="en">
</html>
```

### Head Element

The `<head>` element contains important meta-information about our webpages and stuff required to render in the browser. We should not use any element that displays content on the webpage inside the `<head>` element.

```html
<!DOCTYPE html>

<html lang="en">
	<head>
		<meta charset="UTF-8">
		<title>My First Webpage</title>
	</head>
</html>
```

The `<meta>` tag contains the charset encoding of the webpage in the `<head>` element. The `<title>` element isused to give webpages a readable title displayed on the browser tab.

### Body Element

The  `<body>` element is the final tab to complete the boilerplate. This tag contains the HTML content of the website.

```html
<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8">
	<title>My First Webpage</title>
</head>

<body>
	<p>Hello World!</p>
</body>

</html>
```

## Responsive Design

A responsive site is characterized by a web page that can conform to the devices screen. This is especially useful today when screens can vary all different aspect ratios, resolutions, and sizes.

```html
<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8" name="viewport" content="width=device-width, intial-scale=1.0">
	<title>My Other Webpage</title>
</head>

<body>
	<p>Hello World!</p>
</body>

</html>
```

This gives the page access to its width enabling you to style elements based on it. For example to style an image differently based on the width of the page in CSS create a new image tag with the style property.

```html
<img src="my_image.png" style="width:80%;">
```

You can also show different pictures based on the browser width using the `max-width` property.

```html
<picture>
	<source srcset="img_1.png" media="(max-width: 600px)">
	<source srcset="img_2.png" media="(max-width: 1500px)">
	<source srcset="img_3.png">
</picture>
```

To create responsive text you can use the `vw` unit when styling which refers to viewport width as a percentage (1vw = 1% of the viewport width).

```html
<h1 style="font-size:10vw">Hello World!</h1>
```

This is not a comprehensive list of how to create a responsive website but the key takeaway is that everything is styled relative to the size of the screen.