<template>
  <div class="flex justify-center items-center h-screen m-10">
    
    <div class="w-[500px] bg-neutral-100">
      <div> {{str}}</div>
    </div>
    
  </div>
</template>

<script lang="ts" setup>
import { SfLink } from '@storefront-ui/vue';
const router = useRouter()
const routes = router.getRoutes()


const res = useState('methodResult', () => 'waiting ...');
var str = computed(() => JSON.stringify(res.value,null,2));


</script>

<style>
pre {outline: 1px solid #ccc; padding: 5px; margin: 5px; }
.string { color: green; }
.number { color: darkorange; }
.boolean { color: blue; }
.null { color: magenta; }
.key { color: rgb(5, 36, 14); }

</style>
