<template >
  <div >

    <div class="alert alert-danger hide" v-bind:class="{active: sum.showAlert}" role="alert">
        At least one tag must be selected!
    </div>

    <div class="dropDown" ref="dropdownMenu" >
        <button class="btn btn-warning dropdown-toggle" v-on:click="toggleButton"> {{sum.button}} </button>
        <div class="hide " v-bind:class="{active: showTags}" >
             <Tags @childToParent="onChildClick"/>
        </div>
    </div>

  </div>
</template>

<script>

import Tags from './Tags'

export default {
  data() {
    return {
      checked: [],
      showTags: false,
      showAlert: false
    }
  },
  name: "Dropdown",
  components: { Tags },

  methods: {
      // put checkedTags array from Tags to checked array
      onChildClick (value) {
        this.checked = value
      },
      // toggle active class on Tags div when dropdown button is clicked
      toggleButton: function() {
        this.showTags = !this.showTags;     
      },
      // click on screen to close dropdown
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
    //create button text with clicked tags sum
    sum() {
       if (this.checked.length == 0) {
        return {
            button: "Select Tags",
            showAlert: true
        }
      } else if (this.checked.length == 1) {
        return {
            button: this.checked.length + " Tag",
             showAlert: false
        }
      } else {
        return {
            button: this.checked.length + " Tags",
            showAlert: false
        }
      }
    },
}
};
</script>

<style>
    .hide {
        display: none; 
    } 
    .active {
        display: block;
    }
    
    .dropDown {
        left: 50%;
        transform: translate(-50%, 0);
        top: 100px;
        position: absolute;
    }
    .btn-secondary {
        background-color: blue;
    }
   
    
</style>
