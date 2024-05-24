<template>
  <button class="{
    'primary':context == 'primary',
    'secundary':context == 'secundary',
    'lg': size == 'lg'
  }">{{ text }}</button>
</template>

<script>
export default {
 props: ["text", "context", "size", "onClick"]
}
</script>

<style lang="sass" scoped>
button
      @apply px-2 py-1 text-sm bg-blue-500 text-white rounded-full border min-w-[80px] text-center
      @apply cursor-pointer
      &.primary
        @apply bg-blue-500
      &.secundary
        @apply bg-orange-500
      &.lg
        @pply px-2 py-1
        
</style>