<template>
  <div class="bg-white">
    <h2 class="text-3xl font-bold text-gray-900 text-center m-16">
      Products List
    </h2>

    <section
      aria-labelledby="product-heading"
      class="mt-6 lg:col-span-2 lg:mt-0 xl:col-span-3"
    >
      <div
        class="
          grid grid-cols-1
          gap-y-4
          sm:grid-cols-2 sm:gap-x-6 sm:gap-y-10
          lg:gap-x-8
          xl:grid-cols-3
          p-6
          lg:p-10
        "
      >
        <div
          v-for="product in products"
          :key="product.id"
          class="
            group
            relative
            flex flex-col
            overflow-hidden
            rounded-lg
            border border-gray-200
            bg-white
          "
        >
          <nuxt-link :to="`/products/${product.id}`">
            <div
              class="
                aspect-w-3 aspect-h-4
                group-hover:opacity-75
                sm:aspect-none sm:h-96
              "
            >
              <img
                :src="product.image"
                class="
                  w-5/12
                  rounded-lg
                  group-hover:opacity-75
                  lg:ml-28 lg:mt-10
                  ml-8
                  object-cover object-center
                "
              />
            </div>
            <div class="flex flex-1 flex-col space-y-2 p-4">
              <h3 class="text-sm font-medium text-gray-900">
                <a :href="product.href">
                  <span aria-hidden="true" class="absolute inset-0" />
                  {{ product.title }}
                </a>
              </h3>

              <div class="flex flex-1 flex-col justify-end">
                <p class="text-base font-medium text-gray-900">
                  ${{ product.price }}
                </p>
              </div>
            </div>
          </nuxt-link>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup >
definePageMeta({
  layout: "products",
});
const { data: products } = await useFetch("https://fakestoreapi.com/products");
</script>