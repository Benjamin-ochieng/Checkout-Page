<template>
  <div class="sm:flex sm:flex-row-reverse">
    <cart v-on:get-total="getTotal" />
    <div class="info py-10 sm:w-1/2 sm:px-6">
      <form @submit.prevent="reviewOrder">
        <fieldset>
          <legend class="text-gray-900 font-semibold">
            Contact information
          </legend>
          <base-input
            label="E-mail"
            v-model="email"
            type="email"
            name="email"
            icon="email"
            placeholder="john.doe@email.com"
            class="mb-4"
            required
          />
          <base-input
            label="Phone"
            v-model="phone"
            type="tel"
            name="tel"
            icon="telephone"
            placeholder="Your phone number"
            class="mb-4"
          />
        </fieldset>
        <fieldset class="mt-10">
          <legend class="text-gray-900 font-semibold">Shipping address</legend>
          <base-input
            label="Full name"
            v-model="names"
            type="text"
            name="name"
            icon="user"
            placeholder="John Doe"
            class="mb-4"
          />
          <base-input
            label="Address"
            v-model="address"
            type="text"
            name="address"
            icon="address"
            placeholder="Your Address"
            class="mb-4"
          />
          <base-input
            label="City"
            v-model="city"
            type="text"
            name="city"
            icon="city"
            placeholder="Your city"
            class="mb-4"
          />
          <div class="flex">
            <div class="w-1/2">
              <base-select
                :options="countries"
                label="Country"
                placeholder="Your country..."
                name="country"
                icon="flag"
                v-model="country"
              />
            </div>
            <div class="m-3"></div>
            <div class="w-1/2">
              <base-input
                label="Postal Code"
                v-model="postalCode"
                type="text"
                name="postalCode"
                icon="post-box"
                placeholder="Your city"
                class="mb-4"
              />
            </div>
          </div>
          <base-check
            label="Save this information for next time"
            class="mt-4"
            v-model="saveInfo"
          ></base-check>
        </fieldset>
        <div class="flex justify-end py-10">
          <input
            type="submit"
            value="Continue"
            class="px-10 py-4 rounded-lg bg-orange-500 text-white"
          />
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import Cart from '@/components/Cart.vue';

export default {
  components: {
    Cart,
  },
  inject: ['gStore'],
  data() {
    return {
      test: {
        text: 'Hel',
      },
      email: '',
      phone: '',
      names: '',
      address: '',
      city: '',
      country: '',
      postalCode: '',
      saveInfo: false,
      countries: ['United States', 'Canada', 'Mexico'],
      total: 0,
    };
  },
  methods: {
    reviewOrder() {
      const checkoutDetails = {
        email: this.email,
        phone: this.phone,
        names: this.names,
        address: this.address,
        city: this.city,
        country: this.country,
        postalCode: this.postalCode,
        saveInfo: this.saveInfo,
        total: this.total,
      };
      this.gStore.flashMessage = 'Success, confirm your order and pay';
      setTimeout(() => {
        this.gStore.flashMessage = '';
      }, 5000);
      this.$router.push({
        name: 'Pay',
        params: { paymentDetails: JSON.stringify(checkoutDetails) },
      });

      this.email = '';
      this.phone = '';
      this.name = '';
      this.address = '';
      this.city = '';
      this.country = '';
      this.postalCode = '';
      this.saveInfo = false;
      this.total = 0;
    },
    getTotal(int) {
      this.total = int;
    },
  },
};
</script>

<style lang="scss" scoped></style>
