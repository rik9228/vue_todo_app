<template>
  <div class="addTodo">
    <input type="text" placeholder="タスクを追加" v-model="inputValue" />
    <button @click="add">確定する</button>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      inputValue: "",
      id: 0,
    };
  },
  methods: {
    add() {
      if (this.inputValue === "") {
        alert("値を入力してください");
        return;
      }
      this.id++;
      this.$emit("submitValue", this.inputValue, this.id);
      this.inputValue = "";
    },
  },
};
</script>

<style></style>
