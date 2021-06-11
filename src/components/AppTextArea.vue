<template>
  <div class="text-area-container">
    <label v-if="label" :for="id">
      {{ label }}
    </label>
    <div class="textarea-wrapper">
      <textarea 
        :id="id"
        :class="{ 'no-resize': !resizable }"
        :rows="rows"
        :disabled="disabled"
        :minlength="minlength"
        :maxlength="maxlength"
        :placeholder="placeholder"
        @input="$emit('update:modelValue', $event.target.value)">
        {{ modelValue }}
      </textarea>
      <div v-if="counter" class="counter">
        Characters: {{ modelValue ? modelValue.length : 0 }}
      </div>
    </div>
    <div v-if="hint" class="hint">
      {{ hint }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'AppTextArea',
  props: {
    id: {
      type: String,
      required: true,
    },
    modelValue: {
      type: [Number, String],
    },
    cols: {
      type: Number,
      default: 30,
    },
    rows: {
      type: Number,
      default: 10,
    },
    resizable: {
      type: Boolean,
      default: false,
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    minlength: {
      type: Number,
      required: false,
    },
    maxlength: {
      type: Number,
      required: false,
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
    counter: {
      type: Boolean,
      default: false,
    },
  },
  emits: ['update:modelValue'],
}
</script>

<style lang="less" scoped>
.text-area-container {
  margin-bottom: 1em;

  label {
    font-size: 14px;
    user-select: none;
    transition: font-weight .2s linear;
  }
  .textarea-wrapper {
    border: 1px solid #6a6a6a;
    border-radius: 2px;
    margin-top: 0.25em;
    padding: 6px;

    textarea {
      -webkit-appearance: none;
      width: 100%;
      padding: 0;
      border: none;
      outline: none;
      font-size: 12px;
      font-family: Avenir, Helvetica, Arial, sans-serif;;

      &.no-resize {
        resize: none;
      }
    }

    .counter {
      font-size: 12px;
      text-align: right;
    }
  }

  .hint {
    font-size: 12px;
    color: #6a6a6a;
    user-select: none;
    margin-top: 0.25em;
  }
}
</style>