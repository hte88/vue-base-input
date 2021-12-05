<script>
export default {
  model: {
    prop: 'title',
    event: 'change',
  },
  props: {
    value: {
      type: String,
    },
    isValid: {
      type: Boolean,
      default: null
    },
    inputType: {
      type: String,
      default: 'text'
    },
    inputClass: {
      type: String,
      default: ''
    },
    isRequired: {
      type: Boolean,
      default: false
    },
    showBorder: {
      type: Boolean,
      default: true
    },
    showIcon: {
      type: Boolean,
      default: true
    },
    errorMessage: {
      type: String,
      default: ''
    },
    icon: {
      type: [Object, String],
      default: null,
    },
    urlIconValid: {
      type: [Object, String],
      default: null,
    },
    urlIconFaild: {
      type: [Object, String],
      default: null,
    },
    urlIconOpenEyes: {
      type: [Object, String],
      default: null,
    },
    urlIconCloseEyes: {
      type: [Object, String],
      default: null,
    },
    regex: {
      type: [Object, String],
      default: null,
      example:
        '^(?=.*[A-Za-z])(?=.*\d)(?=.*[@$!%*#?&])[A-Za-z\d@$!%*#?&]{10,}$',
    },
    labelInside: {
      type: Boolean,
      default: false,
    },
    customStyle: {
      type: Object,
      default() {
        return {
          borderIsValid: 'border-valid',
          borderIsDefault: 'border-default',
          borderIsBad: 'border-faild',
          errorMessage: 'error-color',
          label: 'label-color',
          inputBgFull: 'bg-full',
          inputBgEmpty: 'bg-empty',
        };
      },
    },
  },
  computed: {
    getValueLength() {
      return this.modelValue !== '' && this.modelValue !== null ? this.modelValue?.length : '';
    },
    getIconCheck() {
      if (this.isValidate === false) {
        return this.urlIconFaild;
      } else {
        return this.urlIconValid;
      }
    },
    getIconEyes() {
      if (this.showPassword) {
        return this.urlIconOpenEyes;
      } else {
        return this.urlIconCloseEyes;
      }
    },
    classBorder() {
      return this.isValidate &&
        this.showBorder &&
        this.returnValueByLength(this.getValueLength, true, false, 1)
        ? this.customStyle.borderIsValid
        : this.isValidate === false
        ? this.customStyle.borderIsBad
        : this.customStyle.borderIsDefault;
    },
  },
  mounted() {
    if (this.getValueLength > 1) {
      this.update(this.modelValue);
    }
  },
  watch: {
    modelValue(value) {
      this.update(value);
    },
    regex() {
      this.update(this.modelValue);
    },
  },
  data() {
    return {
      modelValue: this.value,
      isValidate: this.isValid,
      showErrorMessage: false,
      showPassword: false,
    };
  },
  methods: {
    returnValueByLength(value, correct, incorrect, number) {
      return value >= number ? correct : incorrect;
    },
    testRegex(value) {
      if (this.regex !== null && this.regex !== '') {
        const regex = new RegExp(this.regex);
        return regex.test(value);
      } else {
        return true;
      }
    },
    update(value) {
      if (this.isRequired && this.testRegex(value) && value.length >= 1) {
        this.isValidate = true;
      } else if (
        this.isRequired &&
        !this.testRegex(value) &&
        value.length >= 1
      ) {
        this.isValidate = false;
      } else if (!this.isRequired && value.length >= 1) {
        this.isValidate = true;
      } else {
        this.isValidate = null;
      }
      this.$emit('update:value', value);
      this.$emit('update:isValid', this.isValidate);
    },
  },
};
</script>
<template>
  <div :class="[classBorder, inputClass, 'base-input']">
    <div
      :class="[
        returnValueByLength(
          getValueLength,
          customStyle.inputBgFull,
          customStyle.inputBgEmpty,
          1
        ),
        'bloc-input',
      ]"
    >
      <input
        v-model="modelValue"
        v-bind="$attrs"
        :class="[
          labelInside ? 'input-label-inside' : 'input-label-outside',
          'input',
        ]"
        :placeholder="$attrs.placeholder ? $attrs.placeholder : ' '"
        :type="showPassword ? 'text' : inputType"
      />
      <button
        v-if="
          getIconCheck &&
          isValidate === false &&
          getValueLength >= 1 &&
          showIcon
        "
        @click.prevent="showErrorMessage = !showErrorMessage"
        :class="[
          returnValueByLength(
            getValueLength,
            customStyle.inputBgFull,
            customStyle.inputBgEmpty,
            1
          ),
          'button-icon',
        ]"
        type="button"
      >
        <img :src="getIconCheck.src" :alt="getIconCheck.alt" />
      </button>
      <div
        v-if="
          getIconCheck &&
          isValidate !== false &&
          getValueLength >= 1 &&
          showIcon
        "
        :class="[
          returnValueByLength(
            getValueLength,
            customStyle.inputBgFull,
            customStyle.inputBgEmpty,
            1
          ),
          'button-icon',
        ]"
      >
        <img :src="getIconCheck.src" :alt="getIconCheck.alt" />
      </div>

      <div
        :class="[
          returnValueByLength(
            getValueLength,
            customStyle.inputBgFull,
            customStyle.inputBgEmpty,
            1
          ),
          'bloc-button',
        ]"
      >
        <button
          v-if="getIconEyes && showIcon && inputType === 'password'"
          @click.prevent="showPassword = !showPassword"
          class="button-icon"
          type="button"
        >
          <img :src="getIconEyes" alt="" />
        </button>
        <div v-if="icon" class="button-icon">
          <img :src="icon.src" :alt="icon.alt" />
        </div>
      </div>
      <label
        v-if="$attrs.label && !$attrs.placeholder"
        :for="$attrs.name"
        :class="[
          labelInside ? 'label-inside' : 'label-outside',
          customStyle.label,
        ]"
      >
        {{ $attrs.label }}
        <span v-if="isRequired" class="required">*</span>
      </label>
    </div>
    <div class="bloc-error">
      <transition name="fade">
        <p
          v-if="showErrorMessage && isValidate === false && errorMessage"
          :class="[customStyle.errorMessage, 'error-message']"
        >
          {{ errorMessage }}
        </p>
      </transition>
    </div>
  </div>
</template>
