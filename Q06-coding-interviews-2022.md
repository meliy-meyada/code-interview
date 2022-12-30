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
1. First, create a new Angular project using the Angular CLI.

2. Next, create a component for the input box and the table. You can do this by running the following command:
```sh,
ng generate component categories
```
---

3. In the ``categories.component.html`` file, add the input box and the table. The input box should have an ``ngModel`` directive for two-way data binding and an ``(ngModelChange)`` event binding to trigger the filtering function when the input value changes. The table should have a ``*ngFor`` directive to iterate over the data and display it in rows.

```html,
<input type="text" [(ngModel)]="filter" (ngModelChange)="filterCategories()">

<table>
  <tr *ngFor="let category of filteredCategories">
    <td>{{ category }}</td>
  </tr>
</table>
```
---
4. In the ``categories.component.ts`` file, add a property for the data and a property for the filtered data. Also, add a function for filtering the data based on the input value.
```ts,
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-categories',
  templateUrl: './categories.component.html',
  styleUrls: ['./categories.component.css']
})
export class CategoriesComponent implements OnInit {
  data = {
    "count": 51,
    "categories": [
      "Animals",
      "Anime",
      "Anti-Malware",
      "Art & Design",
      "Authentication & Authorization",
      "Blockchain",
      "Books",
      "Business",
      "Calendar",
      "Cloud Storage & File Sharing",
      "Continuous Integration",
      "Cryptocurrency",
      "Currency Exchange",
      "Data Validation",
      "Development",
      "Dictionaries",
      "Documents & Productivity",
      "Email",
      "Entertainment",
      "Environment",
      "Events",
      "Finance",
      "Food & Drink",
      "Games & Comics",
      "Geocoding",
      "Government",
      "Health",
      "Jobs",
      "Machine Learning",
      "Music",
      "News",
      "Open Data",
      "Open Source Projects",
      "Patent",
      "Personality",
      "Phone",
      "Photography",
      "Programming",
      "Science & Math",
      "Security",
      "Shopping",
      "Social",
      "Sports & Fitness",
      "Test Data",
      "Text Analysis",
      "Tracking",
      "Transportation",
      "URL Shorteners",
      "Vehicle",
      "Video",
      "Weather"
    ]
  }
  filteredCategories: string[];

  constructor() { }

  ngOnInit(): void {
    this.filteredCategories = this.data.categories;
  }

  filterCategories() {
    this.filteredCategories = this.data.categories.
```
