<script setup lang="ts">
import { ref } from 'vue'

const links = [
  {
    label: 'Portfolio',
    url: 'https://portfolio.randyollins.com',
    icon: 'mdi-briefcase',
  },
  {
    label: 'Dribbble',
    url: 'https://dribbble.com/randyollins',
    icon: 'mdi-dribbble',
  },
  {
    label: 'LinkedIn',
    url: 'https://linkedin.com/in/randyollins',
    icon: 'mdi-linkedin',
  },
  {
    label: 'Email',
    url: 'mailto:hello@randyollins.com',
    icon: 'mdi-email',
  },
]
</script>

<template>
  <v-container class="fill-height d-flex align-center justify-center">
    <v-row justify="center" align="center">
      <v-col cols="12" sm="10" md="8" lg="6">
        <v-card class="pa-8" rounded="xl">
          <!-- Profile Section -->
          <div class="text-center mb-8">
            <v-avatar size="120" class="mb-6 d-block mx-auto" color="gradient-primary">
              <span class="text-h5 font-weight-bold">RO</span>
            </v-avatar>
            <h1 class="text-h4 font-weight-bold mb-3">Randy Ollins</h1>
            <p class="text-body1 text-medium-emphasis">
              Building clean link-in-bio experiences that feel polished and personal.
            </p>
          </div>

          <!-- Links Section -->
          <div class="d-flex flex-column gap-3">
            <v-btn
              v-for="link in links"
              :key="link.label"
              :href="link.url"
              :target="link.url.startsWith('mailto:') ? undefined : '_blank'"
              :rel="link.url.startsWith('mailto:') ? undefined : 'noreferrer'"
              size="large"
              block
              class="text-none"
              variant="flat"
              color="primary"
              :prepend-icon="link.icon"
            >
              {{ link.label }}
            </v-btn>
          </div>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped>
.gap-3 {
  gap: 0.75rem;
}

:deep(.gradient-primary) {
  background: linear-gradient(135deg, #5b8cff, #8f5bff) !important;
}
</style>
