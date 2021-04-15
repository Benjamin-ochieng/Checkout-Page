<template>
  <div class="m-auto sm:w-1/2">
    <div class="bg-white rounded-lg border border-gray-300 p-3 shadow-lg animate-fade-out-up">
      <div class="flex">
        <div class="px-2 text-green-500">
          <base-icon iconId="tick" class="fill-current"></base-icon>
        </div>
        <div class="ml-2 mr-6">
          <p class="block text-gray-500">
            {{ message }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    message: {
      type: String,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped></style>
