<template>
  <li class="list-item" :class="resolveClass(todo)">
    <input type="checkbox" class="list-item-checkbox" @input="toggleDone(todo)">
    <span class="list-item-text">{{ todo.text }}</span>
    <span class="list-item-close" @click="deleteTodo(todo)">X</span>
  </li>
</template>

<script>
export default {
  name: "ToDoItem",
  props: {
    todo: Object,
    deleteTodo: Function
  },
  methods: {
    toggleDone: (todo) => {
      todo.done = !todo.done
    },
    resolveClass: (todo) => todo.done ? 'list-item-done' : 'list-item-undone'
  }
}
</script>

<style scoped>
.list-item {
  display: block;
  list-style: none;
  border: 1px solid black;
  margin: 1rem 0;
  padding: .5rem;
}

.list-item-done {
  border: 1px solid red !important;
  background-color: rgb(255,0,0,.15);
}

.list-item-undone {
  border: 1px solid blue !important;
  background-color: rgb(0,0,255,.1);
}

.list-item-checkbox {
  float: left;
  transform: scale(1.5);
}

.list-item-text {
  display: inline-block;
  margin: auto;
}

.list-item-close {
  cursor: pointer;
  float: right;
}
</style>