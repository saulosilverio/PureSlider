# PureSlider

### A simple and responsive slider using HTML and advanced CSS techniques.

## Table of contents

- [Introduction](#introduction)
- [Why use PureSlider?](#why-use-pureslider)
- [Adding PureSlider to your project](#adding-pureslider-to-your-project)
- [Customizing PureSlider](#customizing-pureslider)


## Introduction

This slider component was developed to meet the simple demand of having a light and responsive image carousel without the need to use a complex javascript library. 

## Why use PureSlider?

Slider libraries are usually quite complex and full of configuration options. That's not the point of PureSlider, the idea is that you can create a simple image carousel without relying on 3rd party libraries.

## Adding PureSlider to your project
With very little programming knowledge and few lines of code you can start using Pureslider on your pages.

### HTML
Add the following HTML code where you want the slider component to appear.

```html
<div class="ps-wrapper">
    <div id="psContainer" class="ps-items">
        <div class="ps-item"><img src="https://picsum.photos/1366/768?grayscale&random=1"/></div>
        <div class="ps-item"><img src="https://picsum.photos/1366/768?grayscale&random=2"/></div>
        <div class="ps-item"><img src="https://picsum.photos/1366/768?grayscale&random=3"/></div>
        <div class="ps-item"><img src="https://picsum.photos/1366/768?grayscale&random=4"/></div>
        <div class="ps-item"><img src="https://picsum.photos/1366/768?grayscale&random=5"/></div>
        <div class="ps-item"><img src="https://picsum.photos/1366/768?grayscale&random=6"/></div>
        <div class="ps-item"><img src="https://picsum.photos/1366/768?grayscale&random=7"/></div>
        <div class="ps-item"><img src="https://picsum.photos/1366/768?grayscale&random=8"/></div>
        <div class="ps-item"><img src="https://picsum.photos/1366/768?grayscale&random=9"/></div>
        <div class="ps-item"><img src="https://picsum.photos/1366/768?grayscale&random=10"/></div>
    </div>
</div>
```

### CSS
PureSlider utilizes some advanced CSS properties to provide smooth transitions and improve user experience. As it is developed using primarily CSS, the PureSlider is compatible with most modern browsers.

```css
.ps-wrapper {
    width: 100vw;
}
.ps-wrapper img {
    height: 100%;
    width: 100%;
    object-fit: cover;
}
.ps-items {
    display: flex;
    gap: 2rem;
    align-items: flex-end;
    overflow-x: auto;
    object-fit: cover;
    scroll-snap-type: x mandatory;
    scroll-behavior: smooth;
    -webkit-overflow-scrolling: touch;
}
.ps-item {
    flex: none;
    width: 45vw;
    height: 40vh;
    scroll-snap-align: start;
    pointer-events: none;
}

/* Customizing the size of odd slides */
.ps-item:nth-of-type(odd) {
    height: 50vh;
    width: 30vw;
}
```

### JavaScript
To manipulate the carousel with the mouse wheel it's necessary to add some lines of JavaScript. So when the mouse wheel moves in Y direction up or down, the slider will move right or left. It is strictly necessary to add the corresponding `id="psContainer"` in the html tag that contains the slides.

```javascript
<script>
    document.querySelector("#psContainer")
    .addEventListener("wheel", event => {
        if(event.deltaY > 0) {
            event.target.scrollBy(400, 0)  // When the mouse is scrolled up the slider will move 400px to the left.
        } else {
            event.target.scrollBy(-400, 0) // When the mouse is scrolled down the slider will move 400px to the right.
        }
    })
</script>
```

In order for the Mouse Wheel to work only on the parent of the slides, it is necessary to add the `pointer-events: none;` in the  class of the slides.
```css
.ps-item {
    ...
    pointer-events: none;
}
```

## Customizing PureSlider
