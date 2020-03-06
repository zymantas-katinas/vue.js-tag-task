<template>     
    <div>
      <div class="tag">
                <input type="checkbox" id="3" value="trecias" v-model="checkedTag"  v-on:change="emitToParent">
                <label for="3">Tag three</label>
            </div>
            <div class="tag">
                <input type="checkbox" id="4" value="ketvirtas" v-model="checkedTag" v-on:change="emitToParent">
                <label for="4">Tag four</label>
            </div>
            <div class="tag">
                <input type="checkbox" id="5" value="penktas" v-model="checkedTag" v-on:change="emitToParent">
                <label for="5">Tag five</label>
            </div>
        </div>

</template>

<script>
export default {
    data() {
        return {
            checkedTag: [],
        }
    },
    name: "Tag",
    methods: {
        // onChildClick (value) {
        //   this.checkedTag = value
        // },
        emitToParent () {
            this.$emit('childToParent', this.checkedTag)
    }
  }
}

</script>