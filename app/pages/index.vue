<template>
  <ContentWrapper>
    <div class="text-center">
      <h1 class="text-4xl font-bold text-gray-900 dark:text-white mb-4">
        Bem-vindo ao PatoLeague
      </h1>
      <p class="text-gray-600 dark:text-gray-400 mb-8">
        Sistema de gerenciamento de ligas
      </p>
      <NuxtLink
        to="/login"
        class="inline-block px-6 py-3 bg-primary-600 text-white rounded-md hover:bg-primary-700 transition-colors"
      >
        Fazer Login
      </NuxtLink>
    </div>
  </ContentWrapper>
</template>

<script setup lang="ts">
</script>
