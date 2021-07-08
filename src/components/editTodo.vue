<template>
  <div class="edit">
    <p>タスク編集フォーム</p>
    <p>ID：{{ targetTodoItem.id }}のタスクを編集中</p>
    <input type="text" v-model="editTodoValue" />
    <button @click="edit">確定</button>
  </div>
</template>

<script>
export default {
  props: {
    targetTodoItem: { reqiure: true },
  },
  data() {
    return {
      editTodoValue: "",
    };
  },
  methods: {
    edit() {
      if (this.editTodoValue === "") {
        alert("値を入力してください");
        return;
      }
      this.$emit("edit", this.editTodoValue, this.targetTodoItem.id);
    },
  },
};
</script>

<style></style>
