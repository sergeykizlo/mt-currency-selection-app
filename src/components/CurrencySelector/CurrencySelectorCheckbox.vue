<template>
  <label class="cs-checkbox"
       :class="componentClass"
  >
    <input type="checkbox"
           name="currency"
           :id="name"
           :value="value"
           :checked="value"
           @input="onInput"
    />
    {{ name }}
  </label>
</template>

<script>
  export default {
    name: "CurrencySelectorCheckbox",
    props: {
      name: String,
      value: Boolean
    },
    computed: {
      componentClass() {
        return {
          'cs-checkbox--selected': this.value,
        }
      }
    },
    methods: {
      onInput(event) {
        this.$emit('input', event.srcElement.checked);
      }
    }
  }
</script>

<style lang="scss" scoped>
    @import "../../styles/colors";

    .cs-checkbox {
        position: relative;
        display: inline-block;
        width: calc((100% / 3) - 16px);
        padding: 8px;
        border: 1px solid $gray;
        margin: 8px;
        font-size: 28px;
        text-transform: uppercase;
        color: $blue;
        background-color: $lightGray;
        cursor: pointer;

        &:hover {
            background-color: $mediumTransparencyGray;
        }

        &--selected,
        &--selected:hover {
            background-color: $white;
        }

        input[type="checkbox"] {
            -webkit-appearance: none;
            position: relative;
            width: 16px;
            height: 16px;
            border: 1px solid $gray;
            border-radius: 4px;
            margin: 0 4px 0 0;

            &:focus {
                outline: none;
            }

            &:checked::after {
                position: absolute;
                top: 0;
                left: 0;
                width: 14px;
                height: 14px;
                content: 'X';
                font-size: 14px;
                font-weight: bold;
                line-height: 14px;
                text-align: center;
                color: $red;
            }
        }
    }
</style>
