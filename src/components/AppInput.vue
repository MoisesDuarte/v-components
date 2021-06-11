<template>
  <div class="input-container">
    <label v-if="label" :for="id">
      {{ label }}
    </label>
    <input
      :id="id"
      :type="type"
      :placeholder="placeholder"
      :disabled="disabled"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
    />
    <div v-if="hint" class="hint">
      {{ hint }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'app-input-text',
  props: {
    id: {
      type: String,
      required: true
    },
    modelValue: {
      type: [Number, String],
    },
    type: {
      type: String,
      default: 'text'
    },
    label: {
      type: String,
      required: false,
    },
    placeholder: {
      type: String,
      default: '',
    },
    hint: {
      type: String,
      required: false,
    },
    disabled: {
      type: Boolean,
      default: false,
    }
  },
  emits: ['update:modelValue'],
}
</script>

<style lang="less" scoped>
.input-container {
  margin-bottom: 1em;
  text-align: left;

  label, input {
    display: block;
  }

  label {
    font-size: 14px;
    margin-bottom: 0.5em;
    user-select: none;
    transition: font-weight .2s linear;
  }

  input {
    -webkit-appearance: none;
    width: 240px;
    border: none;
    border-radius: 6px 6px 0 0;
    border-bottom: 1px solid #6a6a6a;
    outline: none;
    padding: 6px 4px;
    transition: border-bottom .2s linear, background .2s;

    &:focus  {
      background: #f5f5f5;
      border-bottom: 1px solid black;
    }
  }

  .hint {
    font-size: 12px;
    margin-top: 0.25em;
    color: #6a6a6a;
    user-select: none;
  }

  &:focus-within > label {
    color: black;
  }
}
</style>