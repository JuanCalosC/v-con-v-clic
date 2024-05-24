<template>
    <div class="todo_form">
    <form @submit.prevent="submitHandler">
        <input type="text" placeholder="Mete un nuevo todo" v-model="formContent.text">
        <button-base />
    </form>
</div>
</template>

<script>
import ButtonBase from './ButtonBase.vue'
export default {
  components: { ButtonBase },
    props: ["formContent", "submitHandler"]
}
</script>

<style lang="sass" scoped>
.todo_form
    @apply mx-outo max-w-3xl w-11/12 py-2
    from
      @apply flex gap-2
      input
        @apply w-full border p-2
    
</style>