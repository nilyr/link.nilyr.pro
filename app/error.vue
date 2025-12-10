<script setup lang="ts">
import type { NuxtError } from '#app'
import errorImage from './assets/images/404.svg?raw'

const props = defineProps({
  error: Object as () => NuxtError
})

const route = useRoute()

if (props.error?.statusCode === 404) {
  if (!route.path.startsWith('/dashboard')) {
    clearError({ redirect: 'https://nilyr.pro' })
  }
}
</script>

<template>
  <NuxtLayout name="default">
    <a
      class="
        mx-auto flex h-full w-full max-w-[600px] items-center justify-center
        [&_svg]:w-full
      "
      href="/"
      v-html="errorImage"
    />
  </NuxtLayout>
</template>
