<template>
  <div
    :class="[
      'min-h-screen bg-gray-50 dark:bg-gray-900 transition-colors',
      containerClass
    ]"
  >
    <div
      :class="[
        'mx-auto',
        {
          'max-w-7xl': size === 'full',
          'max-w-6xl': size === 'large',
          'max-w-4xl': size === 'medium',
          'max-w-2xl': size === 'small',
          'max-w-md': size === 'xs'
        },
        paddingClass
      ]"
    >
      <slot />
    </div>
  </div>
</template>

<script setup lang="ts">
interface Props {
  /**
   * Tamanho do container
   * @default 'full'
   */
  size?: 'xs' | 'small' | 'medium' | 'large' | 'full'
  
  /**
   * Padding vertical do conteúdo
   * @default true
   */
  padding?: boolean
  
  /**
   * Padding customizado (sobrescreve o padrão)
   */
  paddingClass?: string
  
  /**
   * Classes customizadas para o container externo
   */
  containerClass?: string
}

const props = withDefaults(defineProps<Props>(), {
  size: 'full',
  padding: true
})

const paddingClass = computed(() => {
  if (props.paddingClass) {
    return props.paddingClass
  }
  
  if (!props.padding) {
    return ''
  }
  
  return 'py-8 px-4 sm:px-6 lg:px-8'
})
</script>
