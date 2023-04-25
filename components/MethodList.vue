<template>
 
    <div class=" ">
      <div v-for="method in methods">
      <div v-if="method.id !== '/'" class=" flex p-4 bg-white border-neutral-300 border-b">
        <NuxtLink :to="'/' + method.name" class="flex flex-row flex-nowrap">
          <SfButton
            aria-label="open-method"
            variant="tertiary"
            square
          >
            <template #prefix>
              <Component :is="SfIconOpenInNew" />
            </template>
            <span class="hidden md:inline-flex">{{ method.name }} </span>
          </SfButton>
        </NuxtLink>
      </div>
    </div>
  </div>
  
  
</template>

<script lang="ts" setup>
import { SfAccordionItem, SfIconOpenInNew } from '@storefront-ui/vue';
import { ref } from 'vue';
import { SfLink } from '@storefront-ui/vue';
import { SfButton } from '@storefront-ui/vue';
import {sdk} from '~/sdk.config';

const res = useState('methodResult')

async function callEndpoint(methodName: string) {
  //ts ignore is needed because the method name is dynamic
  // @ts-ignore
const {data} = await sdk.boilerplate[methodName]('test');
res.value = data
}

function reset() {
res.value = 'waiting to call getCart() ...'
}

const opened = ref<boolean[]>([]);
 
const router = useRouter()
const routes = router.getRoutes()


//add routes to accordionItems
const methods = routes.map((route) => {
  return {
    id: route.path,
    name: route.path.replace("/", ""),
  }
})


</script>
