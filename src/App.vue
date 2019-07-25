<template>
    <div class="app">
        <currency-selector />
    </div>
</template>

<script>
  import CurrencySelector from './components/CurrencySelector/CurrencySelector';

  export default {
      components: {
          CurrencySelector,
      }
  }
</script>

<style lang="scss">
    @import './styles/reset-styles.scss';

    .app {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
    }
</style>
