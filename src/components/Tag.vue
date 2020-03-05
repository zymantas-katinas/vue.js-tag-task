<template>
    <div v-bind:class="{'is-checked':tag.completed}" >
        <h1>
            <input type="checkbox" v-on:change="markComplete" v-bind:id="tag.title" v-model="checkedNames">
            {{tag.title}}
        </h1>
    </div>
</template>

<script>
export default {
    name: "Tag",
    props: ["tag"],
    methods: {
        markComplete() {
            this.tag.completed = ! this.tag.completed
        }
    },

}

</script>

<style scoped>
    .is-checked {
        color: green;
    }
</style>