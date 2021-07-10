<template>
  <div id="app">
    <div class="container">
      <h1>Todoリスト</h1>
      <img alt="Vue logo" src="./assets/logo.png" />
      <board />
    </div>
  </div>
</template>

<script>
import Board from "@/components/Board.vue";

export default {
  name: "App",
  components: {
    Board,
  }
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
