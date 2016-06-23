<template>
  <text :x="point.x" :y="point.y">{{stat.label}}</text>
</template>

<script>
export default {
  props: {
    stat: Object,
    index: Number,
    total: Number
  },
  replace: true,
  computed: {
    point: function() {
      return this.$parent.valueToPoint(
        this.stat.value + 10,
        this.index,
        this.total
      )
    }
  },
}

</script>

<style scoped>
text {
  font-family: Helvetia Neue,Arial,sans-serif;
  font-size: 10px;
  fill: #666
}
</style>
