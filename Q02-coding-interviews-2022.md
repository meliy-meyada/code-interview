# Question 2


```html,
<div class="container">
  <section style="background-color:#d0d0d0;overflow:scroll;">
    <h3>Instructions</h3>
    <ul>
      <li>Existing HTML code in the quiz must be untouched</li>
      <li>Existing CSS code in the quiz must be untouched</li>
    </ul>
    <h3>Objectives</h3>
    <ul>
      <li>Change the dot from green to black by using CSS</li>
      <li>Write CSS to make red box's size fit to white color area</li>
      <li>The dot should be at center of the red box area (vertical and horizontal)</li>
      <li>Content MUST NOT overflow -- No vertical scrollbar</li>
    </ul>
  </section>
  <div class="content">
    <div class="black-dot"></div>
  </div>
</div>
```
### Instructions

- Existing HTML code in the quiz must be untouched

- Existing CSS code in the quiz must be untouched

### Objectives

- Change the dot from green to black by using CSS

- Write CSS to make red box's size fit to white color area

- The dot should be at center of the red box area (vertical and horizontal)
- Content MUST NOT overflow -- No vertical scrollbar

## Answer 
---
To change the dot from green to black, you can add the following CSS rule:
```css,
.black-dot {
  background-color: black;
}
```
---

To make the red box fit to the white color area, you can use the following CSS rule:
```css,
.content {
  width: fit-content;
  height: fit-content;
  background-color: red;
}
```
---

To center the dot both vertically and horizontally within the red box, you can use the following CSS rules:
```css,
.black-dot {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

To prevent the content from overflowing and causing a vertical scrollbar, you can add the following CSS rule:
```css,
html, body {
  overflow: hidden;
}
```
---

All
```css,
.black-dot {
  background-color: black;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.content {
  width: fit-content;
  height: fit-content;
  background-color: red;
}

html, body {
  overflow: hidden;
}
```
