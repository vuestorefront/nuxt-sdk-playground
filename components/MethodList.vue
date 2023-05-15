<template>
    <div class="w-full">
        <div class="overflow-auto pl-4 pr-8 pt-8" :class="{
            'hidden': !menuRoutes.length,
            'md:hidden': menuRoutes.length
        }">
            <SfScrollable
                class="items-center [&::-webkit-scrollbar]:hidden [-ms-overflow-style:none] [scrollbar-width:none]">
                <div v-for="method in menuRoutes" :key="method.name"
                    class="flex items-center justify-center text-gray-300 border border-neutral-400 h-20 px-4 shrink-0 gap-2">
                    <NuxtLink :to="method.path" class="flex flex-row">
                        {{ method.name }}
                        <SfIconOpenInNew class='text-primary-600 fill-current w-8' />
                    </NuxtLink>
                </div>
            </SfScrollable>
        </div>


        <div v-if="!menuRoutes.length">
            <div class="text-white mt-4 items-center flex md:flex-col gap-2">
                <SfIconVisibilityOff class='md:w-12' />
                No methods available
            </div>
        </div>

        <div v-if="menuRoutes.length">
            <div class='hidden md:flex flex-col border-t mt-2 border-primary-600' v-for="method in menuRoutes"
                :key="method.name">
                <NuxtLink :href="method.path" class='text-white flex items-center gap-2 border-b justify-center p-4'>
                    {{ method.name }}
                    <SfIconOpenInNew class='text-primary-600 fill-current md:w-8' />
                </NuxtLink>
            </div>
        </div>
    </div>
</template>

<script lang="ts" setup>
import { SfAccordionItem, SfIconOpenInNew, SfIconVisibilityOff, SfScrollable } from '@storefront-ui/vue';

const res = useState('methodResult')

type MethodType = {
    id: string;
    name: string;
};

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

// menuRoutes.value = [];

function inRouteArray(route: string) {
    return menuRoutes.value.some((item) => item.path === route)
}

</script>
