<template>
  <transition
    enter-active-class="transition duration-500 ease-in-out"
    leave-active-class="transition duration-500 ease-in-out"
    enter-from-class="-translate-x-full"
    enter-to-class="translate-x-0"
    leave-from-class="translate-x-0"
    leave-to-class="-translate-x-full"
  >
    <SfDrawer
    class="mt-20 !border-none"
      ref="drawerRef"
      :disable-click-away="true"
      v-model="open"
      :placement="placement"
      
    >
      <header class="flex items-center justify-between px-10 py-6">
        <div class="flex items-center">Your Endpoints</div>
      </header>
      <div class="p-5 px-10">
        <strong>
          <p>
            To create a new endpoint, run:
          </p>
          <p class="typography-text-base md:typography-text-lg bg-slate-300 p-5">
            npx vsf-cli add endpoint &lt;endpoint-name>
          </p>
        </strong>
        <MethodList />
   
      </div>
    </SfDrawer>
  </transition>
</template>

<script lang="ts" setup>
import { SfDrawer, SfDrawerPlacement, SfButton, SfIconFavorite, SfIconClose, useTrapFocus } from '@storefront-ui/vue';
import { ref } from 'vue';

const placement = ref<`${SfDrawerPlacement}`>('left');
const open = ref(true);
const drawerRef = ref();

useTrapFocus(drawerRef, { activeState: open });
</script>
