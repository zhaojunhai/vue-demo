<template>
  <div id ="demo">
    <svg width="200" height="200">
      <polygraph :stats="stats"></polygraph>
    </svg>

    <div v-for="stat in stats">
      <label>{{stat.label}}</label>
      <input type="range" v-model="stat.value" min="0" max="100" />
      <span>{{stat.value}}</span>
      <button @click="remove(stat)">X</button>
    </div>
    <form id="add">
      <input name="newlabel" v-model="newLabel" />
      <button @click="add">Add a stat</button>
    </form>
    <pre id="raw">
      {{stats|json}}
    </pre>
  </div>
</template>

<script>
  var stats = [
    { label: 'A', value: 100 },
    { label: 'B', value: 100 },
    { label: 'C', value: 100 },
    { label: 'D', value: 100 },
    { label: 'E', value: 100 },
    { label: 'F', value: 100 }
  ]

  import polygraph from './components/Pllygraph-template.vue'
  export default {
    data: function() {return {
      newLabel: '',
      stats: stats
    }
  },
  components: {
    'polygraph': polygraph 
  },
  methods: {
    add: function(e) {
      e.preventDefault()
      if(!this.newLabel) return
        this.stats.push({
          label: this.newLabel,
          value: 100
        })
        this.newLabel=''
      },
      remove: function(stat) {
        if(this.stats.length > 3) {
          this.stats.$remove(stat)
        } else {
          alert('can not remove more')
        }
      }
    }
  }
</script>
<style>
  body {
    font-family: Helvetica Neue, Arial, sans-serif;
  }
  label {
    display: inline-block;
    margin-left: 10px;
    width: 20px;
  }

  #raw {
    position: absolute;
    top: 0;
    left: 300px;
  }
</style>
