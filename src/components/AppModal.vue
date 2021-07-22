<template>
  <div class="modal-wrapper">
    <div class="modal">
      <header>
        <slot name="header">
          Default Title
        </slot>
        <button 
          class="close-button"
          type="button"
          @click="close">
          X
        </button>
      </header>

      <section>
        <slot name="body">
          Default Body
        </slot>
      </section>
      
      <footer>
        <slot name="footer">
          <button 
            class="cancel-button"
            type="button"
            @click="close">
            Cancel
          </button>
        </slot>
      </footer>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AppModal',
  methods: {
    close() {
      this.$emit('close');
    },
  },
};
</script>

<style lang="less" scoped>
.modal-wrapper {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 2;

  .modal {
    background: #FFFFFF;
    overflow-x: auto;
    display: flex;
    flex-direction: column;
  }
}
</style>

