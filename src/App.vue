<template>
  
    <!--Componentización v-model, v-if, two binding un conjunto modelo de datos todos-->
    <dummy-component>
      hola te quedan {{ todos.length }} cosas por hacer..
    </dummy-component>

    <todo-list v-if="todos.length > 0">
      

      <todo-item v-for="(todo, i) in todos" 
          :key="i" 
          :todo="todo" 
          :editHandler="editTodo"
          :removeHandler="removeTodo" />

    </todo-list>

    <todo-empty-list v-else />

   <todo-form 
    :form-content="newTodoForm" 
    :submit-handler="addTodo" />

   <button-base  text="counter" :context="primery" :size="lg" :onClick="sayHello" class="text-white bg-gray-700 hover:bg-gray-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2 dark:bg-gray-600 dark:hover:bg-gray-700 focus:outline-none dark:focus:ring-gray-800"/>
   <button-base  text="conuterBy2" :context="primery" :size="lg" :onClick="sayHello" class="text-white bg-gray-700 hover:bg-gray-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2 dark:bg-gray-600 dark:hover:bg-gray-700 focus:outline-none dark:focus:ring-gray-800"/>
  
   <button-base  text="Enviar" :context="secundary" :size="lg" :onClick="sayGoobye" />
   <button-base  text="menssageToUpper" />
   
 
</template>

<script>
import TodoForm from './components/TodoForm.vue'
import TodoList from './components/TodoList.vue'
import TodoEmptyList from './components/TodoEmptyList.vue'
import DummyComponent from './components/DummyComponent.vue'
import './components/TodoItem.vue'
import TodoItem from './components/TodoItem.vue'
import ButtonBase from './components/ButtonBase.vue'


export default {
  name: "App",
  // components: registrar otros componentes
  components: {
    TodoList,
    TodoEmptyList,
    TodoForm,
    DummyComponent,
    TodoItem,
    ButtonBase
    
  },

  // props: pasar contenidos a funciones a componentes hijos

  // data: variables reactivas

  data() {
    return {
      counter: 0,
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

// methods: guardamos funciones

  methods: {
    addTodo(ev) {
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
    },
      sayHello() {
        console.log("helo...")
      },
      sayGoodbye() {
        console.log("adios...")
  }
},
computed:{
  conuterBy2(){
    return this.counter * 2
  },
  menssageToUpper(){
    return this.menssage.ToUpperCase()
  }
}
}
  
 

</script>

<!-- <style lang="scss" scoped>
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
