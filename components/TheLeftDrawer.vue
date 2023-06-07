<template>
  <div
    class="fixed bottom-0 left-0 w-full h-52 z-10 bg-neutral-900 md:w-72 md:h-screen md:relative text-neutral-900 flex flex-col items-center mr-0 border py-2 md:py-8 px-2 md:px-4">
    <NuxtLink to="/"
      class='flex w-full md:w-72 md:justify-center md:items-end border-b border-primary-600 justify-start items-start p-2 md:p-4 gap-1'>
      <SfIconViewList class="text-primary-600 w-8 fill-current" />
      <h3 class="typography-headline-3 text-gray-200">
        Methods
      </h3>
    </NuxtLink>
    <MethodList />
  </div>
</template>

<script lang="ts" setup>
import { SfIconViewList } from '@storefront-ui/vue';
</script>
