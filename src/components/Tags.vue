<template>
        <div class="tags">
            <Tag @childToParent="onChildClick"
                v-for="data in myJson"
                v-bind:key="data.title"
                v-bind:id="id"
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
        onChildClick (value) {
            if(value.length == 1){
                this.checkedTags.push('1')
            } else {
                this.checkedTags.pop()
            }
        //   this.checkedTags += 1,
         this.$emit('childToParent', this.checkedTags)

        }
    }
  }


</script>