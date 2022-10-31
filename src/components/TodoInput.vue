<template>
  <div class="inputBox shadow">
    <input type="text" v-model.trim="newTodoItem" placeholder="Type what you have to do" v-on:keyup.enter="addTodo">
    <span class="addContainer" v-on:click="addTodo">
        <i class="addBtn fas fa-plus" aria-hidden="true"></i>
    </span>
    <modal v-if="showModal" @close="showModal=false">
      <h3 slot="header">경고</h3>
      <span slot="footer" @click="showModal=false">
        할 일을 입력하세요.
        <i class="cloaseModalBtn fas fa-times" aria-hidden="true"></i>
      </span>
    </modal>
  </div>
</template>

<script>
  import Modal from "./common/Modal.vue"
  export default {
    data() {
      return {
        newTodoItem : "",
        showModal : false
      }
    },
    components : {
      Modal : Modal
    },
    methods : {
      addTodo() {
        if (this.newTodoItem !== "") {
          this.$emit("addTodo", this.newTodoItem); // addTodo 이벤트를 발생시키면서 value 값을 TodoInput child teg에 전달한다.
          this.clearInput();
          // console.log(this.newTodoItem);
          // localStorage.setItem(this.newTodoItem, this.newTodoItem);
          // this.clearInput();

        } else {
          this.showModal = !this.showModal;
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
