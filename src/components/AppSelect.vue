<template> 
  <div class="select-container" tabindex="0" @blur="isOpen = false">
    <label 
      v-if="label" 
      :class="{ 'active': isOpen }" 
      @click="focusOnSelect">
      {{ label }}
    </label>
    <div 
      class="selected" 
      :class="{ 'open': isOpen }" 
      @click="isOpen = !isOpen">
      {{ selected && selected.length > 0 ? selected : 'Select a option' }}
    </div>
    <div 
      class="options" 
      :class="{ 'hide': !isOpen }">
      <div 
        v-for="(option, index) of options" 
        :key="index"
        @click="onSelectOption(option)">
        {{ option }}
      </div>
    </div>
    <div 
      v-if="hint" 
      class="hint">
      {{ hint }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'AppSelect',
  props: {
    modelValue: {
      type: String,
    },
    options: {
      type: Array,
      default: [],
    },
    label: {
      type: String,
    },
    hint: {
      type: String,
    }
  },
  data() {
    return {
      isOpen: false,
      selected: this.modelValue,
    };
  },
  methods: {
    focusOnSelect() {
      this.isOpen = true;
    },
    onSelectOption(option) {
      this.selected = option;
      this.$emit('update:modelValue', option);
      this.isOpen = false;
    },
  },
  emits: ['update:modelValue'],
}
</script>

<style lang="less" scoped>
.select-container {
  position: relative;
  width: 248px;
  margin-bottom: 1em;
  text-align: left;
  font-size: 12px;

  label {
    font-size: 14px;
    user-select: none;

    &.active {
      color: black;
    }
  }

  .selected {
    background: #ffffff;
    border: 1px solid #6a6a6a;
    border-radius: 2px;
    padding-left: 0.75em;
    margin-top: 0.5em;
    cursor: pointer;
    user-select: none;
    height: 27px;
    line-height: 27px;

    &.open {
      border: 1px solid black;
      color: black;
      border-radius: 2px 2px 0 0;
    }
  }

  .options {
    position: absolute;
    left: 0;
    right: 0;
    background: #ffffff;
    color: #333333;
    border-left: 1px solid black;
    border-right: 1px solid black;
    border-bottom: 1px solid black;
    border-radius: 0 0 4px 4px;
    z-index: 1;
    overflow: hidden;

    & div {
      height: 27px;
      line-height: 27px;
      padding-left: 0.75em;
      cursor: pointer;
      user-select: none;

      &:hover {
        background: #f5f5f5;
      }
    }

    &.hide {
      display: none;
    }
  }

  .hint {
    font-size: 12px;
    margin-top: 0.25em;
    color: #6a6a6a;
    user-select: none;
  }
}
</style>