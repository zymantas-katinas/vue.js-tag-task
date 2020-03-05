<template>
    <!-- <div> -->
        <!-- <div v-bind:key="tag.id" v-for="tag in tags"> -->
        <div>
           <!-- <Tag v-bind:tag="tag" /> -->
           <input type="checkbox" id="1" value="5" v-model="checkedTags">
           <label for="1">5</label>
            <input type="checkbox" id="2" value="5" v-model="checkedTags">
           <label for="2">5</label>
         

        </div>
    <!-- </div> -->
</template>

<script>

// import Tag from './Tag.vue'

export default {
    name: "TagsList",
    components: {
        // Tag
    },
    data: {
        checkedTags: [],
    },
    computed: {
      sum() {
          return this.checkedTags.reduce(
            function (a, b) {
              return a + b
          }, 0);
      }
    }
    // props: ["tags"],

}
</script>
