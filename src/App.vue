<template>
  <div id="app">
    <button @click="createNewTodo">Add Todo</button>
  </div>
</template>

<script>
import API, {  graphqlOperation } from '@aws-amplify/api'
import { createTodo } from "./graphql/mutations"

export default {
  name: 'app',
  methods :{
    async createNewTodo() {
      const todo = { name: "Todo Title" , description: "あれをやる" + Date()}
      await API.graphql(graphqlOperation(createTodo, { input: todo }))
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
