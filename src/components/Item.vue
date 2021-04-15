<template>
  <ul>
    <li id="item" class="flex mb-8" v-for="(item, index) in items" :key="index">
      <div class="w-1/2">
        <img
          :src="item.image"
          :alt="item.name"
          class="h-32  object-cover object-center rounded-md shadow"
        />
      </div>
      <div class="w-1/2 flex flex-col justify-between">
        <p class="text-sm text-gray-900">{{ item.name }}</p>
        <div class="flex items-center">
          <p class="text-sm text-gray-900" :class="{ discounted: item.discount }">
            {{ item.price }}
          </p>
          <span class="text-sm px-3 text-orange-500" v-if="item.discount">{{
            discountedPrice(item)
          }}</span>
        </div>
        <div
          id="buttons"
          class="w-32 p-3 flex justify-between border border-solid rounded-lg border-gray-900"
        >
          <button
            class="w-5 h-5 flex justify-center items-center bg-gray-400 rounded focus:outline-none"
            @click="decreaseItemQty(item)"
          >
            -
          </button>
          <input
            type="number"
            min="0"
            max="100"
            class="h-5 w-6 appearance-none m-0 text-xs"
            v-model="item.qty"
          />
          <button
            class="w-5 h-5 flex justify-center items-center bg-gray-400 rounded active:outline-none"
            @click="increaseItemQty(item)"
          >
            +
          </button>
        </div>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
  methods: {
    discountedPrice(item) {
      // rounding an int: Math.round(int * 100) / 100
      return Math.round(((item.price * item.discount) / 100) * 100) / 100;
    },
    decreaseItemQty(item) {
      // eslint-disable-next-line no-param-reassign
      if (item.qty > 0) item.qty -= 1;
      console.log(item.qty);
      return item;
    },
    increaseItemQty(item) {
      // eslint-disable-next-line no-param-reassign
      if (item.qty < 100) item.qty += 1;
      console.log(item.qty);
      return item;
    },
  },
};
</script>

<style scoped>
.discounted {
  @apply line-through;
  @apply text-xs;
}
</style>
