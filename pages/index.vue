<template>
<div class="flex justify-center items-center h-screen">
    <div class="p-5 w-105">
      <p class="typography-text-xs md:typography-text-sm font-bold tracking-widest text-neutral-500 uppercase">
        Let's go
      </p>
      <h1 class="typography-headline-2 md:typography-headline-1 md:leading-[67.5px] font-bold mt-2 mb-4">
        Build something amazing
      </h1>
      <div class="my-12">
        <div>
          To create a new enpoint, run:
         <br>
         <p class="typography-text-base md:typography-text-lg bg-slate-300 p-5">
          npx vsf-cli add endpoint &lt;endpoint-name>
         </p>
        </div>
      </div>
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

