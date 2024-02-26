<template>
  <ToDoHeader></ToDoHeader>
  <ToDoInput></ToDoInput>
  <ToDoList v-bind:propsdata="todoItems"></ToDoList> <!--v-bind:내려보낼 props 속성 이름="현재 위치의 컴포넌트 데이터 속성"-->
  <ToDoFooter></ToDoFooter>
</template>

<script>
import ToDoHeader from './components/ToDoHeader.vue';
import ToDoInput from './components/ToDoInput.vue';
import ToDoList from './components/ToDoList.vue';
import ToDoFooter from './components/ToDoFooter.vue';


export default {
  data: function(){
    return {
      todoItems: [],
    }
  },  

  components: {
    'ToDoHeader': ToDoHeader,
    'ToDoInput': ToDoInput,
    'ToDoList': ToDoList,
    'ToDoFooter': ToDoFooter
  },

  created: function() {
    if (localStorage.length > 0) {
      for (var i = 0; i<localStorage.length; i++){
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
