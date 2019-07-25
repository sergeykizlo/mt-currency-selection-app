<template>
  <div class="currency-selector">
    <div class="currency-selector__items" v-if="selectedCurrencies.length > 0">
      <template v-for="currency in selectedCurrencies">
        <currency-selector-item :key="currency.name"
                                :name="currency.name"
                                v-model="currency.selected"
        />
      </template>
    </div>
    <div class="currency-selector__checkboxes">
      <template v-for="currency in currencies">
        <currency-selector-checkbox :key="currency.name"
                                    :name="currency.name"
                                    v-model="currency.selected"
        />
      </template>
    </div>
  </div>
</template>

<script>
  import currencies from '../../assets/currencies';
  import CurrencySelectorItem from './CurrencySelectorItem';
  import CurrencySelectorCheckbox from './CurrencySelectorCheckbox';

  export default {
    name: "CurrencySelector",
    components: {
      CurrencySelectorItem,
      CurrencySelectorCheckbox
    },
    data() {
      return {
        currencies: currencies
      }
    },
    computed: {
        selectedCurrencies() {
            return this.currencies.filter(currency => currency.selected);
        }
    }
  }
</script>

<style lang="scss" scoped>
  @import "../../styles/colors";

  .currency-selector {
      width: 600px;
      padding: 16px;
      border: 1px solid $gray;
      border-radius: 4px;
      box-shadow: 4px 4px 5px 0 $lightGray;
      margin: 16px;
      font-family: Calibri, sans-serif;

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
