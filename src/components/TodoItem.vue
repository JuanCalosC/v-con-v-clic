<template>
    <div class="w-full flex flex-row justify-between border-b-2 todo_item">

        <div class="todo_title">
            <h3 :contenteditable="todo.editing">{{ todo.title }}</h3>
        </div>
        <div class="flex gap-2 todo_actions">
            <span class="text-red-800" @click="removeHandler(i)">remove</span>
            <span class="text-green-500" @click="editHandler(i)">edit</span>
        </div>
    </div>
</template>

<script>
export default {
    props: ["todo", "removeHandler", "editHandler"]
}
</script>

<style></style>