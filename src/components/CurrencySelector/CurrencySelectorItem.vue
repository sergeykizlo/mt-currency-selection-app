<template>
  <div class="cs-item">
    {{ name }}
    <div class="cs-item__remove-button"
         @click="onRemoveClick"
    >
      X
    </div>
  </div>
</template>

<script>
  export default {
    name: "CurrencySelectorItem",
    props: {
      name: String,
      value: Boolean
    },
    methods: {
      onRemoveClick() {
        this.$emit('input', false);
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import "../../styles/colors";

  .cs-item {
      position: relative;
      display: inline-block;
      width: calc((100% / 3) - 16px);
      padding: 8px;
      border-radius: 4px;
      margin: 8px;
      font-size: 24px;
      line-height: 28px;
      text-align: center;
      text-transform: uppercase;
      background-color: $lightGray;

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
</style>
