<template>
  <table>
    <tbody>
      <tr>
        <th>ID</th>
        <th>タスク名</th>
        <th>状態</th>
        <th>-</th>
        <th>-</th>
      </tr>
      <todo :todo="todo" v-for="todo in todos" :key="todo.id" @editTodoHandler="editTodoHandler" @deleteTodo="deleteTodo" />
    </tbody>
  </table>
</template>

<script>
import todo from "@/components/Todo.vue";
export default {
  name: "TodosTable",
  components: {
    todo,
  },
  props: {
    todos: { type: Array, require: true },
  },
  methods: {
    editTodoHandler(targetTodoId) {
      this.$emit("editTodoHandler", targetTodoId);
    },
    deleteTodo(targetTodoId) {
      this.$emit("deleteTodo", targetTodoId);
    },
  },
};
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

table {
  max-width: 800px;
  width: 100%;
  margin: 0 auto;
  border: 1px solid #ccc;
  margin-top: 40px;
}

th {
  width: calc(100% / 5);
  /* border: 1px solid #ccc; */
}
</style>
