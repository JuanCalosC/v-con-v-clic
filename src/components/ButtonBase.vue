<template>
  <button class="{
    'primary':context == 'primary',
    'secundary':context == 'secundary',
  }">{{ text }}</button>
</template>

<script>
export default {
 props: ["text", "context"]
}
</script>

<style lang="sass" scoped>
button
      @apply px-2 text-sm bg-blue-500 text-white rounded-full border min-w-[80px] text-center
      @apply cursor-pointer
      &.primary
        @apply bg-blur-500
      &.secundary
        @apply bg-orange-500
        
</style>