<template>
  <div>
    <div class="alert alert-danger" v-bind:class="{active: showAlert}" role="alert">At least one tag must be selected!</div>
    <button v-on:click="myFilter"> {{sum.button}} </button>
    <div  v-bind:class="{active: showTags}">
        <div>
            <input type="checkbox" id="1" value="pirmas" v-model="checkedTags">
            <label for="1">Tag one</label>
        </div>
        <div>
            <input type="checkbox" id="2" value="antras" v-model="checkedTags">
            <label for="2">Tag two</label>
        </div>
    </div>

  </div>
</template>

<script>

export default {
  name: "TagsList",

  data: function() {
    return {
      checkedTags: [],
      showTags: true,
      showAlert: false
    }
    },

    methods: {
        myFilter: function() {
         this.showTags = !this.showTags;   
          if(this.checkedTags.length > 0) {
                this.showAlert = true
            }   
        },
        // alert: function(){
           
        // }
  },

  computed: {
    sum() {
       if (! this.checkedTags.length) {
        return {
            button: "Select Tags",
        }
      } else if (this.checkedTags.length == 1) {
        return {
            button: this.checkedTags.length + " Tag",
        }
      } else {
        return {
            button: this.checkedTags.length + " Tags",
        }
      };
    }
  }

};
</script>

<style>
    .active {
        display: none;
        /* color: blue; */
    }
</style>
