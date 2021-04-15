<template>
  <div>
    <label :for="cuid" class="text-sm text-gray-600 font-semibold">{{ label }}</label>
    <div class="relative">
      <select
        :id="cuid"
        v-bind="$attrs"
        class="w-full py-2 pl-10 pr-3 border rounded-lg appearance-none text-xs text-gray-600 bg-white outline-none"
        :value="modelValue"
        @change="$emit('update:modelValue', $event.target.value)"
      >
        <option value="">{{ placeholder }}</option>
        <option v-for="(option, index) in options" :key="index" :value="option">{{
          option
        }}</option>
      </select>
      <div class="absolute inset-y-0 left-0 flex items-center ml-3 text-gray-600">
        <base-icon :iconId="icon" iconClass="fill-current w-4 h-4"></base-icon>
      </div>
      <div class="absolute inset-y-0 right-0 flex items-center p-3 text-gray-600">
        <base-icon iconId="arrow-down" iconClass="fill-current w-3 h-3"></base-icon>
      </div>
    </div>
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
    placeholder: {
      type: String,
      default: '',
    },
    icon: {
      type: String,
      default: '',
    },
    modelValue: {
      type: [Number, String],
      default: '',
    },
    options: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped></style>
