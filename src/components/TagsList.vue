<template >
  <div >
    <div class="alert alert-danger disabled" v-bind:class="{active: sum.showAlert}" role="alert">At least one tag must be selected!</div>
    <div class="dropdown" ref="dropdownMenu" >
        <button v-on:click="toggleButton"> {{sum.button}} </button>
        <div class="disabled" v-bind:class="{active: showTags}" >
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
  </div>
</template>

<script>

export default {
  name: "TagsList",
  data: function() {
    return {
      checkedTags: [],
      showTags: false,
      showAlert: false
    }
    },


    methods: {
        toggleButton: function() {
         this.showTags = !this.showTags;     
        },
        documentClick(e){
            let el = this.$refs.dropdownMenu
            let target = e.target
            if ( el !== target && !el.contains(target)) {
              this.showTags=false
            }
        }
      
    },
    created () {
            document.addEventListener('click', this.documentClick)
    },
    destroyed () {
            document.removeEventListener('click', this.documentClick)
    },

  computed: {
    sum() {
       if (this.checkedTags.length == 0) {
        return {
            button: "Select Tags",
            showAlert: true
        }
      } else if (this.checkedTags.length == 1) {
        return {
            button: this.checkedTags.length + " Tag",
             showAlert: false
        }
      } else {
        return {
            button: this.checkedTags.length + " Tags",
            showAlert: false
        }
      }
    },
}
};
</script>

<style>
    .disabled {
        display: none; 
    }
    .active {
        display: block;
    }
    .dropdown {
        max-width: 100%;
    }
</style>
