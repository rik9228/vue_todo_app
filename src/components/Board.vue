<template>
  <div class="">
    <addTodo @submitValue="addTodo" />
    <sortTodo @changeTodoStatus="changeTodoStatus" />
    <editTodo v-if="isEditing" :targetTodoItem="targetTodoItem" @edit="edit" />
    <todosTable :todos="filterdTodos" @editTodoHandler="editTodoHandler" @deleteTodo="deleteTodo" />
  </div>
</template>

<script>
import AddTodo from "@/components/AddTodo.vue";
import editTodo from "@/components/editTodo.vue";
import TodosTable from "@/components/TodosTable.vue";
import sortTodo from "@/components/sortTodo.vue";

export default {
  name: "App",
  components: {
    TodosTable,
    AddTodo,
    editTodo,
    sortTodo,
  },
  data() {
    return {
      todos: [],
      isEditing: false,
      currentTodoStatus: "all",
    };
  },
  methods: {
    addTodo(inputValue, id) {
      this.todos.push({
        name: inputValue,
        id,
        status: false,
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
          todo.name = editTodoItemValue;
          this.isEditing = false;
        }
      });
    },
    changeTodoStatus(inputValue) {
      this.isEditing = false;
      this.currentTodoStatus = inputValue;
    },
  },
  computed: {
    filterdTodos() {
      if (this.currentTodoStatus === "working") {
        return this.todos.filter((todo) => todo.status === false);
      } else if (this.currentTodoStatus === "completed") {
        return this.todos.filter((todo) => todo.status !== false);
      } else {
        return this.todos.filter((todo) => todo.status !== false || todo.status === false);
      }
    },
  },
};
</script>

<style></style>
