<template>
  <!--Componentización v-model, v-if, two binding un conjunto modelo de datos todos-->
  <div class="todo_list" v-if="todos.length > 0">

    <div class="todo_item" v-for="(todo, i) in todos" :key="i">
      <div class="todo_title">
        <h3 :contenteditable="todo.editing">{{ todo.title }}</h3>
      </div>
      <div class="todo_actions">
        <span class="remove" @click="removeTodo">remove</span>
        <span class="edit" @click="editTodo">edit</span>
      </div>
    </div>
  </div>

  <div class="todo_emtp_list" v-else>No hay to-dos todavia :</div>

  <div class="todo_form">
    <form @submit.prevent="addTodo">
      <input type="text" placeholder="Mete un nuevo todo" v-model="newTodoForm.text">
      <button type="submit">Enviar</button>
    </form>
  </div>
</template>

<script>
export default {
  // config del component modelo de datos
  data() {
    return {
      todos: [
        {
          title: "prueba",
          editing: false
        },
        {
          title: "adiós",
          editing: false
        },
        {
          title: "23123",
          editing: false
        },
        {
          title: "asdasd",
          editing: false
        },
      ],
      newTodoForm: {
        text: ""

      }
    }

  },

  methods: {
    addTodo() {
      this.todos.push({
        title: this.newTodoForm.text,
        editing: false
      })
      this.newTodoForm.text=""
    },
    removeTodo(i) {
      this.todos.splice(i, 1)
    },
    editTodo(i) {
      this.todos[i].editing= true
    }
  },
}

</script>

<style lang="sass" scoped>
.todo_list
  @apply mx-outo max-w-3xl w-11/12 divide-y divide-blue-500
  .todo_item
    @apply flex justify-between items-center py-2
    .todo_title h3 
      @apply font-bold
    .todo_actions
      @apply flex gap-2
      .remove
      @apply px-2 py-1 text-sm border-pink-500 rounded-r-full border min-w-[80px] text-center
      @apply cursor-pointer 
      .edit
      @apply px-2 py-1 text-sm border-bue-500 rounded-r-full border min-w-[80px] text-center
      @apply cursor-pointer 
.todo_empty_list
  @apply mx-auto max-w-3xl w-11/12
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
