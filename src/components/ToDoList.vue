<template>
  <div>
    <ul>
      <li v-for="todoItem in toDoItems" v-bind:key="todoItem">{{todoItem}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      toDoItems: []
    }
  },

  created: function() {
    if (localStorage.length > 0) {
      for (var i = 0; i< localStorage.length; i++) {
        if (localStorage.key(i) !== 'loglevel:webpack-dev-server') {
          this.toDoItems.push(localStorage.key(i));
        }
      }
    }
  } //앱이 생성되자마자 실행되는 hook
}
</script>

<style>

</style>