<template>
  <div>
    <h1 class="text-2xl font-semibold text-gray-900">Checkout</h1>
    <info />
  </div>
</template>

<script>
import Info from '@/components/Info.vue';

export default {
  components: {
    Info,
  },
  methods: {
    reviewDetalis(details) {
      console.log(this.items);
      console.log(details);
    },
  },
};
</script>

<style lang="scss" scoped></style>
