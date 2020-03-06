<template >
  <div >

    <div class="alert alert-danger displayNone" v-bind:class="{displayBlock: sum.showAlert}" role="alert">
        At least one tag must be selected!
    </div>

    <div class="dropDown" ref="dropdownMenu" >
      <button class="btn btn-warning dropdown-toggle" v-on:click="toggleButton">
        {{sum.text}} 
        <span v-bind:class="{displayNone: sum.showAlert}" class ="tags-sum">{{sum.sum}}</span>
      </button>

      <div class="dropdown-items hide " v-bind:class="{active: showTags}" >
        <Tags @childToParent="onChildClick"  />
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
      showAlert: false,
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
      },
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
          sum: '',
          text: "Select Tags",
          showAlert: true
      }
      } else if (this.checked.length == 1) {
        return {
          sum: this.checked.length,
          text: "Tag ",
          showAlert: false
        }
      } else {
        return {
          sum: this.checked.length,
          text: "Tags ",
          showAlert: false
        }
      }
    },
  }
};
</script>

<style>
    .hide {
        max-height: 0;
        overflow: hidden;
        transition: ease-in-out 0.3s;
        border: 0px solid #21252900;
        opacity: 0;
    } 
    .active {
        max-height: 500px;
        opacity: 1;
    }
    .displayNone {
      display: none;
    }
    .displayBlock {
      display: block;
    }
    .dropDown {
        left: 50%;
        transform: translate(-50%, 0);
        top: 100px;
        position: absolute;      
    }
    .dropDown button {
      width: 120px;
    }
    .dropdown-items {
      border: 1px solid #21252947;
      border-radius: 5px;
      padding: 10px;     
    }
    .tags-sum {
      color: #ffc107;
      background-color: #212529d8;
      padding: 0 6px;
      border-radius: 5px;
      font-weight: 700;
        font-size: 15px;
    } 
</style>
