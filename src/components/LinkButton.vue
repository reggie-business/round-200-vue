<script setup lang="ts">
defineProps<{
  label: string
  url: string
  icon: string
}>()

const isMailto = (url: string) => url.startsWith('mailto:')
</script>

<template>
  <v-btn
    :href="url"
    :target="isMailto(url) ? undefined : '_blank'"
    :rel="isMailto(url) ? undefined : 'noreferrer'"
    size="large"
    block
    class="text-none"
    variant="flat"
    color="primary"
    :prepend-icon="icon"
  >
    {{ label }}
  </v-btn>
</template>
