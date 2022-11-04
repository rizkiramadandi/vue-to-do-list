<script>
    import ToDoList from "./components/ToDoList.vue"

    export default {
        components: {
            ToDoList,
        }
    }
</script>

<template>
  <div class="layout">
    <ToDoList/>
  </div>
</template>

<style>
  .layout {
    display: flex;
    width: 100%;
    height: 100%;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
</style>