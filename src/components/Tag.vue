<template>     
    <div>
        <div class="tag">

            <input 
                type="checkbox"
                v-bind:key="id" 
                v-bind:value="title"
                v-model="checkedTag" 
                v-on:change="emitToParent"
            >
            <label v-bind:for="id">
                {{title}}
            </label>

        </div>
        <hr>
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

<style scoped>
    .tag {
        height: auto;
    }
    label {
        margin: 0 5px;
        padding: 0;
    }
    input {
        margin: 0;
        padding: 0;
    }
    hr {
        margin: 5px 0;
        padding: 0;
    }
</style>