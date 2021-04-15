<template>
  <div>
    <label :for="cuid" class="relative text-sm text-gray-600 font-semibold"
      >{{ label }}

      <input
        :id="cuid"
        class="w-full py-2 pl-10 pr-3 border rounded-lg border-gray-600 text-sm focus:outline-none"
        v-bind="$attrs"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
      />
      <div class="absolute bottom-0 left-0 flex items-center ml-3 text-gray-600">
        <base-icon :iconId="icon" iconClass="fill-current w-4 h-4"></base-icon>
      </div>
    </label>
  </div>
</template>

<script>
import cuid from 'cuid';

export default {
  props: {
    label: {
      type: String,
      default: '',
    },
    modelValue: {
      type: [String, Number],
      default: '',
    },
    icon: {
      type: String,
      default: '',
    },
  },
  data() {
    return {
      cuid: cuid(),
    };
  },
};
</script>

<style scoped></style>
