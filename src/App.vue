<script setup lang="ts">
import { RouterView } from 'vue-router'
import { useTheme } from 'vuetify'

const theme = useTheme()

const toggleTheme = () => {
  theme.global.name.value = theme.global.name.value === 'dark' ? 'light' : 'dark'
}

const themeIcon = () => {
  return theme.global.name.value === 'dark' ? 'mdi-white-balance-sunny' : 'mdi-moon-waning-crescent'
}
</script>

<template>
  <v-app>
    <v-app-bar color="primary" dark flat>
      <v-spacer />
      <v-btn icon @click="toggleTheme" :title="`Toggle ${theme.global.name.value === 'dark' ? 'light' : 'dark'} mode`">
        <v-icon>{{ themeIcon() }}</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main class="d-flex align-center justify-center">
      <RouterView />
    </v-main>
  </v-app>
</template>

<style scoped>
:deep(main) {
  height: 100%;
}
</style>
