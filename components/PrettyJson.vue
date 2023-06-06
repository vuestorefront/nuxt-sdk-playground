<template>
  <div class="box">
    <!-- <JsonViewer :value="jsonData" copyable boxed sort theme="light"  @onKeyClick="keyClick"/> -->
    <h4>Response</h4>
    <JsonViewer class="min-h-[800px] min-w-[500px]" :value="jsonData" expandDepth="5" expanded copyable boxed sort
      theme="dark" />
  </div>
</template>

<script setup>
import { JsonViewer } from "vue3-json-viewer"
// if you used v1.0.5 or latster ,you should add import "vue3-json-viewer/dist/index.css"
import "vue3-json-viewer/dist/index.css";
import { reactive, ref } from "vue";

const jsonData = useState('methodResult', () => 'waiting ...');
</script>

<style>
.box {
  margin-top: 1rem;
}
</style>
