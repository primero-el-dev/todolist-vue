<template>
  <div class="todo-container">
    <ToDoForm :addTodo="addTodo" />
    <ToDoList :todos="todos" :deleteTodo="deleteTodo" />
  </div>
</template>

<script>
import ToDoForm from './components/ToDoForm.vue'
import ToDoList from './components/ToDoList.vue'

export default {
  name: 'App',
  components: {
    ToDoForm,
    ToDoList
  },
  data() {
    return {
      nextId: 3,
      todos: JSON.parse(sessionStorage.getItem('todos') || '{}'),
      addTodo: (text) => {
        this.todos.push({ id: this.nextId++, text: text, done: false })
        this.storeTodos()
      },
      deleteTodo: (todo) => {
        this.todos = this.todos.filter(t => t.id !== todo.id)
        this.storeTodos()
      },
      storeTodos: () => {
        sessionStorage.setItem('todos', JSON.stringify(this.todos))
        console.log(sessionStorage)
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.todo-container {
  display: block;
  padding: 1rem 2rem;
}
</style>
