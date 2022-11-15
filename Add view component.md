
```shell
> npm install --save @angular/material
```

package.json:
```json
"dependencies": {
  ...
    "@angular/material": "14.2.7",
  ...  
  }
```

app.module.ts:
```ts
import {MatCardModule} from '@angular/material/card';
...
 imports: [
...
    MatCardModule
  ],
...
```

app.component.html:

```html
<mat-card class="example-card">
  <mat-card-header>
    <div mat-card-avatar class="example-header-image"></div>
    <mat-card-title>Video #1 header</mat-card-title>
    <mat-card-subtitle>Video #1 subheader</mat-card-subtitle>
  </mat-card-header>
  <img mat-card-image src="https://material.angular.io/assets/img/examples/shiba2.jpg" alt="Video #1">
  <mat-card-content>
    <p>
      The first video description
    </p>
  </mat-card-content>
  <mat-card-actions>
    <button mat-button>Play</button>
    <button mat-button>Like</button>
  </mat-card-actions>
</mat-card>
```

---
links:
[https://material.angular.io/components/card/api] - documentation