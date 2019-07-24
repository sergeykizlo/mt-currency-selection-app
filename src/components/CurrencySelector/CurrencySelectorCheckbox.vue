<template>
  <div class="cs-checkbox"
       :class="{ 'cs-checkbox--selected' : currency.isSelected }"
  >
    <input type="checkbox"
           name="currency"
           :id="currency.name"
           :value="currency.name"
           :checked="currency.isSelected"
           @change="currency.isSelected ? deselectCurrency(currency) : selectCurrency(currency)"/>
    <label :for="currency.name">{{ currency.name }}</label>
  </div>
</template>

<script>
  export default {
    name: "CurrencySelectorCheckbox",
    props: {
      currency: Object,
      selectCurrency: Function,
      deselectCurrency: Function,
    }
  }
</script>

<style lang="scss">
    @import "../../styles/colors";

    .cs-checkbox {
        position: relative;
        display: inline-block;
        width: calc((100% / 3) - 16px);
        padding: 8px;
        border: 1px solid $gray;
        margin: 8px;
        background-color: $lightGray;

        &:hover { background-color: $mediumTransparencyGray; }

        &--selected,
        &--selected:hover {
            background-color: $white;
        }

        input[type="checkbox"] {
            -webkit-appearance: none;
            position: relative;
            float: left;
            display: inline-block;
            width: 16px;
            height: 16px;
            border: 1px solid $gray;
            border-radius: 4px;
            margin: 6px 8px 6px 0;

            &:focus { outline: none; }

            &:checked:after {
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

        label {
            position: absolute;
            top: 0;
            left: 0;
            width: calc(100% - 30px);
            height: 100%;
            padding-left: 30px;
            font-size: 28px;
            line-height: 44px;
            text-transform: uppercase;
            color: $blue;
            cursor: pointer;
        }
    }
</style>
