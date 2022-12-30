# Question 3
```html,
<section style="background-color:#d0d0d0;overflow:scroll;">

  <h3>Instructions</h3>

  <p>Write code that efficient and performant.</p>  

  <h3>Objectives</h3>

  <p>When users click on button, the text (rgb code) that displays on the button should show in ANSWER box.</p>

</section>

<div id="answerBox">ANSWER</div>

<div id="colorPicker"></div>
```

### Instructions

- Write code that efficient and performant.

### Objectives

- When users click on button, the text (rgb code) that displays on the button should show in ANSWER box.

## Answer 
---
Here is one way you could implement this using JavaScript and jQuery:
```js,
$(document).ready(function() {
  // Select the color picker element
  var colorPicker = $('#colorPicker');

  // Select the answer box element
  var answerBox = $('#answerBox');

  // When a button within the color picker element is clicked
  colorPicker.on('click', 'button', function() {
    // Get the text of the button (which should be the RGB code)
    var rgbCode = $(this).text();

    // Set the text of the answer box to the RGB code
    answerBox.text(rgbCode);
  });
});
```
This code listens for a click event on any button elements within the ``#colorPicker`` element, and when one is clicked, it gets the text of the ``button`` (which should be the RGB code) and sets the text of the ``#answerBox`` element to the RGB code.
