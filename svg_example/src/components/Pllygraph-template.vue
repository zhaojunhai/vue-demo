<template>
  <g>
    <polygon :points="points"></polygon>
    <circle cx="100" cy="100" r="80"></circle>
    <axis-label v-for="stat in stats"
      :stat="stat" :index="$index"
      :total="stats.length">
    </axis-label>
  </g>
</template>

<script>
  import axisLabel from './Axis-label-template.vue'
  import Math from "mathjs"


  export default {
    props: ['stats'],
    replace: true,
    methods: {
      valueToPoint: function (value, index, total) {
        console.log("...")
        var x = 0
        var y = -value*0.8
        var angle = Math.PI*2/total * index
        var cos = Math.cos(angle)
        var sin = Math.sin(angle)
        var tx = x*cos - y*sin + 100
        var ty = x*sin + y*cos + 100
        return {
          x: tx,
          y: ty
        }
      }
    },
    computed: {
      points: function() {
        var total = this.stats.length
        var ob = this
        console.log("prints")
        return this.stats.map(function(stat,i) {
          var point = ob.valueToPoint(stat.value, i, total)
          return point.x + ',' +point.y
        }).join(' ')
      }
    },
    components:{
      'axis-label':axisLabel
    }
  }
  </script>
  <style>
  polygon {
    fill: #42b983;
    opacity: .75
  }

  circle {
    fill: transparent;
    stroke: #999
  }
  </style>
