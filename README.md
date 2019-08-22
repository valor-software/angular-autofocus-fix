# ngx-autofocus-fix

Angular 5+ directive for fix autofocus on dinamically created controls (`*ngIf`, `*ngFor`, etc.).

## Advantages over other libraries

* **Uses native HTML attribute `autofocus` as the selector!**  
* There are no custom selectors, no need to change your html template.
* Works with native DOM. Doesn't use any dependencies(jQuery, lodash, etc.).
* Over 50 unit tests!
* E2E tests for 8,7,6 and 5 versions of Angular.
* The library understands an extensive list of input data. (`null/NaN/'true'/[]/...`, not only boolean). See [Advanced examples](#advanced-examples)
* Supports asynchronous focusing.
* Works perfect with Angular Material. (there is an E2E test)

## Installation

To install this library, run:

```bash
$ npm install ngx-autofocus-fix --save
```

## Quick start

1. Import the library in your Angular application, for example in `AppModule`:

```typescript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { AppComponent } from './app.component';

import { NgxAutofocusFixModule } from 'ngx-autofocus-fix'; // <--- new code

@NgModule({
  declarations: [
    AppComponent,
  ],
  imports: [
    BrowserModule,

    NgxAutofocusFixModule, // <--- new code
  ],
  providers: [],
  bootstrap: [ AppComponent ]
})
export class AppModule { }
```

2. You can now use autofocus directive in app.component.html

```html
<input autofocus
       placeholder="I have autofocus"
       *ngIf="showInput"
>
<button (click)="showInput = !showInput">Toggle Input</button>
```

**Stackblitz demo:**

## Advanced examples

Ways to **disable autofocus:** any js-falsely value, except empty string

```html
   <!-- with data binding -->
   <input [autofocus]=""> <!-- undefined value -->
   <input [autofocus]="undefined">
   <input [autofocus]="false">
   <input [autofocus]="null">
   <input [autofocus]="0">
   <input [autofocus]="NaN">
   
   <!-- without data binding -->
   <input autofocus="undefined">
   <input autofocus="false">
   <input autofocus="null">
   <input autofocus="0">
   <input autofocus="NaN">
   
   <input> <!-- disabled by default -->
``` 

Ways to **enable autofocus:** any js-true value and empty string

```html
   <!-- empty string will enable autofocus, this is default html behavior -->
   <input [autofocus]="{}">
   <input [autofocus]="[]">
   <input [autofocus]="''">
   <input autofocus="">
   <input autofocus>
   
   <input autofocus="autofocus">
   
   <input [autofocus]="true">
   <input [autofocus]="1">
   <input autofocus="true">
   
   <input [autofocus]="'any other values'">
   <input autofocus="any other values">
```

## Development

To generate all `*.js`, `*.d.ts` and `*.metadata.json` files:

```bash
$ npm run build
```

To lint all `*.ts` files:

```bash
$ npm run lint
```

## License

MIT © [Anton Korniychuk](mailto:dev@korniychuk.pro)
