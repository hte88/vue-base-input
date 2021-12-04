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


### Getting Started 🚀

```sh
      <base-input
          v-model:value="modelValue.value"
          v-model:isValid="modelValue.isValid"
          input-type="text"
          name="email"
          label="Email"
          error-message="This email, is not good"
          input-class="mb-2 border-2 rounded-md"
          :regex="^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,24}))$"
          :is-required="true"
          :show-border="true"
          :show-icon="true"
          :label-inside="false"
      >
      </base-input>
```



[![Demo on Netlify](https://www.netlify.com/img/deploy/button.svg)](https://base_input.netlify.com)

#### Bonus links

