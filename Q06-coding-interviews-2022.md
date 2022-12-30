# Question 6
Create a web app with an input for using as filter and a table for display the result. The app need to get data from https://api.publicapis.org/categories for using for displaying in the result table.
Result table
- By default display all data from categories
Filtering
- When user type any text in the input box, the result table should be filter to display only the result that contains the text.
> NOTE
- The app could created with any framework but Angular is preferred

## Answer 
---

1. Create a new Angular project using the Angular CLI.

2. Create a component for the result table. This component will be responsible for displaying the data in the table.

3. In the component, create an input field for the user to enter a filter query.

4. Create a service to make API calls to the https://api.publicapis.org/categories endpoint.

5. In the component, use the service to fetch the data from the API and store it in a variable.

6. Use the ``ngFor`` directive to loop through the data and display it in a table.

7. Implement the filtering functionality by using the Angular Pipe feature. When the user types in the input field, the pipe will filter the data and display only the results that contain the text entered by the user.

```ts,
import { Component, OnInit } from '@angular/core';
import { CategoriesService } from './categories.service';
import { Category } from './category';

@Component({
  selector: 'app-categories',
  template: `
    <input type="text" [(ngModel)]="filterText" placeholder="Filter by name">
    <table>
      <tr>
        <th>Name</th>
        <th>Description</th>
      </tr>
      <tr *ngFor="let category of categories | filter:filterText">
        <td>{{category.name}}</td>
        <td>{{category.description}}</td>
      </tr>
    </table>
  `,
  styleUrls: ['./categories.component.css']
})
export class CategoriesComponent implements OnInit {
  categories: Category[];
  filterText: string;

  constructor(private categoriesService: CategoriesService) { }

  ngOnInit() {
    this.categoriesService.getCategories().subscribe(categories => {
      this.categories = categories;
    });
  }
}
```
And here is an example of the ``filter`` pipe

```ts,
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'filter'
})
export class FilterPipe implements PipeTransform {

  transform(items: any[], searchText: string): any[] {
    if (!items) {
      return [];
    }
    if (!searchText) {
      return items;
    }
    searchText = searchText.toLowerCase();
    return items.filter(it => {
      return it.name.toLowerCase().includes(searchText);
    });
  }

}
```
