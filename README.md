# Nitro Angular Components Library
Nitro Angular Library

# Nitro Otp / Pin Input `0.4.0`

One Time Password (OTP) Input Angular Library Component for the web built with Angular `11.0.0` and tested from all versions `>= 10.0.0`.

This can be used as OTP inputs or Personal Identification Number (PIN) inputs or for all each character specific inputs.

## Features:

1. *Light weight*
2. *Fully customizable*
3. *CSS Vars for Theming*
4. *In-Built Boxed & Dashed Appearance*

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
|`revealChar`|`Boolean`| `•` | <details><summary>*Set the Characters Reveal or Not*</summary>Set Character to mask or show for OTP<br>__Eg.:__<br>`<nitro-otp [revealChar]="true"></nitro-otp>`</details>|
|`size`|`Number`| 4 | <details><summary>*Max. Size of Input*</summary>Defines the maximum size of OTP / Pin Input Control<br>__Eg.:__<br>`<nitro-otp [size]="4"></nitro-otp>`</details>|

**CSS Variables:**
```css
:root {
  --nitro-otp_border-color: goldenrod;
  --nitro-otp_border-color_focus: blue;
  --nitro-otp_border-color_error: red;
}
```

This library was generated with [Angular CLI](https://github.com/angular/angular-cli) version `11.0.0`.
