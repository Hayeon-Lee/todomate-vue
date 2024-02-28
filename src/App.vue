<template>
  <ToDoHeader></ToDoHeader>
  <ToDoInput v-on:addTodoItem="addOneItem"></ToDoInput> <!--v-on: 하위 컴포넌트에서 발생시킨 이벤트 이름="현재 컴포넌트의 메서드 명"-->
  <!--v-bind:내려보낼 props 속성 이름="현재 위치의 컴포넌트 데이터 속성"-->
  <ToDoList v-bind:propsdata="todoItems" 
            v-on:removeItem="removeOneItem"
            v-on:toggleItem="toggleOneItem">
  </ToDoList> 
  <ToDoFooter v-on:clearTodo="clearAllItems"></ToDoFooter>
</template>

<script>
import ToDoHeader from './components/ToDoHeader.vue';
import ToDoInput from './components/ToDoInput.vue';
import ToDoList from './components/ToDoList.vue';
import ToDoFooter from './components/ToDoFooter.vue';


export default {
  data(){
    return {
      todoItems: [],
      showModal: false,
    }
  },  

  methods: {
    addOneItem (todoItem) {
      const obj = {completed: false, item: todoItem};
      localStorage.setItem(todoItem, JSON.stringify(obj));
      this.todoItems.push(obj);
    },
    removeOneItem (todoItem, index) {
      localStorage.removeItem(todoItem.item);
      this.todoItems.splice(index, 1);
    },
    toggleOneItem (todoItem, index) {
      this.todoItems[index].completed = !this.todoItems[index].completed;
      localStorage.removeItem(todoItem.item);
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
    },
    clearAllItems () {
      localStorage.clear();
      this.todoItems = [];
    }
  },
  clearInput: function() {
    this.newTodoItem = '';
  },

  components: {
    'ToDoHeader': ToDoHeader,
    'ToDoInput': ToDoInput,
    'ToDoList': ToDoList,
    'ToDoFooter': ToDoFooter
  },

  created() {
    if (localStorage.length > 0) {
      for (let i = 0; i<localStorage.length; i++){
        if(localStorage.key(i) !== 'loglevel:webpack-dev-server') {
          this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
        }
      }
    }
  }
}
</script>

<style>
*{
  font-family: "IBM Plex Sans KR", sans-serif;
}

body {
  text-align: center;
  background-color: #F6F6F6;
}

input {
  border-style: groove;
  width: 200px;
}

button {
  border-style: groove;
}

.shadow {
  box-shadow: 5px 10px 10px rgb(0, 0, 0, 0.03);
}
</style>
