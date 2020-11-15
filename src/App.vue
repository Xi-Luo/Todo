<template>
  <div id="app">
<!--    <img alt="Vue logo" src="./assets/logo.png">-->
<!--    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
    <todo></todo>
  </div>
</template>

<script>
import todo from "@/components/todo";
export default {
  name: 'App',
  components: {
    todo
  }
}
</script>

<style>

</style>
