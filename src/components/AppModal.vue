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
          <AppButton 
            color="error"
            @click="close">
            Cancel
          </AppButton>
        </slot>
      </footer>
    </div>
  </div>
</template>

<script>
import AppButton from './AppButton';

export default {
  name: 'AppModal',
  components: {
    AppButton,
  },
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
    border-radius: 5px;
    min-width: 300px;

    header {
      position: relative;
      display: flex;
      justify-content: center;
      padding: 1rem;

      .close-button {
        position: absolute;
        top: 0;
        right: 0;
        border: none;
        background: transparent;
        cursor: pointer;
      }
    }

    footer {
      display: flex;
      justify-content: center;
    }

    section {
      padding: 1.25rem 1rem;
    }

  }
}
</style>

