<template>
        <div class="tags">
            <div class="tag">
                <input type="checkbox" id="3" value="trecias" v-model="checked" v-on:change="emitToParent">
                <label for="3">Tag three</label>
            </div>
            <div class="tag">
                <input type="checkbox" id="4" value="ketvirtas" v-model="checked" v-on:change="emitToParent">
                <label for="4">Tag four</label>
            </div>
        </div>
</template>

<script>
export default {
    data() {
        return {
            checked: [],
        }
    },
    name: "Tags",
    methods: {
        emitToParent (event) {
            this.$emit('childToParent', this.checked)
    }
  }
}

</script>