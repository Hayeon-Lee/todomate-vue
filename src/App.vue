<script setup>
import ToDoItem from "./components/ToDoItem.vue";
</script>

<template>
  <div id="app">
    <h1>To-Do List</h1>
    <form @submit.prevent="Submit">
      <to-do-item></to-do-item>
      <button>할 일 추가</button>
    </form>

  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
