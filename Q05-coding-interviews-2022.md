# Question 5

Please create a web application following below specs.

1. Angular framework is preferred, but you can also use your preferred framework, or pure javascript/HTML5

2. Page consist of 3 columns, first column has fixed width of 200px, last column has fixed width of 300px, the middle column expand/shrink to fill the remaining space of the page, and should be at least 100px. If window is smaller than 600px, show the scrollbar.

3. In the first column, create an input field, where user can enter any number. If the value entered by users are not integer, round it to the nearest integer. If user enter negative values, replace it with 1

4. In the second column, show a drop down, which user can choose what calculation between "is Prime" and

"isFibonacci" he wants to calculate, default the value to isPrime.

- isPrime: calculate whether the input is a prime number, show true in Col3 if the number is prime, and false in the other case

- IsFibanacci: calculate whether the input is a fibonacci number, show true in Col3 if the number is a fibonacci number, and false in the other case.

5. Whenever the value in input box in columnI, or the dropdown in column2 changes, execute the calculation accordingly, and show the result in column 3

## Answer 
---
1. First, make sure you have the Angular CLI installed. If not, you can install it by running 
```sh, 
npm install -g @angular/cli 
```

2. Create a new Angular project by running 
```sh, 
ng new my-app 
```

3. Navigate to the project directory and start the development server by running 
```sh, 
cd my-app and ng serve
```

4. Open a text editor and create the following files:
``src/app/app.component.html``: 
---
This will contain the HTML template for the main component of the app.

```html,
<div class="container">
  <div class="col col-1">
    <input type="number" [(ngModel)]="inputNumber" (input)="onInputChange()" [value]="inputNumber">
  </div>
  <div class="col col-2">
    <select [(ngModel)]="selectedCalculation" (change)="onCalculationChange()">
      <option value="isPrime">is Prime</option>
      <option value="isFibonacci">is Fibonacci</option>
    </select>
  </div>
  <div class="col col-3">
    {{result}}
  </div>
</div>
```
---
``src/app/app.component.css``: This will contain the CSS styles for the main component of the app.
```css,
.container {
  display: flex;
}

.col {
  width: 200px;
  border: 1px solid black;
  box-sizing: border-box;
}

.col-1 {
  width: 200px;
}

.col-2 {
  flex: 1;
  min-width: 100px;
}

.col-3 {
  width: 300px;
}

@media (max-width: 600px) {
  .container {
    overflow-x: scroll;
  }
}
```
---
``src/app/app.component.ts``: This will contain the TypeScript code for the main component of the app.

