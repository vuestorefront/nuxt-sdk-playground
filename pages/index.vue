<template>
  <main class="flex flex-col items-center md:pt-24 md:py-0 py-24 gap-12 text-white mb-44 md:mb-0">
    <h1 class="typography-headline-2 font-semibold text-primary-600">Welcome!</h1>
    <p class="typography-headline-4 text-center">
      Start building new Integration with Vue Storefront SDK Integration Boilerplate
    </p>
    <section class='flex flex-col gap-12 items-center'>
      <NumberTitle :number="1" :title="'Make your first API call using SDK'">
        <SfButton :tag="NuxtLink" to="/methods/exampleMethod" type=" button" onClick={hitExampleMethodApi}
          class='bg-primary-600 py-2 px-4'>
          Open Example Method page and call API
        </SfButton>
      </NumberTitle>

      <NumberTitle :number="2" :title="'Create new method using CLI'">
        <TabBrowser :data="tabBrowserData" />
      </NumberTitle>

      <NumberTitle :number="3" :title="'Read documentation and start developing integration'">
        <Grid :columns="3">
          <template #1>
            <Card :title="'SDK Documentation'" :description="'General SDK Documentation'"
              href="https://docs.vuestorefront.io/sdk/sdk/" target=”_blank”>
              <template #icon>
                <SfIconViewList class="text-primary-600 w-8" />
              </template>
            </Card>
          </template>
          <template #2>
            <Card :title="'Integration Boilerplate'" :description="'Integration Boilerplate Repository'"
              href="https://github.com/vuestorefront/integration-boilerplate" target=”_blank”>
              <template #icon>
                <SfIconViewList class="text-primary-600 w-8" />
              </template>
            </Card>
          </template>
          <template #3>
            <Card title="Storefront UI" description="Storefront UI docs"
              href="https://docs.storefrontui.io/v2/" target=”_blank”>
              <template #icon>
                <SfIconViewList class="text-primary-600 w-8" />
              </template>
            </Card>
          </template>
        </Grid>
      </NumberTitle>
    </section>
  </main>
</template>

<script lang="ts" setup>
import { SfButton, SfIconViewList } from '@storefront-ui/vue';
import { resolveComponent } from 'vue';

const NuxtLink = resolveComponent('NuxtLink');

const res = useState('waiting to call exampleMethod() ...');
const tabBrowserData = [{
  language: 'bash', commands: {
    command: 'npx @vue-storefront/cli add endpoint coolEndpoint',
    description: 'Add new method to the integration'
  }
}
]
</script>
```
