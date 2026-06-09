<script setup lang="ts">
const props = defineProps<{
  title: string
  subtitle?: string
  buttonLabel?: string
}>()

const emit = defineEmits<{
  (e: 'action'): void
}>()
</script>

<template>
  <v-card class="pa-6 rounded-xl mb-6" style="max-width: 520px;">
    <div class="mb-4">
      <h2 class="text-h5 font-weight-bold mb-2">{{ props.title }}</h2>
      <p class="text-body1 text-medium-emphasis" v-if="props.subtitle">{{ props.subtitle }}</p>
    </div>
    <div class="text-body2">
      <slot />
    </div>
    <v-btn
      v-if="props.buttonLabel"
      class="mt-4"
      color="primary"
      variant="tonal"
      @click="emit('action')"
    >
      {{ props.buttonLabel }}
    </v-btn>
  </v-card>
</template>

<style scoped>
.text-body2 {
  line-height: 1.6;
}
</style>
