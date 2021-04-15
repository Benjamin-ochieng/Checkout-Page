<template>
  <div>
    <input
      type="checkbox"
      v-bind="$attrs"
      :id="cuid"
      :checked="modelValue"
      @change="$emit('update:modelValue', $event.target.checked)"
    />
    <label :for="cuid" class="text-sm ml-2 text-gray-600">{{ label }}</label>
  </div>
</template>

<script>
import cuid from 'cuid';

export default {
  data() {
    return {
      cuid: cuid(),
    };
  },
  props: {
    label: {
      type: String,
      default: '',
    },
    modelValue: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<style lang="scss" scoped></style>
