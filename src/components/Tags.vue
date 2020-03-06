<template>
        <div class="tags">
            <Tag 
                @childToParent="onChildClick"
                v-for="data in myJson"
                v-bind:key="data.id"            
                v-bind:title="data.title"          
             />
        </div>
</template>

<script>

import json from '../tagsdata.json'
import Tag from './Tag'

export default {
    data() {
        return {
            checkedTags: [],
            myJson: json
        }
    },

    name: "Tags",
    components: { Tag },

    methods: {
        // when Tag is clicked add or remove from checkedTags array
        onChildClick (value) {
            if(value.length == 1){
                this.checkedTags.push('1')
            } else {
                this.checkedTags.pop()
            }
         this.$emit('childToParent', this.checkedTags)
        }
    }
  }
</script>

<style scoped>
    .tags {
        text-align: left;
    }
</style>