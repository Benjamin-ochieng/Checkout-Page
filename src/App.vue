<template>
  <div id="app" class="min-h-screen px-4 bg-white sm:px-48">
    <div id="nav" class="py-5">
      <router-link to="/" class="text-gray-900">Home</router-link> |
      <router-link to="/checkout" class="text-gray-900">Checkout</router-link>
    </div>
    <div class="flex min-w-screen mb-8">
      <div class=""></div>
      <base-notification
        v-if="gStore.flashMessage"
        :message="gStore.flashMessage"
      ></base-notification>
    </div>
    <router-view />
  </div>
</template>
<script>
export default {
  inject: ['gStore'],
};
</script>
<style src="@/assets/css/tailwind.css"></style>
<style></style>
