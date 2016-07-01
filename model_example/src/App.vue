<template>
  <div id="app">
    <button id="show-modal" @click="showModal = true">Show Modal</button>
    <modal :show.sync="showModal">
      <h3 slot="header">custom header</h3>
    </modal>
  </div>
</template>

<script>
  import Modal from 'components/Modal_component.vue'

  export default {
    // el: function() {return {el:'#app'};},
    data: function() {
      return {
        showModal:false
      };
    },
    components: {
      'modal': Modal
    }
  }
</script>
