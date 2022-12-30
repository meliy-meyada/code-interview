# Question 3
```html,
<section style="background-color:#d0d0d0;overflow:scroll;">
  <h3>Instructions</h3>
  <p>You can only modify code in MyDlg class</p>
  <h3>Objectives</h3>
  <p>Developers want to be able to prevent the dialog from closing (when click X) by cancelling the event with `preventDefault()`. Currently, MyDlg doesn't support this use case, you're asked to fix it.</p>
</section>
<my-dlg id="dlg"></my-dlg>
```
### Instructions
- You can only modify code in MyDlg class

### Objectives
- Developers want to be able to prevent the dialog from closing (when click X) by cancelling the event with `preventDefault()`. Currently, MyDlg doesn't support this use case, you're asked to fix it.

## Answer 
---
To prevent the dialog from closing when the X button is clicked, you can add an event listener to the close button and cancel the default action using the ``preventDefault()`` method.

Here's an example of how you can do this in the ``MyDlg`` class:
```js,
class MyDlg extends HTMLElement {
  connectedCallback() {
    // Get the close button
    const closeButton = this.shadowRoot.querySelector('.close-button');

    // Add an event listener to the close button
    closeButton.addEventListener('click', (event) => {
      // Cancel the default action (closing the dialog)
      event.preventDefault();
    });
  }
}
```
This will prevent the dialog from closing when the close button is clicked. You can also use this technique to add custom behavior when the close button is clicked, such as showing a confirmation dialog before closing the dialog.



