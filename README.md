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


### Usage 🚀

```sh
<vue-base-input></vue-base-input>
```

Using ```v-model```

```sh
<vue-base-input
  v-model:value="modelValue.value"
  v-model:isValid="modelValue.isValid"
>
</vue-base-input>
```

## Available props

| Prop                          | Type            | Default     | Description                                           |
|-------------------------------|-----------------|-------------|-------------------------------------------------------|
| is-valid                      | Boolean         | null        | return true if regex is true or if input is not empty |
| input-type                    | String          | text        |                                                       |
| input-class                   | String          |             |                                                       |
| is-required                   | Boolean         | false       |                                                       |
| show-validate                 | Boolean         | true        |                                                       |
| show-border                   | Boolean         | true        |                                                       |
| show-icon                     | Boolean         | true        |                                                       |
| error-message                 | String          | text        |                                                       |
| icon                          | String          | text        |                                                       |
| url-icon-valid                | String          | null        |                                                       |
| url-icon-faild                | String          | null        |                                                       |
| url-icon-open-eyes            | String          | null        |                                                       |
| url-icon-close-eyes           | String          | null        |                                                       |
| regex                         | String          | null        |                                                       |
| label-inside                  | Boolean         | false       |                                                       |
| custom-style                  | Object          |             |                                                       |


### Demo

[![Demo on Netlify](https://www.netlify.com/img/deploy/button.svg)](https://vue-base-input.netlify.app/)
