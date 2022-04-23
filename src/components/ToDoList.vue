<template>
  <ul class="todo-list">
    <ToDoItem v-for="todo in todos" :todo="todo" :deleteTodo="deleteTodo" :key="todo.id"/>
  </ul>
</template>

<script>
import ToDoItem from './ToDoItem.vue'

export default {
  name: "ToDoList",
  components: {
    ToDoItem
  },
  props: {
    todos: Array,
    deleteTodo: Function
  }
}
</script>

<style scoped>
.todo-list {
  width: 100%;
  padding: 0;
}
</style>