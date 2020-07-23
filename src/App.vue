<template>
  <div id="app">
    <p id="remotemessage"></p>
    <p id="quizmessage"></p>
    <todoList />
  </div>
</template>

<script>
import todoList from './components/todoList.vue'

export default {
  name: 'App',
  components: {
    todoList
  }
}
</script>

<style>
body{
  background: #ccc;
  margin: 0;
  font-family: "Meiryo", "Meiryo UI", "Microsoft JhengHei UI", "Microsoft JhengHei", sans-serif;
}
#remotemessage, #quizmessage{
  width: 60%;
  margin: 0 auto;
}
</style>
