<template>     
    <div>
        <div class="tag">

            <input type="checkbox"
                v-bind:id="id" 
                v-bind:value="title"
                v-model="checkedTag" 
                v-on:change="emitToParent">

            <label v-bind:for="id">
                {{title}}
            </label>

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
    props: {
        id: String,
        title: String,
    },
    methods: {
        // emit to Tags component checkedTag array
        emitToParent () {
            this.$emit('childToParent', this.checkedTag)
    }
  }
}

</script>