<script setup lang="ts">
import LinkButton from '@/components/LinkButton.vue'
import MyCustomCard from '@/components/MyCustomCard.vue'

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

const handleCardAction = () => {
  window.alert('Custom card action triggered!')
}
</script>

<template>
  <v-container fluid class="d-flex align-center justify-center px-4 py-8">
    <v-row justify="center" align="center" class="w-100">
      <v-col cols="12" sm="11" md="10" lg="6" class="d-flex justify-center">
        <MyCustomCard
          title="Welcome"
          subtitle="A reusable custom component"
          buttonLabel="Learn more"
          @action="handleCardAction"
        >
          <p>Use this slot to pass rich content into the card.</p>
        </MyCustomCard>

        <v-card class="pa-8 rounded-xl w-100" style="max-width: 520px;">
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
            <LinkButton
              v-for="link in links"
              :key="link.label"
              :label="link.label"
              :url="link.url"
              :icon="link.icon"
            />
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
