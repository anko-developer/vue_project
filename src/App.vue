<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <TodoList v-bind:propsdata="todoItems" v-on:removeTodo="removeTodo"></TodoList>
    <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
  </div>
</template>

<script>
// 컴포넌트 내용을 불러오기 위한 ES6 import 구문 / ES6 방식: import로 vue 파일을 가져온다.
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

// ES5의 방식을 쓴다면 아래처럼 가능 / ES5 방식: var에 직접 담는다.
// var TodoHeader = {
//   template: '<div>header</div>'
// }

export default {
  data() {
    return {
      todoItems: []
    }
  },
  created() {
      if (localStorage.length > 0) {
          for(var i = 0; i <  localStorage.length; i++) {
              this.todoItems.push(localStorage.key(i));
          }
      }
  },
  methods: {
    addTodo(todoItem) { // TodoInput.vue에서 argument 값으로 value 값을 받아옴
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    removeTodo(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);            
    },
    clearAll() {
      localStorage.clear();
      this.todoItems = [];
    }
  },
  components: {
    'TodoHeader': TodoHeader,
    'TodoInput': TodoInput,
    'TodoList': TodoList,
    'TodoFooter': TodoFooter
  },
}
</script>

<style lang="scss">
  body {margin:0;background-color:#f6f6f8}
  input {width:200px;border-style:groove}
  button {border-style:groove}
  #app {padding:0 10px}
  .shadow {box-shadow:5px 10px 10px rgba(0,0,0,0.03)}
</style>