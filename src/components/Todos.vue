<template>
  <table>
    <tbody>
      <tr>
        <th>ID</th>
        <th>タスク名</th>
        <th>-</th>
        <th>-</th>
      </tr>
      <tr class="todos" v-for="todo in todos" :key="todo.id">
        <td>{{ todo.id }}</td>
        <td>{{ todo.todo }}</td>
        <td><button @click="deleteTodo(todo.id)">削除</button></td>
        <td><button @click="editTodoHandler(todo.id)">編集</button></td>
      </tr>
    </tbody>
  </table>
</template>

<script>
// import todo from "@/components/Todo.vue";
export default {
  name: "Todos",
  // components: {
  //   todos,
  // },
  // data() {},
  props: {
    todos: { type: Array, require: true },
  },
  methods: {
    deleteTodo(targetTodoId) {
      console.log(targetTodoId);
      this.$emit("deleteTodo", targetTodoId);
    },
    editTodoHandler(targetTodoId) {
      this.$emit("editTodoHandler", targetTodoId);
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
  width: calc(100% / 4);
  /* border: 1px solid #ccc; */
}
</style>
