<template>
  <div class="button-container">
    <button
      :class="color"
      :type="type"
      @click="$emit('click')">
      <slot></slot>
    </button>
  </div>
</template>

<script>
export default {
  name: 'AppButton',
  props: {
    type: {
      type: String,
      default: 'button'
    },
    color: {
      type: String,
      default: 'red',
    }
  }
}
</script>

<style lang="less" scoped>
.button-container {
  button {
    -webkit-appearance: none;
    position: relative;
    background: transparent;
    border: 1px solid black;
    border-radius: 2px;
    padding: 6px 12px;
    margin-bottom: 1em;
    cursor: pointer;

    &.primary {
      background: royalblue;
      border: 1px solid royalblue;
      color: #ffffff;
    }

    &.secondary {
      background: darkorange;
      border: 1px solid darkorange;
      color: #ffffff;
    }

    &.error {
      background: tomato;
      border: 1px solid tomato;
      color: #ffffff;
    }

    &.success {
      background: forestgreen;
      border: 1px solid forestgreen;
      color: #ffffff;
    }
  }
}
</style>