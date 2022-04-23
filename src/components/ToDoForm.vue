<template>
  <form class="todo-form" @submit.prevent="addNewTodo">
    <input type="text" class="todo-form-input" v-model="newTodo">
    <button type="submit" class="todo-form-submit">Save</button>
  </form>
</template>

<script>
export default {
  name: "ToDoForm",
  props: {
    addTodo: Function
  },
  data() {
    return {
      newTodo: '',
    }
  },
  methods: {
    addNewTodo() {
      this.addTodo(this.newTodo)
      this.newTodo = ''
    }
  }
}
</script>

<style scoped>
.todo-form {
  display: flex;
  flex-direction: row;
  width: 100%;
}

.todo-form-input {
  display: inline-block;
  width: 100%;
  padding: .5rem 1rem;
}

.todo-form-submit {
  display: inline-block;
  padding: 0 1.5rem;
  text-transform: uppercase;
  letter-spacing: 1px;
}
</style>