<template>
  <div id="app">
    <div class="container">
      <h1>Todoリスト</h1>
      <img alt="Vue logo" src="./assets/logo.png" />
      <addTodo @submitValue="addTodo" />
      <editTodo v-if="isEditing" :targetTodoItem="targetTodoItem" @edit="edit" />
      <todos :todos="todos" @deleteTodo="deleteTodo" @editTodoHandler="editTodoHandler" />
    </div>
  </div>
</template>

<script>
import AddTodo from "@/components/AddTodo.vue";
import editTodo from "@/components/editTodo.vue";
import Todos from "@/components/Todos.vue";

export default {
  name: "App",
  components: {
    Todos,
    AddTodo,
    editTodo,
  },
  data() {
    return {
      todos: [],
      isEditing: false,
      targetTodoItem: null,
    };
  },
  methods: {
    addTodo(inputValue, id) {
      this.todos.push({
        todo: inputValue,
        id,
      });
    },
    deleteTodo(targetTodoId) {
      this.todos = this.todos.filter((todo) => todo.id !== targetTodoId);
      this.isEditing = false;
    },
    editTodoHandler(targetTodoId) {
      this.isEditing = true;
      this.targetTodoItem = this.todos.find((todo) => todo.id === targetTodoId);
    },
    edit(editTodoItemValue, targetTodoItemId) {
      this.todos.forEach((todo) => {
        if (todo.id === targetTodoItemId) {
          todo.todo = editTodoItemValue;
          this.isEditing = false;
        }
      });
    },
  },
};
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

.container {
  max-width: 1000px;
  width: calc(100% - 32px * 2);
  margin: 0 auto;
}
</style>
