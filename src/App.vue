<template>
    <div class="app">
        <currency-selector></currency-selector>
    </div>
</template>

<script>
  import './styles/reset-styles.scss';
  import CurrencySelector from './components/CurrencySelector/CurrencySelector';

  export default {
      components: {
          'currency-selector': CurrencySelector
      }
  }
</script>

<style lang="scss">
    div { box-sizing: border-box; }

    .app {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }
</style>
