# Nitro Angular Components Library
Nitro is an upcoming Angular Components Library, which helps developer to integrate Angular components easily and are built with fully customizable options.

# Nitro OTP

[
  ![Angular Library - Nitro OTP](https://img.shields.io/static/v1?label=npm+package&message=0.5.0&color=green?style=for-the-badge&logo=npm)
](https://www.npmjs.com/package/nitro-otp)

[
  ![Angular Library - Nitro OTP](https://img.shields.io/static/v1?label=Angular&message=12.0.0&color=green?style=for-the-badge&logo=angular)
](https://www.npmjs.com/package/nitro-otp)

Nitro OTP (One Time Password) or PIN (Personal Identification Number) Input is an Angular Library Component for the web built with Angular `12.0.0` and tested from all versions `>= 10.0.0`.

This can be used as OTP inputs or Personal Identification Number (PIN) inputs or for all each character specific inputs.

> _If you are facing any issues with lower versions of angular, Please use the previous version `Nitro-OTP @ 0.4.0` or `Nitro-OTP @ 0.2.0`._

## Features:

1. *Light weight*
2. *Fully customizable*
3. *CSS vars for theming*
4. *In-Built Boxed & Dashed appearance*

## Usage

`app.module.ts`
```ts
import { OtpModule } from 'nitro-otp';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    OtpModule
  ]
})
```

`some.component.ts`
```ts
import { OtpComponent } from 'nitro-otp';
```

`some.component.html`
```html
<nitro-otp #otp [size]="4" message="Incorrect OTP" [autoFocus]="true" (otpChange)="afterOtpChanged($event)"></nitro-otp>
```

#### Error Management Example:
`some.component.ts`
```ts
// Below code are OPTIONAL for error display
export class SomeComponent {
  @ViewChild('otp')
  private otp!: OtpComponent;

  afterOtpChanged(otpVal: [string, boolean]): void {
    const [value, length] = otpVal;
    // value: Value of OTP Input
    // length: TRUE, if length matches and vice-versa
    
    // Write your validation code here `this.otp.isError.next(true);` will set Error
    this.otp.isError.next(!length);
  }
}
```

## API:
|Name|Type|Default|Description|
|---|---|---|---|
|`appearance`|`String`| `legacy` | <details><summary>*Change Appearance of Control*</summary>Change appearance of OTP input (legacy / dashed)<br><br>__Eg.:__<br>`<nitro-otp [appearance]="dashed"></nitro-otp>`<br><br>__Accepted Values:__<br>`legacy` / `dashed` / `<any_string>`<br><br><blockquote>Custom String will be added as a class prefixed by an underscores (like `_customTheme`)</blockquote></details>|
|`autoFocus`|`Boolean`| `true` | <details><summary>*Autofocus to Input*</summary>Toggle autoFocus to OTP input<br>__Eg.:__<br>`<nitro-otp [autoFocus]="true"></nitro-otp>`</details>|
|`message`|`String`| `""` | <details><summary>*Message to show*</summary>Custom message to show when an Error occurs<br>__Eg.:__<br>`<nitro-otp [message]="'Invalid OTP'"></nitro-otp>`</details>|
|`passwordChar`|`String`| `•` | <details><summary>*passwordChar to show*</summary>Custom Character to mask the OTP<br>__Eg.:__<br>`<nitro-otp [passwordChar]="*"></nitro-otp>`</details>|
|`revealChar`|`Boolean`| `true` | <details><summary>*Set the Characters Reveal or Not*</summary>Set Character to mask or show for OTP<br>__Eg.:__<br>`<nitro-otp [revealChar]="true"></nitro-otp>`</details>|
|`size`|`Number`| `4` | <details><summary>*Max. Size of Input*</summary>Defines the maximum size of OTP / Pin Input Control<br>__Eg.:__<br>`<nitro-otp [size]="4"></nitro-otp>`</details>|

**CSS Variables:**
```css
:root {
  --nitro-otp_border-color: goldenrod;
  --nitro-otp_border-color_focus: blue;
  --nitro-otp_border-color_error: red;
}
```

This library was generated with [Angular CLI](https://github.com/angular/angular-cli) version `12.0.0`.

# Nitro Popup

[
  ![Angular Library - Nitro Popup](https://img.shields.io/static/v1?label=npm+package&message=0.0.6&color=green?style=for-the-badge&logo=npm)
](https://www.npmjs.com/package/nitro-popup)

[
  ![Angular Library - Nitro Popup](https://img.shields.io/static/v1?label=Angular&message=12.0.0&color=green?style=for-the-badge&logo=angular)
](https://www.npmjs.com/package/nitro-popup)

Nitro Popup can be used for Popups / Modals / Dialog Boxes and even also this can be used as context menu also. Inbuilt support added for overriding context menus.

## Features:

1. *Light weight*
2. *Fully configurable with just one JSON object for each Popup*
3. *Layouts & Templates can be controlled using `<ng-template>`*
4. *Easy Override with CSS styles*
5. *In-Built Animation Support*

## Usage

`app.module.ts`
```ts
import { PopupModule } from 'nitro-popup';

@NgModule({
  declarations: [
    // ...
  ],
  imports: [
    PopupModule
    // ...
  ]
})
```

`some.component.ts`
```ts
  import { PopupService } from 'nitro-popup';

  // ...
  export class SomeComponent {
    constructor(
      public popupService: PopupService
    ) {
    }

    triggerPopupOpen():void {
      openPopup({
        event: new Event('open'),
        template: popupRef
      });
    }

    openPopup(opt: any): void {
      this.popupService.open(opt);
    }

    closePopup(opt: any): void {
      this.popupService.close(opt);
    }
  }
```

`some.component.html` - _SIMPLE USE **Compact**_
```html
  <button (click)="openPopup({
    event: $event,
    template: popupRef
  })" class="btn">OPEN POPUP</button>

  <nitro-popup #popupRef [config]="{
      width: '600px',
      height: '600px',
      id: 'popupYourID',
      contentLayout: popupContentLayout
    }">
  </nitro-popup>

  <ng-template #popupContentLayout>
    <ng-container *ngTemplateOutlet="profileImage"></ng-container>
  </ng-template>

  <ng-template #popupHeaderLayout>
    <span class="title">Title</span>
    <button class="btn close" (click)="closePopup($event)">x</button>
  </ng-template>
  <ng-template #popupFooterLayout>
    Footer
  </ng-template>
  <ng-template #popupSideLayout>
    <nav>
      <ul>
      <li>
        <button>Menu 1</button>
      </li>
      <li>
        <button>Menu 2</button>
      </li>
    </ul>
    </nav>
  </ng-template>
```

`some.component.html` - _SIMPLE USE **with Animations and all Templates**_
```html
  <button (click)="openPopup({
    event: $event,
    template: popupRef
  })" class="btn">OPEN POPUP</button>

  <nitro-popup #popupRef [config]="{
      width: '600px',
      height: '600px',
      id: 'popupDemo',
      class: 'popupYourStyleClass or Classes',
      animateIn: 'zoomIn',
      animateOut: 'zoomOut'
      sideLayout: popupSideLayout,
      headerLayout: popupHeaderLayout,
      footerLayout: popupFooterLayout,
      contentLayout: popupContentLayout
    }">
  </nitro-popup>

  <ng-template #popupContentLayout>
    Popup Contents
  </ng-template>

  <ng-template #popupHeaderLayout>
    <span class="title">Title</span>
    <button class="btn close" (click)="closePopup($event)">x</button>
  </ng-template>
  <ng-template #popupFooterLayout>
    Footer
  </ng-template>
  <ng-template #popupSideLayout>
    <nav class="menu">
      <ul>
        <li>
          <button>Menu 1</button>
        </li>
        <li>
          <button>Menu 2</button>
        </li>
      </ul>
    </nav>
  </ng-template>
```

`some.component.html` - _Growing from a **target element**_
```html
  <button #btnRef (click)="openPopup({
    event: $event,
    template: popupRef
  })" class="btn">OPEN POPUP</button>

  <nitro-popup #popupRef [config]="{
      delay: 500,
      origin: btnRef,
      width: '100%',
      height: '100%',
      id: 'popupDemo',
      class: 'popupStyle',
      animateIn: 'pulse',
      animateOut: 'zoomOut',
      css: {
        'max-width': '100vw',
        'max-height': '100vh'
      },
      contentLayout: popupContentLayout
    }">
  </nitro-popup>

  <ng-template #popupContentLayout>
    <ng-container *ngTemplateOutlet="profileImage"></ng-container>
  </ng-template>

  <!-- <ng-template #popupHeaderLayout>
    <span class="title">Title</span>
    <button class="btn close" (click)="closePopup($event)">x</button>
  </ng-template>
  <ng-template #popupFooterLayout>
    Footer
  </ng-template>
  <ng-template #popupSideLayout>
    <nav>
      <ul>
      <li>
        <button>Menu 1</button>
      </li>
      <li>
        <button>Menu 2</button>
      </li>
    </ul>
    </nav>
  </ng-template> -->
```

## How to override context menu and open a custom Menu
```html
  <div class="customContextMenu" (contextmenu)="openPopup({
      event: $event,
      template: menu
    })" style="width: 100%; height: 100%; top:0; left:0; position: fixed;background: rgba(0,0,0,0.2)">
    Right Button Click this area to get the CUSTOM MENU
    </div>

  <nitro-popup #menu [config]="{
    width: 'auto',
    height: 'auto',
    id: 'popupMenu',
    class: 'popupMenu',
    contentLayout: menuLayout
  }">
    <ng-template #menuLayout>
      <a href="javascript:;">Menu 1</a>
      <a href="javascript:;">Menu 2</a>
      <a href="javascript:;">Menu 3</a>
      <a href="javascript:;">Menu 4</a>
    </ng-template>
  </nitro-popup>
```


## API:
|Name|Type|Default|Description|
|---|---|---|---|
|`id`|`String`| `""` | <details><summary>*ID*</summary>This will set an ID for the popup template (Keep it unique) <br><br>__Eg.:__<br>`<nitro-popup [config]="{id: 'popupName'...}"></nitro-popup>`<br><br>__Accepted Values:__<br>`<any_string>`<br><br><blockquote>ID String will also be added as a class for the popup also.</blockquote></details>|
|`width` and `height`|`String`| `100%` | <details><summary>*Width and height of popup*</summary>Set width and height of the popup. The width can be of `%`, `px` or `auto` values as a string<br>__Eg.:__<br>`<nitro-popup [config]="{width: '600px', height: 'auto'}"></nitro-popup>`</details>|
|`css`|`JSON`| `""` | <details><summary>*Add custom CSS*</summary>Custom css will be applied as inline style to the Popup<br>__Eg.:__<br>`<nitro-popup [config]="{ css: {'max-width': '100vw','max-height': '100vh'}}"></nitro-popup>`</details>|
|`animateIn`|`String`| `""` | <details><summary>*Class for Animate In*</summary> AnimateIn Class will be applied to the Popup at opening event<br>__Eg.:__<br>`<nitro-popup [config]="{ animateIn: 'zoomIn'}"></nitro-popup>`</details>|
|`animateOut`|`String`| `""` | <details><summary>*Class for Animate Out*</summary> AnimateOut Class will be applied to the Popup at opening event<br>__Eg.:__<br>`<nitro-popup [config]="{ animateOut: 'zoomOut' }"></nitro-popup>`</details>|
|`overlay`| `String` / `boolean`| `true` | <details><summary>*Various Overlay Types*</summary>Toggle Overlay Show/Hide or blocks/allow clicks outside the popup<br>Accepted Values are `true`, `false`, `transparent`, `none`, `transparent_none` <br>__Eg.:__<br>`<nitro-popup [config]="{overlay: 'transparent'}"></nitro-popup>`</details>|
|`headerLayout`|`TemplateRef`| `null` | <details><summary>*Header Template*</summary>HTML Template for header<br>__Eg.:__<br>`<nitro-popup [config]="{headerLayout: headerTemplateElementRef}"></nitro-popup>`</details>|
|`footerLayout`|`TemplateRef`| `null` | <details><summary>*Footer Template*</summary>HTML Template for footer<br>__Eg.:__<br>`<nitro-popup [config]="{footerLayout: footerTemplateElementRef}"></nitro-popup>`</details>|
|`contentLayout`|`TemplateRef`| `null` | <details><summary>*Content Template*</summary>HTML Template for content<br>__Eg.:__<br>`<nitro-popup [config]="{contentLayout: contentTemplateElementRef}"></nitro-popup>`</details>|
|`sideLayout`|`TemplateRef`| `null` | <details><summary>*Left Side Template*</summary>HTML Template for side<br>__Eg.:__<br>`<nitro-popup [config]="{sideLayout: sideTemplateElementRef}"></nitro-popup>`</details>|
|`customLayout`|`TemplateRef`| `null` | <details><summary>*custom Layout Template*</summary>Custom HTML Template for Popup<br>__Eg.:__<br>`<nitro-popup [config]="{customLayout: sideTemplateElementRef}"></nitro-popup>`</details>|


This library was generated with [Angular CLI](https://github.com/angular/angular-cli) version `12.0.0`.
