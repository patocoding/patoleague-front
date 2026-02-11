<template>
  <ContentWrapper
    size="xs"
    :padding="false"
    padding-class="px-4"
    container-class="flex items-center justify-center min-h-screen bg-gray-50 dark:bg-gray-900"
  >
    <div class="w-full max-w-sm mx-auto space-y-8">
      <div>
        <h2 class="mt-6 text-center text-3xl font-extrabold text-gray-600">
          Faça login em sua conta PatoLeague
        </h2>
        <p class="mt-2 text-center text-sm text-gray-600 dark:text-gray-400">
          Ou
          <a href="#" class="font-medium text-primary-600 hover:text-primary-500">
            crie uma nova conta
          </a>
        </p>
      </div>
      <form class="mt-8 space-y-6" @submit.prevent="onLogin">
        <div class="rounded-md shadow-sm -space-y-px">
          <div>
            <label for="email" class="sr-only">Email</label>
            <input
              id="email"
              v-model="form.email"
              name="email"
              type="email"
              autocomplete="email"
              required
              class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-t-md focus:outline-none focus:ring-primary-500 focus:border-primary-500 focus:z-10 sm:text-sm dark:bg-gray-800 dark:border-gray-600 dark:text-white dark:placeholder-gray-400"
              placeholder="Endereço de email"
            />
          </div>
          <div>
            <label for="password" class="sr-only">Senha</label>
            <input
              id="password"
              v-model="form.password"
              name="password"
              type="password"
              autocomplete="current-password"
              required
              class="appearance-none rounded-none relative block w-full px-3 py-2 border border-gray-300 placeholder-gray-500 text-gray-900 rounded-b-md focus:outline-none focus:ring-primary-500 focus:border-primary-500 focus:z-10 sm:text-sm dark:bg-gray-800 dark:border-gray-600 dark:text-white dark:placeholder-gray-400"
              placeholder="Senha"
            />
          </div>
        </div>

        <div class="flex items-center justify-between">
          <div class="flex items-center">
            <input
              id="remember-me"
              v-model="form.rememberMe"
              name="remember-me"
              type="checkbox"
              class="h-4 w-4 text-primary-600 focus:ring-primary-500 border-gray-300 rounded"
            >
            <label for="remember-me" class="ml-2 block text-sm text-gray-900 dark:text-gray-300">
              Lembrar-me
            </label>
          </div>

          <div class="text-sm">
            <a href="#" class="font-medium text-primary-600 hover:text-primary-500">
              Esqueceu sua senha?
            </a>
          </div>
        </div>

        <div>
          <button
            type="submit"
            :disabled="isLoading"
            class="group relative w-full flex justify-center py-2 px-4 border border-transparent text-sm font-medium rounded-md text-white bg-primary-600 hover:bg-primary-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-primary-500 disabled:opacity-50 disabled:cursor-not-allowed"
          >
            <span v-if="!isLoading">Entrar</span>
            <span v-else>Carregando...</span>
          </button>
        </div>
      </form>
    </div>
  </ContentWrapper>
</template>

<script setup lang="ts">
definePageMeta({
  layout: false
})

const form = ref({
  email: '',
  password: '',
  rememberMe: false
})

const isLoading = ref(false)

const onLogin = async () => {
  isLoading.value = true
  
  try {
    // TODO: Implementar lógica de autenticação
    console.log('Login attempt:', form.value)
    
    // Simulação de delay
    await new Promise(resolve => setTimeout(resolve, 1000))
    
    // Redirecionar após login bem-sucedido
    // await navigateTo('/dashboard')
  } catch (error) {
    console.error('Erro no login:', error)
  } finally {
    isLoading.value = false
  }
}
</script>
