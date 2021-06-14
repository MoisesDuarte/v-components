<template>
  <div class="checkbox-container">
    <input 
      :id="id"
      :value="modelValue"
      :checked="isChecked"
      type="checkbox"
      @change="$emit('update:modelValue', $event.target.checked)"
    />
    <label v-if="label" :for="id">
      {{ label }}
    </label>
    <div v-if="hint" class="hint">
      {{ hint }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'AppCheckbox',
  props: {
    id: {
      type: String,
      required: true,
    },
    modelValue: {
      type: Boolean,
    },
    label: {
      type: String,
      reqired: false,
    },
    hint: {
      type: String,
      required: false,
    }
  },
  computed: {
    isChecked() {
      return this.modelValue === true;
    },
  },
  emits: ['update:modelValue'],
}
</script>

<style lang="less" scoped>
.checkbox-container {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  margin-bottom: 1em;
  user-select: none;

  input[type=checkbox] {
    -webkit-appearance: none;
    border: 1px solid #6a6a6a;
    border-radius: 2px;
    padding: 8px;
    margin-right: 0.5em;
    margin-left: 0;
    transition: background-color .2s;
    cursor: pointer;

    &:checked {
      position: relative;
      background: royalblue;
      border: 1px solid royalblue;

      &:after {
        content: '✓';
        position: absolute;
        top: -2px;
        left: 3px;
        color: white;
      }
    }
  }

  label {
    font-size: 14px;
    cursor: pointer;
  }

  .flex-break {
    display: flex;
    flex-basis: 100%;
  }

  .hint {
    flex-basis: 100%;
    font-size: 12px;
    margin-left: 2.125em;
    color: #6a6a6a;
    user-select: none;
  }
}
</style>