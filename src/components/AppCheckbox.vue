<template>
  <div class="checkbox-container">
    <input 
      :id="id"
      :value="modelValue"
      :checked="isChecked"
      type="checkbox"
      @change="$emit('update:modelValue', $event.target.checked)"
    />
    <label :for="id">{{ label }}</label>
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
    cursor: pointer;

    &:checked {
      background: royalblue;
      border: 1px solid royalblue;
    }
  }

  label {
    font-size: 14px;
    cursor: pointer;
  }
}
</style>