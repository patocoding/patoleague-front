<template>
  <aside
    :class="[
      'fixed left-0 top-0 z-40 h-screen flex flex-col bg-white dark:bg-gray-900 border-r border-gray-200 dark:border-gray-800 transition-transform duration-200 ease-in-out',
      sidebarWidthClass,
      isOpen ? 'translate-x-0' : '-translate-x-full lg:translate-x-0'
    ]"
    aria-label="Sidebar"
  >
    <!-- Brand -->
    <div class="flex h-16 shrink-0 items-center justify-between gap-2 border-b border-gray-200 dark:border-gray-800 px-4">
      <NuxtLink
        to="/"
        class="flex items-center gap-2 font-semibold text-gray-900 dark:text-white truncate"
      >
        <span class="text-xl">🦆</span>
        <span class="hidden sm:inline">PatoLeague</span>
      </NuxtLink>
      <button
        type="button"
        class="lg:hidden rounded-md p-2 text-gray-500 hover:bg-gray-100 dark:hover:bg-gray-800 dark:text-gray-400 dark:hover:text-white"
        aria-label="Fechar menu"
        @click="toggle"
      >
        <svg class="h-5 w-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>
    </div>

    <!-- Navigation -->
    <nav class="flex-1 overflow-y-auto py-4 px-3" aria-label="Navegação principal">
      <ul class="space-y-1">
        <li v-for="item in navItems" :key="item.to">
          <NuxtLink
            :to="item.to"
            class="flex items-center gap-3 rounded-lg px-3 py-2.5 text-sm font-medium transition-colors"
            :class="isActive(item.to)
              ? 'bg-primary-50 text-primary-700 dark:bg-primary-900/30 dark:text-primary-400'
              : 'text-gray-700 hover:bg-gray-100 dark:text-gray-300 dark:hover:bg-gray-800'"
            @click="onNavClick"
          >
            <span class="text-lg" aria-hidden="true">{{ item.icon }}</span>
            <span>{{ item.label }}</span>
          </NuxtLink>
        </li>
      </ul>
    </nav>

    <!-- Footer (opcional: usuário / logout) -->
    <div class="shrink-0 border-t border-gray-200 dark:border-gray-800 p-3">
      <slot name="footer" />
    </div>
  </aside>

  <!-- Overlay mobile -->
  <div
    v-if="isOpen"
    class="fixed inset-0 z-30 bg-black/50 lg:hidden"
    aria-hidden="true"
    @click="close"
  />
</template>

<script setup lang="ts">
interface NavItem {
  to: string
  label: string
  icon: string
}

const route = useRoute()

const navItems: NavItem[] = [
  { to: '/', label: 'Início', icon: '🏠' },
  // Adicione mais itens conforme as rotas da aplicação
  // { to: '/ligas', label: 'Ligas', icon: '🏆' },
  // { to: '/times', label: 'Times', icon: '👥' },
]

const isOpen = ref(false)

const sidebarWidthClass = computed(() => 'w-64 sm:w-64')

function isActive(path: string) {
  if (path === '/') return route.path === '/'
  return route.path.startsWith(path)
}

function toggle() {
  isOpen.value = !isOpen.value
}

function close() {
  isOpen.value = false
}

function onNavClick() {
  close()
}

defineExpose({
  open: () => { isOpen.value = true },
  close,
  toggle
})
</script>
