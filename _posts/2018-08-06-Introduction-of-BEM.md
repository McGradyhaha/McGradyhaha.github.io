---
layout: post
author: WhyK
comments: true
date: 2018-08-06 18:05:32+10:00
tags: [css, Methodology]
title: Introduction of BEM (Blcok, Element, Modifier)
---

<hr style="filter: alpha(opacity=100,finishopacity=0,style=3);" />
### Introduction
On smaller brochure sites, how you organize your styles isn’t usually a big concern. You get in there, write some CSS, or maybe even some SASS. You compile it all into a single stylesheet with SASS’s production settings, and then you aggregate it to get all the stylesheets from modules into a nice tidy package.

However, when it comes to larger, more complex projects, how you organize your code is the key to efficiency in at least these three ways: it affects how long it takes you to write code, how much of that code you’ll have to write and how much loading your browser will have to do. This becomes especially important when you’re working with teams of themers, and when high performance is essential.

### Blocks, Elments and Modifiers
* Block: Standalone entity that is meaningful on its own.
Examples: `header`, `containder`, `menu`, `checkbox`, `input` 
* Element: A part of a block that has no standalone meaning and is semantically tied to its block. Examples: `menu item`, `list item`, `checkbox caption`, `header title`
* Modifier: A flag on a block or element. Use them to change appearance or behavior. Examples: `disabled`, ` highlighted`, `checked`, `fixed`, `size big`, `color yellow`

### Example of BEM
Let’s look how one particular element on a page can be implemented in BEM. We will take `button` from GitHub:

![example](http://getbem.com/assets/github_buttons.jpg)

We can have a normal button for usual cases, and two more states for different ones. Because we style blocks by class selectors with BEM, we can implement them using any tags we want (`button`, `a` or even `div`). The naming rules tell us to use `block--modifier-value` syntax.
#### 1. HTML
```html
<button class="button">
	Normal button
</button>
<button class="button button--state-success">
	Success button
</button>
<button class="button button--state-danger">
	Danger button
</button>
```
#### 2. CSS
```css
.button {
	display: inline-block;
	border-radius: 3px;
	padding: 7px 12px;
	border: 1px solid #D5D5D5;
	background-image: linear-gradient(#EEE, #DDD);
	font: 700 13px/18px Helvetica, arial;
}
.button--state-success {
	color: #FFF;
	background: #569E3D linear-gradient(#79D858, #569E3D) repeat-x;
	border-color: #4A993E;
}
.button--state-danger {
	color: #900;
}
```
### Naming of BEM
#### 1. Blcok
* Naming: Block names may consist of Latin letters, digits, and dashes. To form a CSS class, add a short prefix for namespacing: `.block`
* HTML: Any DOM node can be a block if it accepts a class name.
```html
<div class="block">...</div>
```
* CSS:
a. Use class name selector only 
b. No tag name or ids c. No dependency on other blocks/elements on a page
```css
.block { color: #042; }
```

#### 2. Element
Parts of a block and have no standalone meaning. Any element is semantically tied to its block.

* Naming: Element names may consist of Latin letters, digits, dashes and underscores. CSS class is formed as block name plus two underscores plus element name: `.block__elem`
* HTML: Any DOM node within a block can be an element. Within a given block, all elements are semantically equal.
```html
<div class="block">
	  ...
	  <span class="block__elem"></span>
	</div>
```
* CSS:
a. Use class name selector only 
b. No tag name or ids 
c. No dependency on other blocks/elements on a page

```css
/* Good Example */
.block__elem { color: #042; }

/* Bad Example */
.block .block__elem { color: #042; }
	div.block__elem { color: #042; }
```
#### 3. Modifier
Flags on blocks or elements. Use them to change appearance, behavior or state.

* Naming: Modifier names may consist of Latin letters, digits, dashes and underscores. CSS class is formed as block’s or element’s name plus two dashes: `.block--mod` or `.block__elem--mod` and `.block--color-black` with `.block--color-red`. Spaces in complicated modifiers are replaced by dash.
* HTML: Modifier is an extra class name which you add to a block/element DOM node. Add modifier classes only to blocks/elements they modify, and keep the original class:
```html
<!-- Good Example -->
<div class="block block--mod">...</div>
	<div class="block block--size-big
		block--shadow-yes">...</div>
<!-- Bad Example -->
<div class="block--mod">...</div>
```
* CSS:
a. Use modifier class name as selector b. To alter elements based on a block-level modifier
c. Element modifier
```css
.block--hidden { }
.block--mod .block__elem { }
.block__elem--mod { }
```
### Example of BEM
Suppose you have block form with modifiers `theme: "xmas"` and `simple: true` and with elements `input` and `submit`, and element submit with its own modifier `disabled: true` for not submitting form while it is not filled:

#### 1. HTML
```html
<form class="form form--theme-xmas form--simple">
  <input class="form__input" type="text" />
  <input
    class="form__submit form__submit--disabled"
    type="submit" />
</form>
```
#### 2. CSS
```css
.form { }
.form--theme-xmas { }
.form--simple { }
.form__input { }
.form__submit { }
.form__submit--disabled { }
```