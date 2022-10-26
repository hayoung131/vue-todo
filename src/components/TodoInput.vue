<template>
  <div class="inputBox shadow">
    <input type="text" v-model.trim="newTodoItem" placeholder="Type what you have to do" v-on:keyup.enter="addTodo">
    <span class="addContainer" v-on:click="addTodo">
        <i class="addBtn fas fa-plus" aria-hidden="true"></i>
    </span>
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
          this.$emit("addTodo", this.newTodoItem); // addTodo 이벤트를 발생시키면서 value 값을 TodoInput child teg에 전달한다.
          this.clearInput();
          // 등록 및 삭제시 바로 반영되지 않음.
          // console.log(this.newTodoItem);
          // localStorage.setItem(this.newTodoItem, this.newTodoItem);
          // this.clearInput();

        }
      },
      clearInput() {
        this.newTodoItem = "";
      }
    }
  }
</script>

<style scoped>
  input:focus {
    outline : none;
  }

  .inputBox {
    background : white;
    height : 50px;
    line-height : 50px;
    border-radius : 5px;
  }

  .inputBox input {
    border-style : none;
    font-size : 0.9rem;
  }

  .addContainer {
    float :right;
    background : linear-gradient(to right, #6478FB, #8763FB);
    display : block;
    width : 3rem;
    border-radius : 0 5px 5px 0;
  }

  .addBtn {
    color : white;
    vertical-align : middle;
  }
</style>
