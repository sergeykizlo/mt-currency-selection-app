<template>
  <div class="currency-selector">
    <div class="currency-selector__items">
        <currency-selector-item
          v-for="currency in currencies"
          :currency="currency"
          :deselectCurrency="deselectCurrency">
        </currency-selector-item>
    </div>
    <div class="currency-selector__checkboxes">
      <currency-selector-checkbox
        v-for="currency in currencies"
        :currency="currency"
        :selectCurrency="selectCurrency"
        :deselectCurrency="deselectCurrency">
      </currency-selector-checkbox>
    </div>
  </div>
</template>

<script>
  import currencies from '../../assets/currencies';
  import CurrencySelectorItem from './CurrencySelectorItem';
  import CurrencySelectorCheckbox from './CurrencySelectorCheckbox';

  export default {
    name: "CurrencySelection",
    components: {
      'currency-selector-item': CurrencySelectorItem,
      'currency-selector-checkbox': CurrencySelectorCheckbox
    },
    data: function () {
      return {
        currencies: currencies
      }
    },
    methods: {
      selectCurrency(currency) {
        currency.isSelected = true;
      },
      deselectCurrency(currency) {
        currency.isSelected = false;
      }
    }
  }
</script>

<style lang="scss">
  @import "../../styles/colors";

  .currency-selector {
      width: 600px;
      padding: 16px;
      border: 1px solid $gray;
      border-radius: 4px;
      box-shadow: 4px 4px 5px 0px $lightGray;
      margin: 16px;
      font-family: Calibri;

      &__items {
          margin-bottom: 32px;
      }
  }

  @media screen and (max-width: 640px) {
      .currency-selector {
          width: 100%;
      }
  }
</style>
