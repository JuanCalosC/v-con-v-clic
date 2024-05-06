<template>
    <div class="relative overflow-x-auto shadow-md sm:rounded-lg">
        <table class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400 todo_form">
            <tbody>
                <thead class="text-xs text-gray-700 uppercase bg-gray-50 ">
                    <tr class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                        <th scope="col" class="px-6 py-3">
                            Product name
                            <div class="flex flex-col items-center gap-2 todo_list">
                                <TodoItem v-for="(todo, i) in todoListContent" 
                                :key="i" 
                                :todo="todo" 
                                :editHandler="editHandler" 
                                :removeHandler="removeHandler"/>
                            </div>
                        </th>
                    </tr>
                </thead>
            </tbody>
        </table>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue';
export default {
   components: { TodoItem },
props: ["todoListContent", "removeHandler", "editHandler"]
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
    </style>