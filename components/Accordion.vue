<template>
 
    <div class=" ">
      <SfAccordionItem   v-for="({ id, methodName }, index) in accordionItems" :key="id" v-model="opened[index]">
      <template #summary>
        <p class="p-4 font-medium hover:bg-primary-100 active:primary-100">

          <div>
           {{ methodName  }}
          </div>
        </p>
      </template>
      <div class=" flex p-4 bg-white border-neutral-300 border-b">
        <SfButton
          type="button"
          @click="callEndpoint(methodName)"
        >
        call {{ methodName }}
        </SfButton>
        <NuxtLink :to="'/' + methodName" class="flex flex-row flex-nowrap">
          <SfButton
            aria-label="open-method"
            variant="tertiary"
            square
          >
            <template #prefix>
              <Component :is="SfIconOpenInNew" />
            </template>
            <span class="hidden md:inline-flex">open</span>
          </SfButton>
          
        </NuxtLink>
       
       

      </div>
    </SfAccordionItem>
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
const accordionItems = routes.map((route) => {
  return {
    id: route.path,
    methodName: route.path.replace("/", ""),
  }
})


</script>
