<template>
  <div>
    <header class="border-b border-gray-500 pb-2">
      <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
        <div class="relative">
          <div>
            <div class="items-center pt-2">
              <NuxtLink to="/">
                <a href="#" class="-m-2 block p-2 font-medium text-gray-900"
                  >Home</a
                >
              </NuxtLink>
            </div>
          </div>
        </div>
      </div>
    </header>
  </div>
  <div class="bg-white">
    <div
      class="mx-auto max-w-2xl py-16 px-4 sm:py-24 sm:px-6 lg:max-w-7xl lg:px-8"
    >
      <div class="lg:grid lg:grid-cols-2 lg:items-start lg:gap-x-8">
        <img :src="product.image" class="object-cover object-center w-9/12" />

        <!-- Product info -->
        <div class="mt-10 px-4 sm:mt-16 sm:px-0 lg:mt-0">
          <h1 class="text-3xl font-bold tracking-tight text-gray-900">
            {{ product.id }}
          </h1>

          <div class="mt-3">
            <p class="text-3xl tracking-tight text-gray-900">
              {{ product.title }}
            </p>
            <h1 class="text-m tracking-tight text-gray-500">
              {{ product.category }}
            </h1>
          </div>

          <div class="mt-6">
            <div
              class="space-y-6 text-base text-gray-700"
              v-html="product.description"
            />
          </div>

          <div class="mt-3">
            <p>$ {{ product.price }}</p>
          </div>

          <div class="mt-3">
            <div class="flex items-center">
              <p class="text-md text-gray-900">
                {{ product.rating.rate }} Rate
              </p>

              <div class="ml-4 flex">
                <a
                  href="#"
                  class="
                    text-sm
                    font-medium
                    text-indigo-600
                    hover:text-indigo-500
                  "
                  >{{ product.rating.count }} reviews</a
                >
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const { id } = useRoute().params;
const uri = "https://fakestoreapi.com/products/" + id;

//fetch detail product

const { data: product } = await useFetch(uri);

definePageMeta({
  layout: "products",
});
</script>