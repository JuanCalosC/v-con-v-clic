<template>
    <div class="todo_form">
    <form @submit.prevent="submitHandler">
        <input type="text" placeholder="Mete un nuevo todo" v-model="formContent.text">
        <button type="submit"
            class="text-white bg-gradient-to-r from-blue-500 via-blue-600 to-blue-700 hover:bg-gradient-to-br focus:ring-4 focus:outline-none focus:ring-blue-300 dark:focus:ring-blue-800 font-medium rounded-lg text-sm px-1 py-1 text-center me-1 mb-1">
            Enviar</button>
    </form>
</div>
</template>

<script>
export default {
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
    button
      @apply px-2 text-sm bg-blue-500 text-white rounded-full border min-w-[80px] text-center
      @apply cursor-pointer
</style>