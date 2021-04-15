<template>
  <div>
    <svg :class="iconClass">
      <use v-bind="{ 'xlink:href': `/icons-sprite.svg#${iconId}` }" />
    </svg>
  </div>
</template>

<script>
export default {
  props: {
    iconClass: {
      type: String,
      default: 'w-4 h-4',
    },
    iconId: {
      type: String,
      default: '',
    },
  },
};
</script>

<style scoped></style>
