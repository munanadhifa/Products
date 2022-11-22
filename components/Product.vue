<template>
  <div class="bg-white">
    <h2 class="text-3xl font-bold text-gray-900 text-center m-16">
      Products List
    </h2>
    <div class="mx-auto max-w-7xl overflow-hidden sm:px-6 lg:px-8">
      <div
        class="
          -mx-px
          grid grid-cols-2
          border-l border-gray-200
          sm:mx-0
          md:grid-cols-3
          lg:grid-cols-4
        "
      >
        <div
          v-for="product in products"
          :key="product.id"
          class="group relative border-r border-b border-gray-200 p-6 lg:p-10"
        >
          <nuxt-link :to="`/products/${product.id}`">
            <div
              class="
                aspect-w-1 aspect-h-1
                overflow-hidden
                w-3/6
                rounded-lg
                group-hover:opacity-75
                lg:ml-16
                ml-8
              "
            >
              <img
                :src="product.image"
                class="object-cover object-center group-hover:opacity-75"
              />
            </div>
            <div class="pt-10 pb-4 text-center">
              <h3 class="text-sm font-medium text-gray-900">
                <a :href="product.href">
                  <span aria-hidden="true" class="absolute inset-0" />
                  {{ product.title }}
                </a>
              </h3>
              <p class="mt-4 text-base font-medium text-gray-900">
                {{ product.price }}
              </p>
            </div>
          </nuxt-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup >
definePageMeta({
  layout: "products",
});
const { data: products } = await useFetch("https://fakestoreapi.com/products");
</script>