<template>
  <li>
    <div :class="{bold:isFolder}" @click="toggle" @dblclick="changeType">
      {{model.name}}
      <span v-if="isFolder">[{{open?'-':'+'}}]</span>
    </div>
    <ul v-show="open" v-if="isFolder">
      <item class="item" v-for="model in model.children" :model="model"></item>
      <li @click="addChild">
        +
      </li>
    </ul>
  </li>
</template>

<script>
  import Vue from 'vue'
  export default {
    name:'item',
    props:{
      model:Object
    },
    data() {
        return { open: false };
    },
    computed: {
      isFolder: function(){
        return this.model.children != null && this.model.children.length!=0
      }
    },
    methods: {
      toggle: function() {
        if(this.isFolder) {
          this.open = !this.open
        }
      },
      changeType: function() {
        if(!this.isFolder) {
          Vue.set(this.model,'children', [])
          this.addChild()
          this.open = true
        }
      },
      addChild: function() {
        this.model.children.push({
          name: 'new stuff'
        })
      }
    }
  }
</script>

<style scoped>
  ul {
    padding-left: 1em;
    line-height: 1.5em;
    list-style-type: dot;
  }
  .bold {
    font-weight: bold;
  }
  .item {
    cursor: pointer;
  }
</style>
