# HTML/CSS 1

---

## Contents

- [Semantic HTML tags](#html-syntax)
- [CSS selectors, CSS cascade, Pseudo-classes such as `:hover`/`:focus`](#css-selectors)
- [Box model: `margin`/`padding`/`border` etc...](#box-model)

---

## Learning Objectives

Learning objectives for this lesson can be found [here](./learning-objectives.md)

---

## What makes a web page?

![What makes a web page](../assets/webpage-parts.png)

## HTML Syntax

You're already familiar with HTML code from your application process. If you want to refresh your memory, read this [quick guide to the HTML syntax](http://marksheet.io/html-syntax.html).

All together, let's review the basic syntax in the following example:

```html
<article>
  <h1>Learning HTML</h1>
  <p>Get to know the HTML basics.</p>
  <a href="http://html5rocks.com">Read Article</a>
</article>
```

> **Question** Which parts are the **Tags** and which parts are the **Attributes**?.

HTML tags are arranged in a hierarchy. This is sometimes called "nesting" tags or creating an HTML "tree". Between the opening `<article>` tag and the closing `</article>` tag there are three other tags. We call these "child" tags, because they have a parent-child relationship.

![HTML Hierarchy](../assets/html-hierarchy.png)

> **Question** As a group, let's try to name all of the parent and child tags in the following example.

```html
<article>
  <h1>Learning HTML</h1>
  <p>
    <span class="author">Author:</span>
    <a href="http://codeyourfuture.io">Code Your Future</a>
  </p>
  <p>Get to know the HTML basics.</p>
  <a href="http://html5rocks.com">Read Article</a>
</article>
```

## Example HTML/CSS Project

In today's class, we will begin adapting styles on this example website. We'll review some of the HTML/CSS basics you already encountered during your application process and learn some new techniques. By the end of the third lesson, we will have worked together to improve the example site on the left so that it looks like the screenshot on the right.

<a href="../assets/screenshot-start.png" target="blank">
  <img src="../assets/screenshot-start.png" style="border: 1px solid #bababa; width: 48%; max-height: 293px">
</a>
<a href="../assets/screenshot-complete.png" target="blank">
  <img src="../assets/screenshot-complete.png" style="border: 1px solid #bababa; width: 48%;">
</a>

> **Exercise**: Fork the [HTML/CSS exercises](https://github.com/Migracode-Barcelona/html-css-git-exercises) repository to your personal account and clone it. Find in the [Migracode GIT Guide](/others/git.html#fork-and-clone-an-existing-project-from-github) the instructions

> **Exercise**: Spend a few minutes exploring the `.html` and `.css` files for this page. Why don't we put everything in one file?

## Semantic HTML

When writing HTML code, you can use different tags to describe the content. Is it a navigation menu, a paragraph of text, or an article? By using the correct tag, you help search engines like Google or screen readers for the visually impaired.

> Semantic HTML is the use of HTML markup to reinforce the semantics, or **meaning**, of the information in webpages and web applications rather than merely to define its presentation or look. [Wikipedia](https://en.wikipedia.org/wiki/Semantic_HTML)

We'll cover the following semantic tags:

- `<header>`
- `<footer>`
- The `role="main"` attribute
- `<nav>`
- `<article>`
- `<aside role="complementary">`

> **Exercise (pair programming):** Work in pairs to determine where to place these new Tags and Attributes in the index.html file. Who benefits when we write "semantic" HTML?

## CSS Selectors

During your application process, you became familiar with CSS selectors. We'll review the basic selectors and then practice combining these to modify our button styles.

> If you want to review the selectors, read the [Common Selectors section](http://learn.shayhowe.com/advanced-html-css/complex-selectors/) of this page.

> **Exercise (pair programming):** Work in pairs to make the blue buttons on the page red (`#ce5f31`). The white button, which says "Volunteer", should remain white but the text should change to red.

## Pseudo Classes

You can assign CSS rules to a class like this:

```css
.btn {
  background: #ce5f31;
}
```

There are also things called "pseudo" classes. In this section, we'll introduce you to the common pseudo classes for assigning styles to interactions, such as moving your mouse over a link.

> "pseudo" is a fancy word for "fake". We call them "pseudo" classes because they're not really there in the HTML, but the browser knows what to do with them.

Here's an example of a pseudo class which changes the color of a link when the mouse moves over it.

```css
.btn:hover {
  background: #ef7f52;
}
```

Not everyone uses a mouse. Some users will prefer a keyboard, where they can hit `tab` to move between links on a page. So that they can see where they are, you should add effects to the `:focus` pseudo class too.

```css
.btn:hover,
.btn:focus {
  background: #ef7f52;
}
```

> **Exercise:** Work in pairs and use the pseudo classes to make the background color of the red buttons change when in a "hover" or "focus" state. See if you can make the white "Volunteer" button change to a different background without effecting the red buttons.

## Box Model

In CSS, everything is a box. An image is a box. A link is a box. The area around this box can be modified with properites that we call margins, borders and padding. Here's a diagram showing what the box looks like.

![Box Model. Source: MDN](https://mdn.mozillademos.org/files/13647/box-model-standard-small.png)

> **Exercise:** Work in pairs and use the `margin` and `padding` rules to spread your navigation links out a bit wider. There should be a small gap between them and enough padding so that the border is not too tight on the text.

You may have noticed that the border you added to the navigation links causes the links to jump around when you move your mouse over them. That's because the border is adding to the width of the box model, pushing the others to the side.

You can also set a transparent border, so that it takes up the space without showing a visible border.

```css
.navlink {
  border: 1px solid transparent;
}
```

> **Exercise:** Use a transparent border so that the width of each navigation menu item stays the same even when it is hovered or focused.

{% include "./homework.md" %}

# Resources

1. [HTML5 - semantic elements](https://developer.mozilla.org/en/docs/Web/Guide/HTML/HTML5)
2. [CSS Selectors - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors)
3. [The Cascade - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Cascade)
4. [Box Model - MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Box_model)
5. [Box Model, box-sizing: border-box - CSS Tricks](https://css-tricks.com/international-box-sizing-awareness-day/)
6. [CSS specificity - MDN](https://developer.mozilla.org/en/docs/Web/CSS/Specificity)
7. [Pseudo classes - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)
