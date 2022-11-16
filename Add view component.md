
Add adaptive video view component

app.module.ts:
```ts
...
 screenSize = 'Large';
...
constructor(private responsive: BreakpointObserver) {
  
  }

  ngOnInit(): void {
    this.responsive.observe([
      Breakpoints.Large, 
      Breakpoints.Medium,
      Breakpoints.Small, 
      Breakpoints.XSmall
    ])
      .subscribe(result => {
        console.log("test...");  
        
        if (result.breakpoints[Breakpoints.Large]) {
          this.screenSize = 'Large';
          console.log("screens matches Large");
        }
        else if (result.breakpoints[Breakpoints.Small]) {
          this.screenSize = 'Small';
          console.log("screens matches Small");
        }
        else if (result.breakpoints[Breakpoints.Medium]) {
          this.screenSize = 'Medium';
          console.log("screens matches Medium");
        }
        else if (result.breakpoints[Breakpoints.XSmall]) {
          this.screenSize = 'XSmall';
          console.log("screens matches XSmall");
        }
  });
  }
```

app.component.html:

```html
<section class="card-view">
  <div class="card" [ngClass]="{'wh100': screenSize=='XSmall' || screenSize=='Small'}" *ngFor="let card of cards">
    <div>
      Video #1 header
    </div>
    <img class="card-image" src="https://i.ytimg.com/vi/4kFNcXxueFo/hqdefault.jpg" alt="Video #1">

    <div>
      <p>
        The first video description
      </p>
    </div>
  </div>
</section>
```

css:
```css
.card-view {
    max-width: 1600px;
    margin: auto;
    height: 100%;
}

.card {
    position: relative;
    background: white;
    display: inline-block;
    border-radius: 8px;
    width: 300px;
    height: 300px;
    border: 1px solid lightgray;
    margin: 30px 15px 30px 15px;
    content-visibility: auto;
    padding: 15px 15px 15px 15px;
}

.wh100 {
    width: 100%;
    height: 100%;
}

.card-image {
    width: 100%;
    border-radius: 8px;
}
```

---
links:
[https://blog.angular-university.io/angular-responsive-design/] - responsive design