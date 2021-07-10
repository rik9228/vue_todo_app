<template>
  <div class="sortButtons">
    <div class="sortButtons__box">
      <label for="all">全て</label>
      <input type="radio" name="sort" value="all" id="all" checked @change="changeTodoStatus" />
    </div>
    <div class="sortButtons__box">
      <label for="working">作業中</label>
      <input type="radio" name="sort" value="working" id="working" @change="changeTodoStatus" />
    </div>
    <div class="sortButtons__box">
      <label for="completed">完了済み</label>
      <input type="radio" name="sort" value="completed" id="completed" @change="changeTodoStatus" />
    </div>
  </div>
</template>

<script>
export default {
  name: "sortTodo",
  methods: {
    changeTodoStatus(e) {
      this.$emit("changeTodoStatus", e.target.value);
    },
  },
};
</script>

<style>
.sortButtons {
  display: flex;
  justify-content: center;
  margin-top: 32px;
}
.sortButtons__box:not(:first-of-type) {
  margin-left: 16px;
}
</style>
