
Add adaptive video view component

app.component.ts:
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
    <div *ngIf="screenSize!='XSmall' && screenSize!='Small'">
      <youtube-player videoId="{{card.id}}" [height]="200" [width]="300"></youtube-player>
    </div>
    <div *ngIf="screenSize=='XSmall' || screenSize=='Small'">
      <youtube-player videoId="{{card.id}}"></youtube-player>  
    </div>

    <div class="title-text">
      {{card.title}}
    </div>
    <div class="desctiption-text">
      {{card.description}}
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
```

---
## Add video player

```shell
> npm install --save @angular/youtube-player
```

app.module.ts:

```ts
import {YouTubePlayerModule} from '@angular/youtube-player';
...

imports: [
  ...
  YouTubePlayerModule
],
...
```

if your angular version is too low for this player:
```shell
>  ng update @angular/core@14 @angular/cli@14 --force
```

app.component.ts:

```ts
...
ngOnInit(): void {
    const tag = document.createElement('script');
    tag.src = 'https://www.youtube.com/iframe_api';
    document.body.appendChild(tag);
...
```    

---
links:
[https://blog.angular-university.io/angular-responsive-design/] - responsive design