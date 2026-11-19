# Frontend Mentor - Recipe page solution

This is a solution to the [Recipe page challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/recipe-page-KiTsR8QQKm).

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Extra feature](#extra-feature)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [AI Collaboration](#ai-collaboration)

## Overview

### The challenge

The challenge is to build out this recipe page and get it looking as close to the design as possible.

### Extra feature

**As a** visitor of the recipe page,<br>
**I want to** see the content appear smoothly when the page opens,<br>
**so that** the page feels polished and easy to follow.

### Screenshot

#### Design preview

![Design preview for the Recipe page coding challenge](./images/preview.jpg)

#### My solution (desktop)

![Screenshot of my Recipe page solution on desktop](./images/desktop-screenshot.png)

### Links

- Repository URL: [GitHub Repo](https://github.com/MATBMS/recipe-page)
- Live Site URL: [GitHub Page](https://matbms.github.io/recipe-page/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- Mobile-first workflow

### What I learned

#### CSS counters

I learned how to number the instruction steps with CSS counters instead of the browser's default list numbers, so I can place and style the numbers exactly like the design.

Three properties work together:

- `counter-reset` creates the counter and sets it to 0. It goes on the parent (the `<ol>`).
- `counter-increment` adds 1 to the counter for each list item (`<li>`).
- `counter()` inside `content` prints the current value. It is used in the `::before` pseudo-element of each item.

```css
.steps {
  counter-reset: step;
}

.steps li {
  counter-increment: step;
}

.steps li::before {
  content: counter(step) ".";
}
```

#### Animation fill mode

I learned that `animation-fill-mode` tells the browser how an element looks before an animation starts (during its delay) and after it ends.

- `backwards` applies the first keyframe during the delay. I need it so each block stays hidden until its turn, instead of showing and then disappearing when its animation starts.
- `forwards` keeps the last keyframe after the end. I do not need it, because each block already ends in its normal state. `both` is the same as using the two together, and it would leave an empty `transform` on every block.

```css
.content > * {
  animation: fade-slide-in 1s ease-out backwards;
}
```

#### Hover only on devices with a mouse

I learned to wrap the hover effect in `@media (hover: hover)`. On a touch screen there is no real hover, so a tap could leave the photo zoomed.

```css
@media (hover: hover) {
  .photo:hover .top-image {
    transform: scale(1.05);
  }
}
```

#### Other things I learned

- **Font loading:** with `font-display: swap`, the browser shows the text right away with a fallback font and switches to my font once it is loaded, so the text is never invisible.
- **Table accessibility:** I put `scope="row"` on a `<th>` to say that it is the header of its row. A screen reader can then link "Calories" to its value.
- **Overriding a CSS variable:** I can define the same custom property in two rules. The more specific selector wins, and everything that reads it with `var()` follows, like the dot colors in the preparation box.
- **Heading outline:** I use one `<h1>` for the page title and `<h2>` for its sections, like a table of contents. Screen readers and search engines use it to understand the page.

### AI Collaboration

This is a project where I act as the Product Engineer, not the developer. I define the requirements and validate every decision, and Claude Code writes the code.
