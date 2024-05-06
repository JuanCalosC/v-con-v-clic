<template>
  <!--Componentización v-model, v-if, two binding un conjunto modelo de datos todos-->
 <todo-list 
   v-if="todos.length > 0" 
  :todo-list-content="todos" 
  :editHandler="editTodo" 
  :removeHandler="removeTodo"/>

 <todo-emtp-list  v-else/>

 <todo-form v-bind="o"
 :form-content="newTodoForm" 
 :submit-handler="addTodo"/>

  
</template>

<script>
import TodoForm from './components/TodoForm.vue'
import TodoList from './components/TodoList.vue'
import Todo_emtp_list from './components/todo_emtp_list.vue'

export default {
  components: {
     TodoList,
     Todo_emtp_list, 
     TodoForm 
    },
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
      this.newTodoForm.text = ""
    },
    removeTodo(i) {
      this.todos.splice(i, 1)
    },
    editTodo(i) {
      this.todos[i].editing = true
    }
  },
  mounted() {
    window.addEventListener("click", (ev) => {
      this.todos.forEach(todo => { todo.editing = false })
    })
  }
}

</script>

<!-- <style lang="sass" scoped>
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
</style> -->
