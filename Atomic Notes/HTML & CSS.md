---
id: HTML
created_date: 2024-09-28
updated_date: 2024-09-28
type: note
tags:
  - "#webdev"
  - "#html"
  - "#css"
---

# HTML & CSS

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

