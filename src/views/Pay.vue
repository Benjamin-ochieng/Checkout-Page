<template>
  <div class="sm:w-1/2 sm:m-auto">
    <div id="cart" class="mt-5 p-6 bg-gray-200 rounded-lg lg:mt-20">
      <div id="cart-summary" class="pt-6">
        <div
          id="shipping"
          class="text-sm py-2 flex justify-between text-gray-900 border-t  border-gray-500"
        >
          <p>Address</p>
          <p>{{ details.address }}</p>
        </div>
        <div
          id="shipping"
          class="text-sm py-2 flex justify-between text-gray-900 border-t border-b border-gray-500"
        >
          <p>Total</p>
          <p>+${{ details.total }}</p>
        </div>
      </div>
      <div class="flex justify-end py-10">
        <input type="submit" value="Pay" class="px-10 py-4 rounded-lg bg-orange-500 text-white" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['paymentDetails'],
  computed: {
    details() {
      return JSON.parse(this.paymentDetails);
    },
  },
};
</script>

<style lang="scss" scoped></style>
