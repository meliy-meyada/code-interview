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

```ts,
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  inputNumber: number;
  selectedCalculation: string;
  result: string;

  constructor() {
    this.selectedCalculation = 'isPrime';
  }

  onInputChange() {
    this.inputNumber = Math.round(this.inputNumber);
    if (this.inputNumber < 1) {
      this.inputNumber = 1;
    }
    this.calculateResult();
  }

  onCalculationChange() {
    this.calculateResult();
  }

  calculateResult() {
    if (this.selectedCalculation === 'isPrime') {
      this.result = this.isPrime(this.inputNumber) ? 'true' : 'false';
    } else if (this.selectedCalculation === 'isFibonacci') {
      this
```
---

Here is an example of how to create a web application that meets the specifications provided using the Angular framework:

```js,html,css,ts,
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    <div class="container">
      <div class="column" style="width: 200px">
        <input type="number" [(ngModel)]="inputNumber" (change)="onInputChange()" [value]="1" />
      </div>
      <div class="column" style="flex: 1; min-width: 100px">
        <select [(ngModel)]="calculationType" (change)="onInputChange()">
          <option value="isPrime">isPrime</option>
          <option value="isFibonacci">isFibonacci</option>
        </select>
      </div>
      <div class="column" style="width: 300px">
        {{ result }}
      </div>
    </div>
  `,
  styles: [`
    .container {
      display: flex;
      flex-direction: row;
      width: 100%;
      height: 100%;
      overflow-x: auto;
    }
    .column {
      display: flex;
      align-items: center;
      justify-content: center;
    }
  `]
})
export class AppComponent implements OnInit {
  inputNumber = 1;
  calculationType = 'isPrime';
  result: boolean;

  ngOnInit() {
    this.onInputChange();
  }

  onInputChange() {
    const input = Math.round(Math.max(1, this.inputNumber));

    if (this.calculationType === 'isPrime') {
      this.result = this.isPrime(input);
    } else {
      this.result = this.isFibonacci(input);
    }
  }

  isPrime(n: number): boolean {
    if (n < 2) {
      return false;
    }
    for (let i = 2; i <= Math.sqrt(n); i++) {
      if (n % i === 0) {
        return false;
      }
    }
    return true;
  }

  isFibonacci(n: number): boolean {
    if (n === 0 || n === 1) {
      return true;
    }
    let previous = 0;
    let current = 1;
    while (current < n) {
      [previous, current] = [current, previous + current];
    }
    return current === n;
  }
}
```
This code defines an Angular component with a template that includes three columns, an input field in the first column, a dropdown in the second column, and a display element in the third column. The component also includes logic to perform the ``isPrime`` and ``isFibonacci`` calculations and display the results in the third column.

The input field and dropdown are bound to component properties using the ``[(ngModel)]`` syntax, and the ``(change)`` event is used to trigger the calculation when the input or dropdown value changes.

The component also includes a couple of helper functions, ``isPrime`` and ``isFibonacci``,
