<template>
  <div id="app">
      <TagsList />
  </div>
</template>

<script>
import TagsList from './components/TagsList'
export default {
  name: "App",
  components: { TagsList},
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
