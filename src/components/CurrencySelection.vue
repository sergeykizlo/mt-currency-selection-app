<template>
    <div class="currency-selection">
        <div class="currency-selection__selected-items">
            <div class="currency-selection__selected-items__item"
                 v-for="currency in currencies"
                 v-if="currency.isSelected === true">
                    {{ currency.name }}
                <div class="currency-selection__selected-items__remove-button"
                     @click="deselectCurrency(currency)">X</div>
            </div>
        </div>
        <div class="currency-selection__items">
            <div v-for="currency in currencies"
                 class="currency-selection__items__item"
                 :class="{ 'currency-selection__items__item--selected' : currency.isSelected }"
                 >
                <input type="checkbox"
                       name="currency"
                       :id="currency.name"
                       :value="currency.name"
                       :checked="currency.isSelected"
                       @change="currency.isSelected ? deselectCurrency(currency) : selectCurrency(currency)"/>
                <label :for="currency.name">{{ currency.name }}</label>
            </div>
        </div>
    </div>
</template>

<script>
    import currencies from '../assets/currencies';

    export default {
        name: "CurrencySelection",
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

<style lang="scss" scoped>
  $white: #fff;
  $black: #000;
  $gray: #a3a3a3;
  $mediumTransparencyGray: rgba(163,163,163, .5);
  $lightGray: #e5e5e5;
  $blue: #114372;
  $red: #ff0301;

  div { box-sizing: border-box; }

  .currency-selection {
      width: 600px;
      padding: 16px;
      border: 1px solid $gray;
      border-radius: 4px;
      margin: 16px;
      box-shadow: 4px 4px 5px 0px $lightGray;
      font-family: Calibri;

      &__selected-items,
      &__items {
          &__item {
              position: relative;
              display: inline-block;
              width: calc((100% / 3) - 16px);
              padding: 8px;
              margin: 8px;
              background-color: $lightGray;
          }
      }

      &__selected-items {
          margin-bottom: 32px;

          &__item {
              border-radius: 4px;
              font-size: 24px;
              line-height: 28px;
              text-align: center;
              text-transform: uppercase;
          }

          &__remove-button {
              position: absolute;
              top: -12px;
              right: -12px;
              width: 24px;
              height: 24px;
              border: 2px solid $white;
              border-radius: 50%;
              font-size: 18px;
              line-height: 20px;
              text-align: center;
              color: $white;
              background-color: $black;
              cursor: pointer;
              transition: all .25s ease-in-out;

              &:hover {
                  border: 2px solid $black;
                  color: $black;
                  background-color: $white;
              }
          }
      }

      &__items {
          &__item {
              border: 1px solid $gray;

              &:hover { background-color: $mediumTransparencyGray; }

              &--selected,
              &--selected:hover {
                background-color: $white;
              }
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
  }

  @media screen and (max-width: 640px) {
      .currency-selection {
          width: 100%;

      }
  }
</style>
