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
  <a id="github" href="https://github.com/rizkiramadandi/vue-to-do-list" rel="noreferrer noopener">
    <span>Github</span>
    <img src="/src/assets/github.svg" alt="Github">
  </a>
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