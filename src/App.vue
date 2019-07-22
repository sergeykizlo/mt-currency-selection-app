<template>
    <div class="app">
        <app-currency-selection></app-currency-selection>
    </div>
</template>

<script>
  import './styles/reset-styles.scss';
  import CurrencySelection from './components/CurrencySelection';

  export default {
      components: {
          'app-currency-selection': CurrencySelection
      }
  }
</script>

<style lang="scss">
    .app {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }
</style>
