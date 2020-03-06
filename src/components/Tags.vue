<template>
        <div class="tags">
            <Tag @childToParent="onChildClick" />
            <Tag @childToParent="onChildClick" />
        </div>
</template>

<script>

import Tag from './Tag'
export default {
    data() {
        return {
            checkedTags: [],
        }
    },
    name: "Tags",
    components: { Tag },

    methods: {
        onChildClick (value) {
          this.checkedTags = value,
         this.$emit('childToParent', this.checkedTags)

        }
    }
  }


</script>