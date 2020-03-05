<template >
  <div >
    <div class="alert alert-danger hide" v-bind:class="{active: sum.showAlert}" role="alert">At least one tag must be selected!</div>
    <div class="dropDown" ref="dropdownMenu" >
        <button class="btn btn-warning dropdown-toggle" v-on:click="toggleButton"> {{sum.button}} </button>
        <div class="hide " v-bind:class="{active: showTags}" >
     
             <Tags :parentData="myData" @childToParent="onChildClick"/>
             <!-- :parentData="myData" -->
        </div>
       
    </div>
  </div>
</template>

<script>
import Tags from './Tags'
export default {
  data() {
    return {
      checkedTags: [],
      showTags: false,
      showAlert: false
    }
  },
  name: "Dropdown",
  components: { Tags },


    methods: {
        onChildClick (value) {
          this.checkedTags = value
          // console.log('aha')
        },
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
