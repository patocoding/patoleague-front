<template>
  <div class="min-h-screen bg-gray-50 dark:bg-gray-900">
    <AppSidebar ref="sidebarRef" />

    <!-- Main content -->
    <div class="lg:pl-64">
      <!-- Header mobile: botão para abrir sidebar -->
      <header class="sticky top-0 z-20 flex h-16 shrink-0 items-center gap-2 border-b border-gray-200 bg-white px-4 dark:border-gray-800 dark:bg-gray-900 lg:hidden">
        <button
          type="button"
          class="rounded-md p-2 text-gray-500 hover:bg-gray-100 dark:hover:bg-gray-800 dark:text-gray-400 dark:hover:text-white"
          aria-label="Abrir menu"
          @click="openSidebar"
        >
          <svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
          </svg>
        </button>
        <span class="font-semibold text-gray-900 dark:text-white">PatoLeague</span>
      </header>

      <main class="min-h-[calc(100vh-4rem)] lg:min-h-screen">
        <slot />
      </main>
    </div>
  </div>
</template>

<script setup lang="ts">
import AppSidebar from '../components/AppSidebar.vue'
const sidebarRef = ref<{ open: () => void } | null>(null)

function openSidebar() {
  sidebarRef.value?.open()
}
</script>
