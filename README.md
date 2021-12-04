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
      <base-input></base-input>
```

Using ```v-model```

```sh
      <base-input
          v-model:value="modelValue.value"
          v-model:isValid="modelValue.isValid"
      >
      </base-input>
```

## Available props

| Prop                          | Type            | Default     | Description                              |
|-------------------------------|-----------------|-------------|------------------------------------------|
|                               |                 |             |                                          |


### Demo

[![Demo on Netlify](https://www.netlify.com/img/deploy/button.svg)](https://vue-base-input.netlify.app/)
