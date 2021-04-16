<template>
  <div>
    <label :for="cuid" class="relative text-sm text-gray-600 font-semibold"
      >{{ label }}

      <input
        :id="cuid"
        :value="modelValue"
        :aria-describedby="error ? `${cuid}-error` : null"
        :aria-invlid="error ? true : null"
        v-bind="$attrs"
        class="w-full py-2 pl-10 pr-3 border rounded-lg border-gray-600 text-sm focus:outline-none"
        @input="handleChange"
        @blur="handleBlur"
      />
      <div class="absolute bottom-0 left-0 flex items-center ml-3 text-gray-600">
        <base-icon :iconId="icon" iconClass="fill-current w-4 h-4"></base-icon>
      </div>
    </label>
    <div class="width-full -mt-3">
      <p
        :aria-live="assertive"
        :id="`${cuid}-error`"
        class="text-xs text-red-600"
        v-if="errorMessage"
      >
        {{ errorMessage }}
      </p>
    </div>
  </div>
</template>

<script>
import cuid from 'cuid';
import { useField } from 'vee-validate';

export default {
  props: {
    label: {
      type: String,
      default: '',
    },
    name: {
      type: String,
      default: '',
    },
    value: {
      type: [String, Number],
      default: '',
    },
    icon: {
      type: String,
      default: '',
    },
  },
  setup(props) {
    const { value: modelValue, errorMessage, handleBlur, handleChange, meta } = useField(
      props.name,
      undefined,
      { initialValue: props.value },
    );
    return {
      modelValue,
      errorMessage,
      handleBlur,
      handleChange,
      meta,
      cuid: cuid(),
    };
  },
};
</script>

<style scoped></style>
