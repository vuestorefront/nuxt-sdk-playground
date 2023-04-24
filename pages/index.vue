<template>
<div class="flex justify-center items-center h-screen">
    <div class="p-5 w-96">
      <p class="typography-text-xs md:typography-text-sm font-bold tracking-widest text-neutral-500 uppercase">
        Let's go
      </p>
      <h1 class="typography-headline-2 md:typography-headline-1 md:leading-[67.5px] font-bold mt-2 mb-4">
        Build something amazing
      </h1>
      <p>
      Here's a list of all your endpoints:
      </p>
      <p class="typography-text-base md:typography-text-lg bg-slate-200 p-5" v-for="route in routes">
      <NuxtLink v-if="route.path !== '/'" :to="route.path"><SfLink>{{ route.path }}</SfLink></NuxtLink>    
      </p>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { SfLink } from '@storefront-ui/vue';
const router = useRouter()
const routes = router.getRoutes()
</script>

