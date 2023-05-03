<template>
    <div class=" ">
        <div v-for="method in menuRoutes">
            <div class=" flex p-4 bg-white border-neutral-300 border-b">
                <NuxtLink :to="method.path" class="flex flex-row flex-nowrap">
                    <SfButton aria-label="open-method" variant="tertiary" square>
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
import { sdk } from '~/sdk.config';

const res = useState('methodResult')

async function callEndpoint(methodName: string) {
    //ts ignore is needed because the method name is dynamic
    // @ts-ignore
    const { data } = await sdk.boilerplate[methodName]('test');
    res.value = data
}

type MethodType = {
    id: string;
    name: string;
};
function reset() {
    res.value = 'waiting to call getCart() ...'
}

const opened = ref<MethodType[]>([]);

const router = useRouter()
const routes = router.getRoutes()
const menuRoutes = useState(() => [{
    path: '/methods/exampleMethod',
    name: 'exampleMethod'
}])

//add routes to accordionItems
routes.map((route) => {
    if (route.path.includes("/methods") && !inRouteArray(route.path)) {
        menuRoutes.value.push({
            path: route.path,
            name: route.path.replace("/methods/", ""),
        })
    }
})

function inRouteArray(route: string) {
    return menuRoutes.value.some((item) => item.path === route)
}

</script>
