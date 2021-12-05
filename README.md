# `vue-base-input (Vue 3)`

Base-input:

I made it, for simplify a create form on my differents projects.
Base-input return if your value is valid and value in Object.

### Install

npm:
```sh
npm i vue-base-input
```

yarn:
```sh
yarn add vue-base-input
```

```sh
import vueBaseInput from 'vue-base-input';

export default {
  // ...
  components: {
    vueBaseInput
  },
  data() {
    return {
      modelValue: {
        value: '',
        isValid: ''
      };
  }
  // ...
}

```

### CSS

Tailwind CSS
```
import 'vue-base-input/src/assets/vue-base-input-tailwind-css.css';
```
CSS
```
import 'vue-base-input/src/assets/vue-base-input.css';
```
Custom
```sh
/* transition */
.fade-enter-active,
.fade-leave-active {}
.fade-enter-from,
.fade-leave-to {}
/* end transition */

.base-input {}
.border-valid {}
.border-default {}
.border-faild {}
.error-color {}
.label-color {}
.bg-full {}
.bg-empty {}
.bloc-input {}
.input {}

/* input label inside true */
.input-label-inside {}
/* input label outside true */
.input-label-outside {}

.bloc-button {}
.button-icon {}
.button-icon img {}
.label-outside {}
.label-inside {}

@media (min-width: 768px) {
  .label-outside {}
  .label-inside {}
  .bloc-error .error-message {}
}

.required {}
.bloc-error {}
.bloc-error .error-message {}

/* animation label inside/outside*/
input:not(:-moz-placeholder-shown) ~ label.label-inside {}
input:not(:-ms-input-placeholder) ~ label.label-inside {}
input:focus-within ~ label.label-inside, input:not(:placeholder-shown) ~ label.label-inside {}
input:not(:-moz-placeholder-shown) ~ label.label-outside {}
input:not(:-ms-input-placeholder) ~ label.label-outside {}
input:focus-within ~ label.label-outside, input:not(:placeholder-shown) ~ label.label-outside {}
```

### Usage 🚀

```sh
<vue-base-input></vue-base-input>
```

Using ```v-model```

```sh
<vue-base-input
  v-model:value="modelValue.value"
  v-model:is-valid="modelValue.isValid"
>
</vue-base-input>
```

## Available props

| Prop                          | Type            | Default     | Description                                           |
|-------------------------------|-----------------|-------------|-------------------------------------------------------|
| is-valid                      | Boolean         | null        | return true if regex is true or if input is not empty |
| input-type                    | String          | text        | Change input type: text, password, date               |
| is-required                   | Boolean         | false       | show * after label and change border color and icon   |
| show-border                   | Boolean         | true        | show/hide border if is-valid is true/false            |
| show-icon                     | Boolean         | true        | show/hide icon if is-valid is true/false              |
| error-message                 | String          | text        | show error message under input                        |
| icon                          | String|Object   | null        | Add url icon :lock:                                   |
| url-icon-valid                | String|Object   | null        | Add url icon success example: :heavy_check_mark:      |
| url-icon-faild                | String|Object   | null        | Add url icon faild example: :x:                       |
| url-icon-open-eyes            | String|Object   | null        | Add url icon open-eyes for password input type        |
| url-icon-close-eyes           | String|Object   | null        | Add url icon close-eyes for password input type       |
| regex                         | String          | null        | build test and return is-valid true or false          |
| label-inside                  | Boolean         | false       | if input isn't empty the label place to inside or outside input                                      |
| custom-style                  | Object          |             |                                                       |
| input-class                   | String          |             |                                                       |


### Demo

[![Demo on Netlify](https://www.netlify.com/img/deploy/button.svg)](https://vue-base-input.netlify.app/)
