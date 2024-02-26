<template>
  <ToDoHeader></ToDoHeader>
  <ToDoInput></ToDoInput>
  <ToDoList></ToDoList>
  <ToDoFooter></ToDoFooter>
</template>

<script>
import ToDoHeader from './components/ToDoHeader.vue';
import ToDoInput from './components/ToDoInput.vue';
import ToDoList from './components/ToDoList.vue';
import ToDoFooter from './components/ToDoFooter.vue';


export default {
  components: {
    'ToDoHeader': ToDoHeader,
    'ToDoInput': ToDoInput,
    'ToDoList': ToDoList,
    'ToDoFooter': ToDoFooter
  },
}
</script>

<style>
</style>
