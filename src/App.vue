<template>
  <div id="app">
    <h1>
      {{sum}}
      <br>
      <input type="checkbox" id="1" value="pirmas" v-model="checkedTags">
      <label for="1">5</label>
      <input type="checkbox" id="2" value="antras" v-model="checkedTags">
      <label for="2">5</label>
    </h1>
  </div>
</template>

<script>
export default {
  name: "App",
  data: function() {
    return {
      checkedTags: []
    };
  },
  computed: {
    sum() {
       if (! this.checkedTags.length) {
        return "error"
      } else {
        return this.checkedTags.length
      };
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
