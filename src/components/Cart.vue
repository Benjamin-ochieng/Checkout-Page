<template>
  <div class="sm:w-1/2 sm:px-6">
    <div id="cart" class="mt-5 p-6 bg-gray-200 rounded-lg lg:mt-20">
      <item :items="checkout.items"></item>
      <div id="cart-summary" class="pt-6">
        <div id="total" class="text-sm py-2 flex justify-between text-gray-900">
          <p>Subtotal</p>
          <p>${{ cartTotal }}</p>
        </div>
        <div
          id="shipping"
          class="text-sm py-2 flex justify-between text-gray-900 border-t border-b border-gray-500"
        >
          <p>Shipping</p>
          <p>+${{ shipping }}</p>
        </div>
        <div id="total" class="text-sm py-2 flex justify-between text-gray-900 font-black">
          <p>Total</p>
          <p>${{ total }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Item from '@/components/Item.vue';

export default {
  components: {
    Item,
  },
  data() {
    return {
      checkout: {
        items: [
          {
            name: 'Vintage Backbag',
            // eslint-disable-next-line global-require
            image: require('@/assets/images/photo1.png'),
            price: 94.99,
            discount: 57,
            qty: 1,
          },
          {
            name: 'Levi Shoes',
            // eslint-disable-next-line global-require
            image: require('@/assets/images/photo2.png'),
            price: 74.99,
            discount: 60,
            qty: 1,
          },
        ],
        info: [],
      },
    };
  },
  methods: {
    itemTotals: items =>
      items.map(({ price, qty, discount }) =>
        discount ? ((price * discount) / 100) * qty : price * qty,
      ),
    sum: arr => Math.round(arr.reduce((a, b) => a + b) * 100) / 100,
    reviewDetails(details) {
      this.checkout.info.push(details);
    },
  },
  computed: {
    cartTotal() {
      return this.sum(this.itemTotals(this.checkout.items));
    },
    shipping() {
      return this.cartTotal < 100 ? 19 : 0;
    },
    // eslint-disable-next-line vue/return-in-computed-property
    total() {
      const result = this.cartTotal + this.shipping;
      this.$emit('get-total', result);
      return result;
    },
  },
};
</script>

<style lang="scss" scoped></style>
