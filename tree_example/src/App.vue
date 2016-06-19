<template>
  <ul id="demo">
    <item class="item" :model="treeData"></item>
  </ul>
</template>

<script>
var data = {
  name: 'My Tree',
  children: [
    { name: 'hello' },
    { name: 'wat' },
    {
      name: 'child folder',
      children: [
        {
          name: 'child folder',
          children: [
            { name: 'hello' },
            { name: 'wat' }
          ]
        },
        { name: 'hello' },
        { name: 'wat' },
        {
          name: 'child folder',
          children: [
            { name: 'hello' },
            { name: 'wat' }
          ]
        }
      ]
    }
  ]
}

import item from './components/item_template.vue'

export default {
  el: function(){return {el: '#demo'};},
  data: function(){ return {treeData:data} },
  components: {'item': item}
}
</script>
