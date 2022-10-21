<template>
  <div>
    <input type="text" v-model.trim="newTodoItem">
    <button v-on:click="addTodo">추가</button>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        newTodoItem : ""
      }
    },
    methods : {
      addTodo() {
        if (this.newTodoItem !== "") {
          console.log(this.newTodoItem);
          localStorage.setItem(this.newTodoItem, this.newTodoItem);
          this.clearInput();
        }
      },
      clearInput() {
        this.newTodoItem = "";
      }
    }
  }
</script>

<style>
</style>
