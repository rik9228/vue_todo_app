<template>
  <tr>
    <td :class="{ isActive: this.todo.status }">{{ todo.id }}</td>
    <td :class="{ isActive: this.todo.status }">{{ todo.name }}</td>
    <td>
      <button @click="changeState(todo.status)">{{ completedText }}</button>
    </td>
    <td><button @click="deleteTodo(todo.id)">削除</button></td>
    <td><button @click="editTodoHandler(todo.id)">編集</button></td>
  </tr>
</template>

<script>
export default {
  name: "Todo",
  props: {
    todo: { require: true },
  },
  methods: {
    deleteTodo(targetTodoId) {
      this.$emit("deleteTodo", targetTodoId);
    },
    editTodoHandler(targetTodoId) {
      this.$emit("editTodoHandler", targetTodoId);
    },
    changeState() {
      this.todo.status = !this.todo.status;
    },
  },
  computed: {
    completedText() {
      return this.todo.status ? "完了" : "作業中";
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
  padding: 1em;
}

th,
td {
  width: calc(100% / 5);
  /* border: 1px solid #ccc; */
}

.isActive {
  text-decoration: line-through;
}
</style>
